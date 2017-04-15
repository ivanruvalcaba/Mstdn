Web-based Desktop Client for [Mastodon][]
=========================================

<img src="https://github.com/rhysd/ss/blob/master/Mstdn/main.png?raw=true" width="484" alt="screen shot"/>

Features:

- [x] Small window on your menubar (or isolated window)
- [x] Desktop notification
- [x] Customizable shortcut keybinds
- [ ] Multi-account

Mastodon is an open source project. So if you want to make a new UI, you can just fork the project,
implement your favorite UI and host it on your place. Then you can participate Mastodon networks from it.

However, Mastodon is a web application. So we can't go out from a browser. So this small tool
provides a way to do it.

## Installation

### Via [npm][]

```
$ npm install -g mstdn
```

### As an isolated app

Download a package archive from [Release page][] (not yet), put unarchived app to proper place, and open it.

## Usage

If you installed this app via npm, below command is available to start app.

```
$ open-mstdn-app
```

At first, a dialog which recommends to write up config is shown and JSON config file will be shown in your editor. You need to fill up '"name"' and `"host"` keys in `"accounts"`.

Then please try to start app again. Usage is the same as web client on mobile devices. Some shortcuts are available by default (please see below 'Customization' section).

## Customization

Mstdn can be customized with JSON config file at `{app dir}/config.json`

The `{app dir}` is:

- `~/Library/Application\ Support/Mstdn` for macOS
- `~/.config/Mstdn` for Linux
- `%APPDATA%\Mstdn` for Windows.

The JSON file can contain below key-values:

### `hot_key`

`hot_key` is a key sequence to toggle application window. The shortcut key is defined globally.
The format is a [Electron's accelerator](https://github.com/electron/electron/blob/master/docs/api/accelerator.md). Please see the document to know how to configure this value.
Default value is `"CmdOrCtrl+Shift+S"`. If you want to disable, please set empty string or `null`. 

### `icon_color`

Color of icon in menubar. `"black"` or `"white"` can be specified.

### `always_on_top`

When this value is set to `true`, the window won't be hidden if it loses a focus. Default value is `false`.

### `normal_window`

When this value is set to `true`, application will be launched as a normal window application.
If menu bar behavior does not work for you, please use set this value to `true` to avoid it.
Default value is `false` on macOS or Linux, `true` on Windows because window position is broken in some version of Windows.

### `zoom_factor`

Font zoom factor in application. It should be positive number. For example, `0.7` means `70%` font zooming.
Default font size is a bit bigger because https://mobile.twitter.com is originally for mobile devices. So default value is `0.9`.

### `accounts`

Array of your accounts. An element should has `"name"`, `"host"` and `"default_page"` keys. `"name"` represents your screen name. `"host"` represents a host part of URL of your mastodon instance. `"default_page"` is a page firstly shown.

You need to write up this config at first.

### `keymaps`

Object whose key is a key sequence and whose value is an action name.

| Action Name        | Description                     | Default Key |
|--------------------|---------------------------------|-------------|
| `scroll-down`      | Scroll down window              | `j`         |
| `scroll-up`        | Scroll up window                | `k`         |
| `scroll-top`       | Scroll up to top of window      | `i`         |
| `scroll-down-page` | Scroll down to bottom of window | `m`         |

If an action name starts with `/`, it will navigate to the path. For example, if you set `"/web/timelines/home"` to some key shortcut and you input the key, browser will navigate page to `https://{your host}/web/timelines/home`.

By default, some key shortcuts are set.

## Multi account

Not yet.

[Mastodon]: https://github.com/tootsuite/mastodon
[npm]: https://www.npmjs.com/package/mstdn
[Release page]: https://github.com/rhysd/Mstdn
