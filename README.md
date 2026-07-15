<div align="center">

# Synkin

**Instantly preview your local web apps on Android — over USB.**

[![npm](https://img.shields.io/npm/v/synkin?color=39d98a&label=npm)](https://www.npmjs.com/package/synkin)
[![License: MIT](https://img.shields.io/badge/license-MIT-39d98a.svg)](#license)
[![Platform](https://img.shields.io/badge/platform-Windows-39d98a.svg)](#requirements)
[![Android](https://img.shields.io/badge/device-Android-39d98a.svg)](#requirements)

[Install](#installation) · [Usage](#usage) · [Docs](https://owsam22.github.io/synkin-page) · [Report an issue](https://github.com/owsam22/synkin/issues)

</div>

---

Synkin is a lightweight CLI that bridges your local development server to an Android device over USB using ADB. It automatically discovers your running dev server, forwards the required ports, and opens Chrome on your connected device.

No IP addresses. No firewall configuration. No Wi-Fi setup.
**Plug in your phone, run one command, and you're live on-device.**

```bash
npm install -g synkin
```
```bash
synkin run
```

---

## Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Typical workflow](#typical-workflow)
- [Supported frameworks](#supported-frameworks)
- [Project detection](#project-detection)
- [Static HTML projects](#static-html-projects)
- [Notes for Vite users](#notes-for-vite-users)
- [Troubleshooting](#troubleshooting)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

---

## Features

| | |
|---|---|
| 🚀 **One-command setup** | Run a single command and the bridge configures itself. |
| 🔌 **USB-only connection** | No Wi-Fi, no shared network, no exposed ports. |
| 📱 **Automatic Chrome launch** | Opens your project on the device the moment it's ready. |
| 🔍 **Automatic project detection** | Recognizes your framework by scanning the current directory. |
| ⚡ **Automatic port discovery** | Finds the ports your servers are running on — nothing to specify. |
| 🔄 **Frontend + backend together** | Bridges both at once, in a single run. |
| 🌐 **Works with localhost APIs** | Backend requests are tunneled through ADB Reverse. |
| 🧹 **Cleans up on exit** | Disconnect the cable or stop Synkin and everything unwinds automatically. |
| 💻 **Cross-project support** | Use it in any project directory, no per-project config. |

---

## Requirements

- Node.js 18+
- An Android device
- A USB cable
- USB debugging enabled on the device
- [ Android Platform Tools -ADB ](https://developer.android.com/tools/releases/platform-tools)

Verify ADB is installed:

```bash
adb version
```

Verify your device is recognized:

```bash
adb devices
```

Expected output:

```text
List of devices attached
2201116PI    device
```

---

## Installation

Install globally with npm:

```bash
npm install -g synkin
```

Verify the installation:

```bash
synkin --version
```

---

## Usage

**1. Start your frontend**

```bash
npm run dev
```

**2. Start your backend** *(optional)*

```bash
npm run dev
```

**3. Connect your Android phone via USB**

**4. Run Synkin**

```bash
synkin run
```

Synkin will then:

- Detect your Android device
- Discover your running project
- Detect frontend and backend ports
- Configure ADB Reverse
- Launch Chrome automatically
- Open your project on the phone

---

## Typical workflow

```bash
# Terminal 1
cd frontend
npm run dev
```

```bash
# Terminal 2
cd backend
npm run dev
```

```bash
# Terminal 3
synkin run
```

That's it — your project is live on-device.

---

## Supported frameworks

| Frontend | Backend |
|---|---|
| React | Express.js |
| Vite | NestJS |
| Next.js | FastAPI |
| Angular | Flask |
| Static HTML | Django |

More frameworks will be added in future releases.

---

## Project detection

Synkin automatically detects supported projects by scanning the current directory — no configuration required.

<details>
<summary>Detected project types</summary>

```
React
Vite
Next.js
Angular
Express
NestJS
FastAPI
Flask
Django
HTML
```

</details>

---

## Static HTML projects

Synkin also supports simple static sites. Serve your files however you like:

```bash
python -m http.server 5500
```

```bash
npx serve .
```

Then run:

```bash
synkin run
```

---

## Notes for Vite users

Your Vite server must be reachable through ADB Reverse. If it's only listening on `127.0.0.1`, Android Chrome can't reach it through the bridge — enable `server.host` in `vite.config.ts`:

```ts
server: {
  host: true
}
```

---

## Troubleshooting

**Device not detected**

Check the connection:

```bash
adb devices
```

Make sure these are enabled on the device:
- USB debugging
- File transfer mode

**Chrome doesn't open**

Confirm Google Chrome is installed on the Android device.

**Project not found**

Run Synkin from inside your project folder:

```bash
cd my-project
synkin run
```

**Backend requests fail**

Make sure your backend server is running *before* starting Synkin.

---

## Roadmap

**v0.2**
- Better project detection
- Improved framework support
- Automatic update notifications
- Better error reporting

**v0.3**
- Multiple device support
- Better diagnostics
- Improved performance

**v1.0**
- Stable release
- Extended framework support
- Enhanced developer experience

---

## Contributing

Contributions, suggestions, and bug reports are welcome. If you find a bug or have an idea for an improvement, [open an issue](https://github.com/owsam22/synkin-page/issues).

## License

Released under the [MIT License](LICENCE).

---

<div align="center">

Made with ❤️ by **Samarpan**

</div>
