# @lumine-code/get-scrollbar-style

Retrieves the current scrollbar style on macOS with consistent fallbacks on Windows and Linux.

> [!WARNING]
> **This package is deprecated.** [Lumine](https://github.com/lumine-code/lumine) no longer depends on it — each window now measures its rendered scrollbar style directly, and change notifications come from Electron's `systemPreferences` API. This repository is archived and no longer maintained.

## Features

- **Native macOS detection**: reads `NSScroller.preferredScrollerStyle` through an N-API addon.
- **Cross-platform API**: returns `legacy` on Windows and Linux.
- **ABI stability**: uses Node-API so one source implementation supports current Node.js and Electron releases.

## Installation

```sh
npm install @lumine-code/get-scrollbar-style
```

## Usage

The exported function returns `overlay`, `legacy`, or `unknown` on macOS. It always returns `legacy` on Windows and Linux.

```js
const getScrollbarStyle = require('@lumine-code/get-scrollbar-style')

console.log(getScrollbarStyle())
```

Electron applications can observe changes separately through the [`systemPreferences` API](https://www.electronjs.org/docs/latest/api/system-preferences) and its `NSPreferredScrollerStyleDidChangeNotification` notification.

## Building

Install Node.js 20 or later and the platform C++ build tools, then run:

```sh
npm install
npm test
```

## Contributing

Bug reports and contributions are welcome on GitHub.
