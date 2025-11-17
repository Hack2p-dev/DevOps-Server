# DevOps Manager (MVP+)

## Installation
  1. In the "Redist" directory, you will find drivers and frameworks for DirectX, .NET (x64 and x86 respectively for your architecture), and MS C++ REDISTRIBUTABLE 2013. Install them sequentially. No reboot is required.
  2. Run the DOM_Setup-x64.exe installer and follow the instructions.
  3. Read this README file to the end.
  4. Enjoy using the software. License: H2P ANY-NY

**Developed:** 2025 | **Company:** Hack2p Team  
**Version:** 1.0 T

## Description

**DevOps Manager** is an advanced tool for managing Windows Firewall ports, local hosting, and automating network operations. The program provides a convenient graphical interface and REST API for port management with support for scheduling, cloud synchronization, and a plugin system.

###  📄 LICENSE AGREEMENT
    H2P ANY-NY SOFTWARE LICENSE AGREEMENT
    LICENSE: H2P ANY-NY (Hack2p Any Node, No Yield)

    DISTRIBUTION TERMS:

✅ ALLOWED: Free distribution after purchasing a license

✅ ALLOWED: Use for educational and research purposes

✅ ALLOWED: Modification for personal use

✅ ALLOWED: Installation on an unlimited number of devices

❌ PROHIBITED: Commercial resale of the software

❌ PROHIBITED: Distribution without attribution

❌ PROHIBITED: Use for illegal purposes

❌ PROHIBITED: Reverse engineering for commercial purposes

### RIGHTS AND LIMITATIONS:
    This license grants a non-exclusive right to use the software. All intellectual property rights are retained by the Hack2p Development Team.

DevOps Manager is designed for:
- 🔧 **Port Management** — opening/closing ports in Windows Firewall through a simple interface
- 🌐 **Local Hosting** — running a built-in or PHP web server for development
- ⏰ **Automation** — scheduling automatic port opening/closing
- 🔌 **REST API** — programmatic integration and port management via HTTP endpoints
- ☁️ **Cloud Sync** — saving and synchronizing configurations in the cloud
- 🧩 **Extensibility** — plugin system for custom commands and integrations
- 📊 **History & Rollback** — tracking all operations with rollback capability

### Key Features

✨ **Modern Interface:**
- Dark and Light themes
- Support for Russian and English languages
- Responsive design with scrolling for all screen resolutions
- Intuitive buttons with icons and tooltips

⚙️ **Port Management:**
- Opening/closing ports in Windows Firewall
- Saving frequently used configurations (presets)
- Checking existing rules
- Support for TCP and UDP protocols

📅 **Scheduler:**
- Automatic port opening/closing on schedule
- Recurring tasks (interval-based)
- Saving schedule in AppData

🌐 **Web Server:**
- Built-in Kestrel server for serving static files
- Optional PHP built-in server (if PHP is installed)
- Configurable IP, port, and document folder

🔌 **REST API:**
- Full-featured API for programmatic integration
- JSON request/response format
- Endpoints: /api/ports/{open,close}, /api/presets, /api/history

☁️ **Cloud Synchronization:**
- Synchronizing presets with cloud storage
- Supported providers: HTTP (custom), extensible architecture
- Saving cloud configurations

🧩 **Plugin System:**
- Loading custom plugins from the plugins\ folder
- Simple IPlugin interface for extending functionality
- Automatic initialization at startup

📖 **History & Rollback:**
- Complete history of all operations
- "Undo" function to revert the last operation
- Local history storage

## Core Components

### Core (PortManager.Core)
- **PortRule** — firewall rule model (Name, Port, Protocol)
- **FirewallService** — port management via `netsh` (open, close, check rule exists)
- **ConfigurationService** — saving and loading presets (.pcf) in JSON format
- **LoggerService** — logging operations in %TEMP%\PortManager with date-based rotation
- **HistoryService** — storing operation history in AppData\Local\PortManager\history.json
- **SchedulerService** — scheduling automatic operations (opening/closing ports on schedule)
- **PluginService** — loading plugins from plugins\ folder, supporting IPlugin interface
- **CloudSyncService** — cloud synchronization of presets via ICloudProvider (HTTP, extensible)

### UI (PortManager.UI)
- WPF application with modern design (Light/Dark themes, Russian/English)
- Port management: opening, closing, saving presets
- Operation history with "Undo" function
- Built-in web server: folder selection, IP, port
- Scrollable panels (ScrollViewers) for compatibility with different screen resolutions

### WebServer (PortManager.WebServer)
- Kestrel host for serving static files
- REST API for automation:
  - `GET /api/ping` — availability check
  - `POST /api/ports/open` — open port (JSON: PortRule)
  - `POST /api/ports/close` — close port (JSON: PortRule)
  - `GET /api/presets` — list of saved presets
  - `GET /api/history` — operation history
- Option to start PHP built-in server (if PHP is installed): `usePhp=true` in StartAsync

## Requirements

- .NET 8 SDK
- Windows (for working with `netsh`, WPF and firewall API)
- Administrator rights for firewall management
- (Optional) PHP CLI for `usePhp=true` mode
- (Optional) MySQL for full web application

Updates - Coming soon...

___________________________________________________________________________________________________ 
## FOR DEVELOPERS and reverse engineers. To obtain open-source code. Write to support@hack2p.ru 

### How to build and run

### Building:

```pwsh
cd "E:\ПРОЕКТ AutoPort by H2p\Alpha"
dotnet clean
dotnet restore
dotnet build
dotnet run --project src/PortManager.UI/PortManager.UI.csproj