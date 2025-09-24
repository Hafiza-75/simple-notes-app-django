# Simple Notes App
Built a full-stack Simple Notes App using React & Django, containerized with Docker, served via Nginx, and deployed on AWS Elastic Beanstalk for scalability.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Tech Stack

- Frontend: React
- Backend: Django
- Database: (SQLite/MySQL depending on config)
- Containerization: Docker
- Web Server / Reverse Proxy: Nginx
- Cloud Deployment: AWS Elastic Beanstalk / EC2

## AWS Deployment Options
### AWS Elastic Beanstalk

- Create a new Elastic Beanstalk application.
- Upload the Dockerized app as a deployment package.
- Elastic Beanstalk will automatically manage scaling and environment.

### AWS EC2

- Launch an EC2 instance (Ubuntu).
- Install Docker & Nginx.
- Pull and run the app container.
- Configure Nginx reverse proxy.
- Map domain or public IP to access globally.

## Installation
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```
Access the app at: http://localhost:8000

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`
### Configure Nginx (Reverse Proxy)

- Install Nginx:
```
sudo apt-get update
sudo apt install nginx -y
```

- Configure reverse proxy in /etc/nginx/sites-available/default:
```
server {
    listen 80;

    server_name your_domain_or_ip;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

- Restart Nginx:
```
sudo systemctl restart nginx
```
## Screenshot:
<img width="574" height="612" alt="nodoc" src="https://github.com/user-attachments/assets/b505c0db-c2f9-4318-93bb-2175b5999124" />
