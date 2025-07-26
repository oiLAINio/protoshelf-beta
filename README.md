# ProtoShelf v0.0.3

ProtoShelf is a comprehensive inventory management system specifically designed for electronic components. Built with a modern React frontend and efficient Go backend, the application compiles into a single executable that serves both the web interface and API, making deployment incredibly simple.

## ✨ Key Features

- **📦 Component Management**: Add, edit, delete, and search electronic components with detailed specifications
- **📍 Location Tracking**: Organize components by units and bins with hierarchical storage system
- **💡 Location pinging**: Locate bins by illuminating them with WLED modules
- **🏷️ Category Management**: Categorize components for better organization and filtering
- **📊 Inventory Tracking**: Track component quantities, locations, and usage across projects
- **🚀 Project Management**: Create and manage personal projects with component assignments
- **📋 Work Orders**: Track work orders within projects and component usage
- **💾 Backup/Restore**: Comprehensive export and import functionality with automatic backups
- **🗄️ Database Support**: SQLite for local storage with configurable paths and network support
- **🎨 Modern UI**: Responsive React interface with dark/light theme support
- **📱 Mobile Friendly**: Fully responsive design with mobile navigation
- **🏷️ Label Generation**: Generate PDF labels with QR codes for bins and components
- **⚙️ Flexible Configuration**: Configurable settings for UI preferences and database options

## 🎯 Use Cases

ProtoShelf is perfect for:
- **Electronics Hobbyists**: Track your growing component collection
- **Makers & DIY Enthusiasts**: Organize parts for various projects
- **Small Workshops**: Manage inventory for electronics repair and prototyping
- **Students & Educators**: Organize educational electronic components
- **Home Labs**: Professional-grade inventory for home electronics labs

## 🏗️ Project Structure

```
protoshelf/
├── client/                 # React frontend application
│   ├── public/            # Static assets
│   ├── src/               # React source code
│   │   ├── components/    # Reusable UI components
│   │   ├── pages/         # Page components
│   │   ├── stores/        # Zustand state management
│   │   ├── types/         # TypeScript type definitions
│   │   ├── config/        # Configuration files (API endpoints)
│   │   └── utils/         # Utility functions
│   ├── package.json       # Node.js dependencies
│   └── README.md          # React-specific documentation
├── server/                # Go backend application
│   ├── handlers/          # HTTP request handlers
│   ├── models/            # Data models
│   ├── services/          # Business logic services
│   ├── config/            # Server configuration
│   ├── db/                # Database utilities
│   ├── main.go            # Main server entry point
│   ├── go.mod             # Go module dependencies
│   └── server.yaml        # Server configuration file
├── data/                  # Database files
│   └── sqlite/            # SQLite database files
├── docs/                  # Documentation
├── build.ps1              # PowerShell build script
├── build.bat              # Windows batch build script
├── docker-compose.yml     # Docker configuration
└── README.md              # This file
```

## 🚀 Quick Start

### Prerequisites

