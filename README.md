# Чат рулетка
[![Чат рулетка](logo_min.png)](https://videochatru.com/)

-----------------
[![Build Info](https://img.shields.io/cirrus/github/vicimpa/chatroulette)](https://github.com/vicimpa/chatroullete)
[![Download](https://img.shields.io/github/downloads/vicimpa/chatroulette/0.0.2/total)](https://github.com/vicimpa/chatroulette/releases)
[![Npm version](https://img.shields.io/npm/v/chatroulette)](https://www.npmjs.com/package/chatroulette)
[![Npm License](https://img.shields.io/npm/l/chatroulette)](https://www.npmjs.com/package/chatroulette)
[![VK Link](https://img.shields.io/badge/social-vk-blue)](https://vk.com/vicimpa)
[![Telegram Link](https://img.shields.io/badge/social-tg-9cf)](https://telegram.im/@vic_dev)

Неофициальный десктопный клиент чат рулетки, который прекрасно подойдет для тех, кому нужно намеренно направить звук с чат рулетки в программу захвата звука, для тех, кто использует обработку видео в чате, для тех, у кого стоит DroidCam, ManyCam и прочая дичь, улучшающая изображение и для тех, у кого есть микрофон, из-за которого не пускают в чат рулетку. Легко обходит запрет на использование виртуальной камеры. Позже планируется доработка в сторону расширения функциональности приложения. Я не нашел альтернатив, по этому и собрал клиент чат рулетки для компьютера. Очень прошу написать мне в [vk](https://vk.com/vicimpa) если у Вас что-то не работает, постараюсь помочь.

- Нет необходимости устанавливать
- Работает независимо от операционной системы
- Не обращает внимание на присутствующие камеры
- Убрана реклама и прочая лишняя информация
- Есть возможность выбирать вывод на аудиоустройства

Загрузить можно [тут](https://github.com/vicimpa/chatroulette/releases/latest)

# Установка и запуск

## Для пользователей Windows

### Способ 1: Скачать готовое приложение (рекомендуется)

Это самый простой способ - не требует установки Node.js или других инструментов.

1. Перейдите на страницу [релизов](https://github.com/vicimpa/chatroulette/releases/latest)
2. Скачайте файл `ChatRoulette-windows-X.X.X.exe`
3. Запустите скачанный файл
4. Готово! Приложение запустится без установки

### Способ 2: Установка через npm

Если у вас уже установлен Node.js:

```bash
npm i -g chatroulette
chatroulette
```

### Способ 3: Сборка из исходного кода

Если вы хотите собрать приложение самостоятельно:

```bash
npm install
npm run build-windows
```

После сборки исполняемый файл будет находиться в папке `build/`

## Для пользователей Linux

### Способ 1: Скачать готовое приложение (рекомендуется)

1. Перейдите на страницу [релизов](https://github.com/vicimpa/chatroulette/releases/latest)
2. Скачайте файл `ChatRoulette-linux-X.X.X.AppImage`
3. Сделайте файл исполняемым: `chmod +x ChatRoulette-linux-X.X.X.AppImage`
4. Запустите файл: `./ChatRoulette-linux-X.X.X.AppImage`

### Способ 2: Установка через npm

```bash
npm i -g chatroulette
chatroulette
```

### Способ 3: Сборка из исходного кода

```bash
npm install
npm run build-linux
```

## Для пользователей MacOS

### Способ 1: Скачать готовое приложение (рекомендуется)

1. Перейдите на страницу [релизов](https://github.com/vicimpa/chatroulette/releases/latest)
2. Скачайте файл `ChatRoulette-macos-X.X.X.dmg`
3. Откройте DMG файл и перетащите приложение в папку Applications

### Способ 2: Установка через npm

```bash
npm i -g chatroulette
chatroulette
```

### Способ 3: Сборка из исходного кода

```bash
npm install
npm run build-mac
```

# Для разработчиков

## Запуск в режиме отладки

```bash
npm install
npm start
```

# Скриншоты

>
> ![screen](screen/img1.png)
>
> ![screen](screen/img2.png)
> 
