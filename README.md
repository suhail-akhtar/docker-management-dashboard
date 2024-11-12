# Docker Web Management UI

A modern, feature-rich web interface for managing Docker containers, volumes, and resources. This project provides a user-friendly dashboard for Docker management with real-time updates, advanced filtering, and comprehensive resource monitoring.

### Note: ### 
Its an initial draft version, all html + javascript + jQuery code is inside in its own .html files, i'll separate it later,


[Docker Web Management UI]

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
- Nginx as reverse proxy (to handle CORS issue)
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Nginx configuration file ###
``` config

server {
    listen 2370;

    location / {
        proxy_pass http://172.22.106.116:2375;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        add_header 'Access-Control-Allow-Origin' '*' always;
        add_header 'Access-Control-Allow-Methods' 'GET, POST, DELETE, OPTIONS' always;
        add_header 'Access-Control-Allow-Headers' '*' always;

        if ($request_method = 'OPTIONS') {
            add_header 'Access-Control-Allow-Origin' '*' always;
            add_header 'Access-Control-Allow-Methods' 'GET, POST, DELETE, OPTIONS' always;
            add_header 'Access-Control-Allow-Headers' '*' always;
            add_header 'Access-Control-Max-Age' 1728000;
            add_header 'Content-Type' 'text/plain charset=UTF-8';
            add_header 'Content-Length' 0;
            return 204;
        }
    }

    location ~* ^/exec/ {
        proxy_pass http://172.22.106.116:2375;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";

        proxy_buffering off;
        proxy_cache off;
        proxy_read_timeout 86400;
        proxy_send_timeout 86400;

        add_header 'Access-Control-Allow-Origin' '*' always;
        add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS' always;
        add_header 'Access-Control-Allow-Headers' '*' always;
    }

    location ~* ^/containers/[^/]+/attach/ws {
        proxy_pass http://172.22.106.116:2375;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;

        proxy_read_timeout 86400s;
        proxy_send_timeout 86400s;
        proxy_buffering off;

        add_header 'Access-Control-Allow-Origin' '*' always;
        add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS' always;
        add_header 'Access-Control-Allow-Headers' '*' always;
    }
}

```
### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/docker-web-management.git
cd docker-web-management
```

2. Configure the Docker API endpoint:
Edit the `API_BASE_URL` in the JavaScript files to point to your Docker API endpoint (in each .html file).

3. Serve the files using a web server:
```bash
# using Node.js http-server
npx http-server

# or run it from vscode live server
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
Add appropriate CORS headers to your Docker or Nginx configuration  (already shared above).

### Security Considerations
- Use HTTPS for production deployments
- Implement authentication for the Docker API
- Configure appropriate CORS policies
- Use secure WebSocket connections for terminal access

## 💻 Development

## Screenshots

### Home Page
!Home.png

### Images Dashboard
!ImageDashboard.png

### Project Structure
```
Following structure will be implemented later, this time its plain structure all html files are in single root heierarchy + includeing jQuery + javascript for Docker API interaction
SO ignore following for now.

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
