# Docker Web Management UI

A modern, feature-rich web interface for managing Docker containers, volumes, and resources. This project provides a user-friendly dashboard for Docker management with real-time updates, advanced filtering, and comprehensive resource monitoring.

![Docker Web Management UI](screenshot.png)

## 🌟 Features

### Dashboard
- Real-time monitoring of container status and resource usage
- Interactive container management (start, stop, remove)
- Quick access to container logs and terminal
- Resource usage visualization (CPU, Memory, Network)

### Container Management
- Create and manage containers with an intuitive interface
- Real-time container status updates
- Interactive terminal access to running containers
- Container logs viewer with filtering capabilities
- Container resource usage monitoring
- Easy container configuration management

### Volume Management
- Comprehensive volume lifecycle management
- Volume usage tracking and monitoring
- Easy volume creation with driver options
- Volume pruning with space reclamation estimation
- Detailed volume information and mounted containers

### User Interface
- Modern, responsive design with Tailwind CSS
- Real-time updates and notifications
- Advanced filtering and search capabilities
- Keyboard shortcuts for common operations
- Dark/Light mode support
- Mobile-friendly interface

## 🚀 Getting Started

### Prerequisites
- Docker Engine (version 19.03 or higher)
- Node.js (version 14 or higher)
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/docker-web-management.git
cd docker-web-management
```

2. Configure the Docker API endpoint:
Edit the `API_BASE_URL` in the JavaScript files to point to your Docker API endpoint.

3. Serve the files using a web server:
```bash
# Using Python's built-in server
python -m http.server 8080

# Or using Node.js http-server
npx http-server
```

4. Access the dashboard:
Open your browser and navigate to `http://localhost:8080`

## 🔧 Configuration

### Docker API Configuration
The application requires access to the Docker API. To enable API access:

1. Configure Docker daemon to expose the API:
```json
{
  "hosts": ["tcp://0.0.0.0:2370", "unix:///var/run/docker.sock"]
}
```

2. Enable CORS for the API (for development):
Add appropriate CORS headers to your Docker API proxy.

### Security Considerations
- Use HTTPS for production deployments
- Implement authentication for the Docker API
- Configure appropriate CORS policies
- Use secure WebSocket connections for terminal access

## 💻 Development

### Project Structure
```
docker-web-management/
├── index.html          # Main dashboard
├── console.html        # Container terminal
├── volumes.html        # Volume management
├── css/               # Stylesheets
└── js/                # JavaScript files
```

### Technologies Used
- **Frontend Framework**: Vanilla JavaScript with jQuery
- **UI Framework**: Tailwind CSS
- **Icons**: Font Awesome
- **Charts**: Chart.js
- **Terminal**: Xterm.js
- **API Communication**: jQuery AJAX

## 🗺️ Roadmap

### Short-term Goals
- [ ] Add authentication and user management
- [ ] Implement network management interface
- [ ] Add container resource limits management
- [ ] Improve terminal performance
- [ ] Add container templates/presets

### Long-term Goals
- [ ] Multi-node Docker cluster management
- [ ] Custom dashboard layouts
- [ ] Container orchestration features
- [ ] Backup and restore functionality
- [ ] Extended monitoring and alerting
- [ ] Integration with container registries

### VDI Solutions Integration
- [ ] WebTop container templates
- [ ] Desktop environment provisioning
- [ ] User session management
- [ ] Resource allocation profiles
- [ ] Persistent storage management

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Docker Engine API](https://docs.docker.com/engine/api/)
- [Tailwind CSS](https://tailwindcss.com)
- [Chart.js](https://www.chartjs.org)
- [Xterm.js](https://xtermjs.org)
- [Font Awesome](https://fontawesome.com)
- [LinuxServer.io](https://www.linuxserver.io/) for WebTop containers

## 📞 Support

- Create an issue for bug reports or feature requests
- Join our [Discord community](https://discord.gg/yourdiscord)
- Check out our [Wiki](https://github.com/yourusername/docker-web-management/wiki) for detailed documentation

---

Made with ❤️ by the Docker Web Management Team