- **Go 1.23.4+** - [Download Go](https://golang.org/dl/)
- **Node.js 16+** - [Download Node.js](https://nodejs.org/)
- **npm** - Comes with Node.js

### Building the Application

The easiest way to build ProtoShelf is using the provided build scripts:

#### Windows PowerShell
```powershell
.\build.ps1
```

#### Windows Command Prompt
```cmd
build.bat
```

#### Manual Build Process
```bash
# 1. Install React dependencies
cd client
npm install

# 2. Build React application
npm run build
cd ..

# 3. Build Go server with embedded React files
cd server
go build -o ../protoshelf.exe .
cd ..

# 4. Run the application
./protoshelf.exe
```

### Running the Application

After building, simply run the executable:

```bash
./protoshelf.exe
```

The application will start on port 3001. Open your browser and navigate to:
```
http://localhost:3001
```

## 🖥️ Screenshots & Interface

ProtoShelf features a clean, modern interface with:
- **Dashboard**: Overview of your inventory with quick stats
- **Components**: Detailed component management with search and filtering  
- **Locations**: Visual unit and bin organization
- **Projects**: Project tracking with component assignments
- **Settings**: Comprehensive configuration options
- **Labels**: Generate professional labels with QR codes

## 🛠️ Development

### Development Mode

For development, you can run the frontend and backend separately:

#### Backend (Go Server)
```bash
cd server
go run main.go
```
Server runs on `http://localhost:3001`

#### Frontend (React)
```bash
cd client
npm start
```
Development server runs on `http://localhost:3000`

### Environment Configuration

The React application automatically detects the environment:
- **Development**: API calls go to `http://localhost:3001`
- **Production**: API calls use relative URLs (same origin)

### Database

ProtoShelf uses SQLite by default, with the database file stored in:
```
data/sqlite/protoshelf.db
```

## API Endpoints

The Go server provides the following API endpoints (all prefixed with `/api`):

### Components
- `GET /api/components` - Get all components
- `POST /api/components` - Add new component
- `PATCH /api/components/{componentID}` - Update component
- `DELETE /api/components/{componentID}` - Delete component

### Locations
- `GET /api/locations` - Get all units
- `POST /api/locations/unit` - Add new unit
- `PATCH /api/locations/unit/{unitID}` - Update unit
- `DELETE /api/locations/unit/{unitID}` - Delete unit
- `PATCH /api/locations/unit/{unitID}/layout` - Update unit layout
- `POST /api/locations/{unitID}/bins` - Add bin to unit
- `PATCH /api/locations/{unitID}/bins/{binID}` - Update bin
- `DELETE /api/locations/{unitID}/bins/{binID}` - Delete bin

### Categories
- `GET /api/categories` - Get all categories

### Projects
- `GET /api/projects` - Get all projects
- `POST /api/projects` - Add new project
- `GET /api/projects/{id}` - Get single project
- `PATCH /api/projects/{id}` - Update project
- `DELETE /api/projects/{id}` - Delete project
- `POST /api/projects/{id}/components` - Assign component to project
- `DELETE /api/projects/{id}/components/{componentID}` - Remove component from project
- `POST /api/projects/{id}/notes` - Add note to project

### Location Matrix
- `POST /api/locate` - Locate a bin in a unit (WLED integration)

### Backups
- `GET /api/backups/export` - Export data backup
- `POST /api/backups/import` - Import data backup
- `POST /api/backups/create` - Create manual backup
- `GET /api/backups/list` - List available backups
- `POST /api/backups/restore` - Restore backup

### Settings
- `GET /api/settings/database` - Get database settings
- `PUT /api/settings/database` - Update database settings
- `GET /api/settings/database/test` - Test database connection
- `GET /api/settings/system` - Get system information

### Labels
- `POST /api/labels/generate` - Generate labels for multiple bins
- `GET /api/labels/{unitID}/bins/{binID}` - Generate label for single bin

## 🔧 Technology Stack

### Frontend (React)
- **React 19** with TypeScript for modern, type-safe development
- **Zustand** for lightweight state management
- **React Hook Form** for efficient form handling
- **Tailwind CSS** for utility-first styling
- **Lucide React** for beautiful, consistent icons
- **React Router** for client-side routing
- **React Toastify** for user notifications

### Backend (Go)
- **Chi Router** for fast HTTP routing
- **Viper** for flexible configuration management
- **Logrus** for structured logging
- **SQLite** for reliable local data storage
- **Embedded React files** for single executable deployment

## 🏛️ Architecture

### Frontend (React)
- **React 19** with TypeScript
- **Zustand** for state management
- **React Hook Form** for form handling
- **Tailwind CSS** for styling
- **Lucide React** for icons
- **React Router** for client-side routing

### Backend (Go)
- **Chi Router** for HTTP routing
- **Viper** for configuration management
- **Logrus** for logging
- **SQLite/MongoDB** for data storage
- **Embedded React files** for single executable deployment

### Single Executable Deployment

The application uses Go's `embed` directive to include the React build files directly in the Go binary. This approach provides several benefits:

**🎯 Key Advantages:**
- **Zero Dependencies**: Single executable with no external files needed
- **Easy Deployment**: Just copy one file and run
- **Consistent Experience**: Frontend and backend always in sync
- **No Web Server Required**: Built-in static file serving

**📁 How It Works:**
1. React app builds to `client/build/`
2. Build files are copied to `server/static/` during build process
3. Go embeds these files using `//go:embed static/*`
4. Go server serves embedded files for non-API routes
5. API routes (`/api/*`) are handled by Go handlers
6. Client-side routes are handled by serving `index.html` and letting React Router take over

### Intelligent Routing System

The server provides smart routing that handles both API and frontend concerns:

- **📁 Static Files**: Files with extensions (`.js`, `.css`, `.png`) are served directly from embedded assets
- **🔌 API Routes**: All routes prefixed with `/api` are handled by Go backend handlers  
- **🧭 Client Routes**: Paths without extensions (`/components`, `/settings`, `/projects`) serve `index.html` for React Router
- **🔄 Page Refreshes**: Work correctly on any route (no 404 errors on browser refresh)
- **🚫 Conflict Prevention**: API and frontend routes are cleanly separated

## ⚙️ Configuration

### Server Configuration
Server settings are configured in `server/server.yaml`:

```yaml
server:
  port: 3001
  host: localhost
database:
  type: sqlite
  path: ../data/sqlite/protoshelf.db
logging:
  level: info
  format: text
```

### Environment Variables
- `NODE_ENV` - Set to `production` for production builds
- `PORT` - Override default server port (3001)

## 🚀 Deployment Options

### Single Executable (Recommended)
The simplest deployment method - after building, you only need:
1. **`protoshelf.exe`** - The main executable (contains everything)
2. **`server.yaml`** - Configuration file (optional, has sensible defaults)
3. **`data/`** - Directory for database files (created automatically)

### Docker Deployment
For containerized environments, use the provided Docker configuration:

```bash
docker-compose up -d
```

### Network Deployment
ProtoShelf supports various database path configurations:
- **Local**: `./data/protoshelf.db`
- **Network (Windows)**: `\\server\share\protoshelf.db`
- **Network (Unix)**: `//server/share/protoshelf.db`
- **Absolute**: `/path/to/database/protoshelf.db`

## 🎯 Roadmap

### Upcoming Features
- **🔍 Advanced Search**: Full-text search across all component data
- **📊 Analytics Dashboard**: Usage statistics and inventory insights
- **🔔 Smart Notifications**: Low stock alerts and maintenance reminders
- **📤 Advanced Export**: CSV, Excel, and custom format support
- **🏢 Multi-User Support**: User accounts and permissions
- **🔗 Integration APIs**: Connect with other tools and services


### Current Focus (v0.1.x)
- Performance optimizations
- Enhanced label generation
- Improved mobile experience
- Additional component fields

## 🤝 Contributing

We welcome contributions! Here's how to get started:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Make** your changes and test thoroughly
4. **Commit** your changes (`git commit -m 'Add amazing feature'`)
5. **Push** to the branch (`git push origin feature/amazing-feature`)
6. **Submit** a pull request

### Development Guidelines
- Follow existing code style and conventions
- Add tests for new features
- Update documentation as needed
- Test on multiple platforms when possible

## 📞 Support & Community

- **🐛 Bug Reports**: Use GitHub Issues for bug reports
- **💡 Feature Requests**: Suggest new features via GitHub Issues
- **❓ Questions**: Check existing issues or create a new one
- **📚 Documentation**: Refer to this README and inline code comments

## 📋 Changelog

### 🎉 Version 0.0.3 (Current)
- **New**: Enhanced project management with work orders
- **New**: Advanced component assignment system
- **New**: Improved table views and data presentation
- **New**: Better mobile navigation with hamburger menu
- **New**: Professional label generation with QR codes
- **Enhanced**: Settings page with comprehensive configuration options
- **Enhanced**: Backup and restore functionality
- **Enhanced**: Database configuration with network support
- **Fixed**: Various UI improvements and bug fixes
- **Performance**: Optimized component loading and filtering

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📋 License

This project is licensed under the MIT License. See [`LICENSE`](./LICENSE) for details.

---

📣 **Note to developers:** If you’re interested in contributing or reviewing the source, keep an eye out for the v1.0 release — the full repository will go public then!


## Support

For issues and questions, please use the GitHub issue tracker.
