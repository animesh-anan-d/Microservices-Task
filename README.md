# Microservices with Docker Compose

![Microservices Architecture](screenshots/architecture.png)

## Table of Contents
- [Setup Instructions](#setup-instructions)
- [Testing Services](#testing-services)
- [Troubleshooting](#troubleshooting)
- [Screenshots](#screenshots)

## Setup Instructions

### Prerequisites
- Docker Desktop ([Download](https://www.docker.com/products/docker-desktop))
- Git ([Download](https://git-scm.com/downloads))

### Installation Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/Microservices-Task.git
   cd Microservices-Task
Start all services:

bash
docker-compose up --build
Verify all containers are running:

bash
docker ps
Should show 4 containers with status "Up"

Testing Services
Endpoints
Service	URL	Command	Expected Response
User Service	http://localhost:3000/users	curl http://localhost:3000/users	[{"name":"Jane Smith"}]
Product Service	http://localhost:3001/products	curl http://localhost:3001/products	[{"price":99.99}]
Order Service	http://localhost:3002/orders	curl http://localhost:3002/orders	[]
Gateway Service	http://localhost:3003/api/users	curl http://localhost:3003/api/users	Routes to User Service
Browser Testing
Open these URLs in your web browser:

User Service: http://localhost:3000/users

Product Service: http://localhost:3001/products

Order Service: http://localhost:3002/orders

Troubleshooting
Common Issues
Port already in use:

bash
Error: Port 3000 is already allocated
Solution: Change ports in docker-compose.yml or run:

bash
netstat -ano | findstr :3000
taskkill /PID <PID> /F
Missing dependencies:

bash
Error: Cannot find module 'express'
Solution:

bash
docker-compose down
docker-compose build --no-cache
docker-compose up
Containers crash on startup:

bash
docker logs <container-name>  # Check specific errors
Empty responses:

Verify endpoint URLs are exact

Check service logs:

bash
docker-compose logs user-service
Complete Reset
bash
docker-compose down -v  # Remove containers and volumes
docker system prune -a  # Clean unused Docker objects
Screenshots
Docker Containers Running
Running Containers

User Service
User Service

Product Service
Product Service

Order Service
Order Service

License
This project is licensed under the MIT License - see LICENSE file for details.


### How to Use This README:
1. **Replace placeholders**:
   - Change `your-username` in the clone URL
   - Ensure your screenshots match the specified names in the `screenshots/` folder

2. **Save**:
   - Copy all content
   - Paste into a new file named `README.md` in your project root

3. **Verify**:
   - All links work
   - Image paths match your screenshot filenames
   - Port numbers match your `docker-compose.yml`

### Key Features:
- Complete setup-to-troubleshooting guide
- Ready-to-copy curl commands
- Visual verification with screenshots
- Clean markdown formatting
- License reference
