# ProtoShelf - User Guide

ProtoShelf is a modern inventory management system for electronic components. This guide will help you get started with using ProtoShelf on your computer.

## 📦 Installation

### Step 1: Download ProtoShelf
1. Download the latest ProtoShelf release (ZIP file) from the releases page
2. Extract the ZIP file to a folder on your computer (e.g., `C:\ProtoShelf\` or `D:\ProtoShelf\`)
3. You should now have a folder containing:
   - `protoshelf.exe` (the main application)
   - `server.yaml` (configuration file)
   - `data/` folder (for your inventory database)

### Step 2: Run ProtoShelf
1. Navigate to the folder where you extracted ProtoShelf
2. Double-click `protoshelf.exe` to start the application
3. You should see a ProtoShelf icon appear in your system tray (bottom-right corner of your screen)

## 🚀 Using ProtoShelf

### Starting the Application
- **Double-click** `protoshelf.exe` to start ProtoShelf
- The application runs in the background and creates a system tray icon
- Once started, ProtoShelf will be accessible through your web browser

### Accessing the Web Interface
You can access ProtoShelf in two ways:

#### Option 1: Through the System Tray (Recommended)
1. Look for the ProtoShelf icon in your system tray (bottom-right corner)
2. Right-click the icon
3. Select "Open ProtoShelf" from the menu
4. Your default web browser will open to the ProtoShelf interface

#### Option 2: Directly in Your Browser
1. Open your web browser (Chrome, Firefox, Edge, etc.)
2. Go to: `http://localhost:3001` (or whatever port is configured in your `server.yaml` file)
3. The ProtoShelf interface will load

> **Note**: The default port is 3001, but this can be changed in the `server.yaml` configuration file.

### System Tray Menu
Right-click the ProtoShelf system tray icon to access:
- **"Open ProtoShelf"** - Opens the web interface in your browser
- **"Stop Server"** - Stops the ProtoShelf server and closes the application

## 🔧 Managing ProtoShelf

### Configuration
ProtoShelf uses a `server.yaml` file for configuration. You can modify this file to change settings:

```yaml
server:
  port: 3001          # Change this to use a different port
database:
  autobackup: true    # Enable automatic backups
  backupinterval: 24  # Hours between backups
  maxbackups: 7       # Maximum number of backups to keep
logging:
  level: debug        # Log level (debug, info, warn, error)
  format: text        # Log format (text or json)
```

**Important**: Stop ProtoShelf before editing the configuration file, then restart it for changes to take effect.

### Starting ProtoShelf
- Double-click `protoshelf.exe` whenever you want to use the application
- The application will start automatically and be ready to use within a few seconds

### Stopping ProtoShelf
You can stop ProtoShelf in two ways:
1. **Right-click** the system tray icon and select "Stop Server"
2. **Close your web browser** (the server will continue running in the background)

### Checking if ProtoShelf is Running
- Look for the ProtoShelf icon in your system tray
- If you don't see it, the application isn't running
- If you see it, ProtoShelf is ready to use

## 🎯 Quick Start Guide

### Adding Your First Component
1. Start ProtoShelf and open the web interface
2. Click on "Components" in the navigation menu
3. Click "Add Component" 
4. Fill in the component details:
   - **Name**: What is this component? (e.g., "Arduino Uno", "10kΩ Resistor")
   - **Quantity**: How many do you have?
   - **Location**: Where is it stored?
   - **Category**: What type of component is it?
5. Click "Save" to add the component to your inventory

### Setting Up Storage Locations
1. Go to "Locations" in the navigation menu
2. Click "Add Unit" to create a storage unit (e.g., "Workbench Drawers", "Component Cabinet")
3. Add bins to your unit by clicking "Add Bin" and specifying:
   - **Position**: Where is this bin located? (e.g., "A1", "Top Left", "Drawer 1")
   - **Description**: What's stored here?

### Organizing with Categories
1. Components are automatically organized into categories
2. Use the search and filter features to find components quickly
3. Categories help you keep similar components together

## 🛠️ Troubleshooting

### ProtoShelf Won't Start
- **Check if already running**: Look for the ProtoShelf icon in your system tray
- **Run as Administrator**: Right-click `protoshelf.exe` and select "Run as administrator"
- **Check antivirus**: Some antivirus software may block the application
- **Verify extraction**: Make sure you extracted the ZIP file completely

### Can't Access the Web Interface
- **Check the system tray**: Make sure ProtoShelf is running (icon should be visible)
- **Try the direct URL**: Go to `http://localhost:3001` in your browser (or check your `server.yaml` for the configured port)
- **Check firewall**: Windows Firewall may be blocking the application
- **Try a different browser**: Some browsers may have security restrictions

### Port Already in Use Error
- **Check other applications**: Another program might be using the configured port
- **Change the port**: Edit `server.yaml` and change the `server.port` value to a different port (e.g., 3002, 8080)
- **Restart ProtoShelf**: Stop the server completely and restart it
- **Restart your computer**: This will free up any stuck ports

### Data Not Saving
- **Check permissions**: Make sure ProtoShelf has write access to the `data/` folder
- **Don't move files**: Keep `protoshelf.exe` and the `data/` folder in the same location
- **Check disk space**: Make sure you have enough free space on your drive

## 📂 File Organization

Keep these files together in the same folder:
```
ProtoShelf/
├── protoshelf.exe          # Main application (don't move this!)
├── server.yaml             # Configuration file
└── data/                   # Your inventory database
    └── sqlite/
        └── protoshelf.db   # Your component data
```

**Important**: 
- Don't move or rename `protoshelf.exe`
- Don't move the `data/` folder
- Keep everything in the same folder for the application to work correctly

## 🔄 Backing Up Your Data

### Automatic Backups
ProtoShelf automatically creates backups of your inventory data. You can:
1. Go to "Settings" → "Backups"
2. View available backups
3. Create manual backups
4. Restore from previous backups

### Manual Backup
For extra safety, you can copy the entire `data/` folder to another location:
1. Stop ProtoShelf (right-click system tray → "Stop Server")
2. Copy the `data/` folder to a safe location (USB drive, cloud storage, etc.)
3. Restart ProtoShelf

## 🆘 Getting Help

### Common Questions
- **Q: Can I run ProtoShelf on multiple computers?**
  A: Yes, but each computer will have its own separate inventory database.

- **Q: Can multiple people use ProtoShelf at the same time?**
  A: Yes, if they access it through the same computer's web browser.

- **Q: Is my data secure?**
  A: ProtoShelf runs locally on your computer. Your data stays on your machine.

- **Q: Do I need an internet connection?**
  A: No, ProtoShelf works completely offline.

### Need More Help?
- Check the GitHub repository for technical documentation
- Report bugs or request features through GitHub Issues
- Review the full README.md for advanced configuration options

## 🎉 You're Ready to Go!

ProtoShelf is now ready to help you organize your electronic components. Start by adding a few components and locations, then explore the features to find what works best for your workflow.

Happy organizing! 📦✨
