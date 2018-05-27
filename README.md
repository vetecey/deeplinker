# Deeplinker

This module helps you to create web-links for opening native applications directly if it is possible. Otherwise web page will be opened.

![](https://capella.pics/e001872a-2203-48cf-9a1f-b1a7cf66b8cd)

## Install

You can install script via package managers or download it to your server. 

### NPM and Yarn

Install package

```shell
npm install @codexteam/deeplinker --save 
```

```shell
yarn add @codexteam/deeplinker
```

Then require `deeplinker` module

```js
const deeplinker = require('@codexteam/deeplinker');
``` 

### Local script

Download [dist/deeplinker.js](dist/deeplinker.js) file to your server and add it to your webpage.

```html
<script src="dist/deeplinker.js" async></script>
```

## Usage

Let's imagine that you want to create a link that opens some page in application, if it is installed. If target application is missing then link should open a web page as a normal link.

Check out example schemes below.

### On click

Call `deeplinker.click(element)` function. Element should contain the following params:

- `data-link` or `href` with a usual link
- `data-app-link` with a deep link (with custom protocol) to an application

Upgrade your link element by adding a listener with preventing default action. Set up `data-app-link` param.

```html
<a href="https://www.instagram.com/codex_team/"
   onclick="event.preventDefault(); deeplinker.click(this)"
   data-app-link="instagram://user?username=codex_team">Follow us on Instagram</a>
```

Or add listener to any element. Set up `data-link` and `data-app-link` params.

```html
<div onclick="deeplinker.click(this)"
     data-link="https://t.me/codex_team"
     data-app-link="tg://resolve?domain=codex_team">Join our Telegram-channel</div>
```

### Run automatically

If you want to try to open app silently then call `deeplinker.tryToOpenApp(deepLink)`.

Could be useful for redirection or invitation pages.

> Doesn't works on mobile devices.

```html
<body onload="deeplinker.tryToOpenApp('tg://user?username=codex_team')">
```

## Schemes of popular apps 

### Telegram

```
tg://resolve?domain=[username]
```

### Twitter

```
twitter://user?screen_name=[username]
```

### Instagram

```
instagram://user?username=[username]
```

### Facebook

```
fb://profile/[id]
```

### VK

```
vk://vk.com/[id]
```

## Issues and improvements

Feel free to ask a question or improve this project.

## License

MIT
