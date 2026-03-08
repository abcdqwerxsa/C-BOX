<div align="center">

# 🚀 P-BOX

**A Modern Proxy Management Panel for Linux**

Powered by Mihomo (Clash.Meta) Core | Elegant Web UI | One-Click Deployment

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Go](https://img.shields.io/badge/Go-1.21+-00ADD8?logo=go)](https://go.dev)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript)](https://typescriptlang.org)

<img src="frontend/public/p-box-logo.png" width="120" alt="P-BOX Logo">

</div>

---

## ✨ Features

- 🎨 **Modern UI** - Beautiful Apple Glass style design with dark/light themes
- 🐧 **Linux Only** - Optimized for Linux servers (amd64/arm64)
- 📊 **Real-time Dashboard** - Traffic stats, connection monitoring, exit IP display
- 📦 **Subscription Management** - Multiple subscription sources with one-click update (supports YAML & JSON format)
- 🔧 **Core Management** - Auto version detection, one-click download and install
- ⚡ **Config Generator** - Visual rule configuration with smart routing
- 🌐 **i18n** - Chinese/English language support
- 🔐 **Authentication** - Built-in login system to protect the panel
- 🚀 **Auto Deploy** - One-click installation with systemd service

## 📸 Screenshots

<details>
<summary>Click to expand screenshots</summary>

| Dashboard | Proxy Groups |
|:---:|:---:|
| Real-time traffic monitoring | Node selection & speed test |

| Subscriptions | Core Management |
|:---:|:---:|
| Multi-source management | Auto version detection |

</details>

## 🚀 Quick Start

### Linux One-Click Install (Recommended)

```bash
curl -fsSL https://raw.githubusercontent.com/abcdqwerxsa/C-BOX/main/install.sh | sudo bash
```

The script will:
- Detect system architecture automatically (amd64/arm64)
- Download the latest stable release from GitHub
- Install to `/etc/p-box`
- Create a systemd service for auto-start
- Start the service on port **8666**

### Manual Installation

Download pre-built binaries from the [Releases](../../releases) page:

| Platform | File |
|:---|:---|
| Linux x64 | `p-box-{version}-linux-amd64.tar.gz` |
| Linux ARM64 | `p-box-{version}-linux-arm64.tar.gz` |

```bash
# Download (replace VERSION with actual version, e.g., 1.0.1)
curl -LO https://github.com/abcdqwerxsa/C-BOX/releases/download/v{VERSION}/p-box-{VERSION}-linux-amd64.tar.gz

# Extract
tar -xzf p-box-*.tar.gz
cd p-box-*

# Run
./p-box
```

Visit http://localhost:8383 to access the panel.

### Local Development & Installation

To run P-BOX from source or contribute to development:

#### 📋 Prerequisites
- **Go** 1.21 or higher
- **Node.js** 18 or higher
- **npm** (comes with Node.js)

#### 🔨 Step-by-Step Setup
1. **Clone the repository:**
   ```bash
   git clone https://github.com/abcdqwerxsa/C-BOX.git
   cd C-BOX
   ```

2. **Initialize Data Directory:**
   ```bash
   mkdir -p data/configs data/cores data/logs
   ```

3. **Setup Backend:**
   ```bash
   cd backend
   go mod tidy
   go build -o p-box .
   cd ..
   ```

4. **Build Frontend:**
   ```bash
   cd frontend
   npm install
   npm run build
   cd ..
   ```

5. **Run:**
   ```bash
   ./backend/p-box
   ```

## 📁 Project Structure

```
p-box/
├── backend/                 # Go Backend
│   ├── main.go              # Entry point
│   ├── server/              # HTTP server
│   ├── modules/             # Feature modules
│   └── config/              # Configuration
├── frontend/                # React Frontend
│   ├── src/                 # Source code
│   └── public/              # Static assets
├── .github/workflows/       # GitHub Actions CI/CD
├── install.sh               # Linux installer script
└── config.yaml              # Default configuration
```

## 🛠️ Tech Stack

| Backend | Frontend |
|:---:|:---:|
| Go 1.21+ | React 18 |
| Gin | Vite 5 |
| WebSocket | TypeScript |
| YAML | Tailwind CSS |
| | Zustand |
| | i18next |

## ⚙️ Configuration

A default configuration file `config.yaml`:

```yaml
server:
  port: 8383
  host: 0.0.0.0

data_dir: data

core:
  type: mihomo
  api_port: 9090

proxy:
  mixed_port: 7890
  socks_port: 7891
  allow_lan: true
  ipv6: false
  mode: rule

log:
  level: info
  file: data/logs/p-box.log
  console: true

security:
  enabled: false
  username: admin
  password: admin123
```

## 🔄 Update

To update to the latest version, simply run the install script again:

```bash
curl -fsSL https://raw.githubusercontent.com/abcdqwerxsa/C-BOX/main/install.sh | sudo bash
```

## 🔮 Known Issues & Roadmap

### TFO (TCP Fast Open) Support

TCP Fast Open is currently **disabled** due to compatibility issues in certain environments (especially WSL).

**What is TFO?**
- Reduces TCP connection latency by allowing data in SYN packet
- 0-RTT for repeated connections (saves ~1 RTT)

**Why disabled?**
- WSL2 networking stack has incomplete TFO support
- Some ISPs/firewalls may block TFO packets
- Connection timeouts in virtualized environments

**Roadmap:**
- [ ] Add TFO support toggle in proxy settings UI
- [ ] Environment detection (auto-enable for native Linux, disable for WSL/VM)
- [ ] Per-proxy TFO configuration

## 🤝 Contributing

Pull Requests and Issues are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m "Add amazing feature"`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- [Mihomo](https://github.com/MetaCubeX/mihomo) - High-performance proxy core
- [Clash](https://github.com/Dreamacro/clash) - Original Clash core
- [Sing-box](https://github.com/SagerNet/sing-box) - The universal proxy platform
- [React](https://react.dev) - Frontend framework
- [Tailwind CSS](https://tailwindcss.com) - CSS framework

---

<div align="center">

**If you find this project helpful, please give it a ⭐️ Star!**

</div>
