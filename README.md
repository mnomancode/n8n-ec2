
# n8n-ec2




## Project Overview

n8n-ec2 is a setup for running [n8n](https://n8n.io/) on an EC2 instance using Docker, with optional Nginx and SSL support.

## Setup Instructions

### 1. Prepare Environment

```sh
sudo vi .env
sudo vi Dockerfile
sudo vi Makefile
make init
sudo apt install make
```

### 2. Docker Commands

To access the running Docker container shell as root:

```sh
docker exec -it --user root <container_id> sh
# Example:
docker exec -it --user root 9e3506a3806d sh
```

### 3. Install Dependencies (on Ubuntu)

```sh
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
newgrp docker
sudo apt install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo apt install -y certbot python3-certbot-nginx
```

### 4. (Optional) Install Certbot on CentOS

```sh
sudo dnf install -y certbot python3-certbot-nginx
```

### 5. Setup n8n Directory and Docker Compose

```sh
mkdir ~/n8n
cd ~/n8n
nano docker-compose.yml
sudo docker compose up -d
```

### 6. Nginx and SSL

```sh
sudo nginx -t
sudo systemctl restart nginx
sudo certbot --nginx -d <your-domain>
# Example:
sudo certbot --nginx -d noman.n8nu.com
```

---

## Extras

See `comands.txt` for a full list of useful commands and setup steps.

---

## Related Resources

- GitHub: [shehan979/n8nec2](https://github.com/shehan979/n8nec2/)
- Video: [YouTube walkthrough](https://www.youtube.com/watch?v=-rcjJbUnaFQ)
