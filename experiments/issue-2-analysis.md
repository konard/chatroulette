# Issue #2 Root Cause Analysis

## Problem Statement
Users cannot use normal and virtual cameras simultaneously. When both are enabled, a registration popup appears.

## Root Cause

### 1. Virtual Camera Detection System
**Location:** `test/test_1.2.js:7`

The application includes a comprehensive virtual camera detection system (FCN object) with:
- **60+ blocked virtual camera names** including: Snap Camera, OBS Virtual Camera, ManyCam, DroidCam, etc.
- **Validation functions:**
  - `FCN.isValid(cameraLabel)` - Returns `false` if camera matches blocked list
  - `FCN.isSuspicious(cameraLabel)` - Returns `true` for suspicious patterns

### 2. Camera Enumeration Blocking
**Location:** `dist/preload.js:54-55`

When cameras are enumerated, Snap Camera is specifically blocked:
```javascript
if (/Snap Camera/.test(d))
  return 'asdfasjdcnawecaseaec'  // Returns fake/obfuscated name
```

### 3. Virtual Camera Rejection Logic
**Location:** `test/test3.js:28863-28868`

During getUserMedia(), the code validates all camera tracks:
```javascript
null == blogger["allowFakeWebcam"] && u["filter"]((function(e) {
    return y(e["label"]),
        FCN["isValid"](e["label"])
}))["length"] !== u["length"]
```

**What this does:**
- If `blogger["allowFakeWebcam"]` is `null` or `false` (default is `false`)
- AND the number of valid cameras doesn't match total cameras
- Then it throws an error (code "0x2a0")
- This error triggers the registration popup

### 4. Default Configuration
**Location:** `test/test3.js:27752`

```javascript
i["allowFakeWebcam"] = !1  // Default is false
```

However, at line 27762, there's a blogger configuration that sets it to `true`:
```javascript
r["allowFakeWebcam"] = !0  // true for certain bloggers
```

## The Flow

1. User has both normal camera + virtual camera (e.g., Snap Camera)
2. Application enumerates all media devices
3. Virtual camera is detected and flagged by FCN validation
4. Since `allowFakeWebcam` is `false` by default
5. Validation fails when virtual camera is present
6. Error is thrown
7. Registration popup appears as anti-fraud measure

## Solution

Change the default `allowFakeWebcam` setting from `false` to `true` to allow virtual cameras.

**File to modify:** `test/test3.js:27752`
**Change:** `i["allowFakeWebcam"] = !1` → `i["allowFakeWebcam"] = !0`

This will allow users to use both normal and virtual cameras simultaneously without triggering the registration popup.

## Alternative Solutions Considered

1. **Remove virtual camera from blocked list** - Not ideal, as it's part of a comprehensive security system
2. **Modify validation logic** - Too invasive, affects anti-fraud measures
3. **Change default setting** - ✓ Cleanest solution, minimal impact

## Security Implications

Allowing virtual cameras reduces anti-fraud protection. However:
- Users should have freedom to use legitimate tools like OBS for streaming
- Registration popup can still be triggered by other fraud indicators
- This is a user experience vs security tradeoff
