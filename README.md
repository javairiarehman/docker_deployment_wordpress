# 🛠️ WordPress + MySQL with Docker Compose

This project sets up a **WordPress website** with a **MySQL 5.7** database using Docker Compose. It also demonstrates how to use a custom Docker network with a static IP address for the WordPress container.

---

## 📂 Project Structure

.
├── docker-compose.yml
├── mysql/ # Local folder for MySQL data volume

yaml
Copy
Edit

---

## ⚙️ Prerequisites

Make sure the following are installed on your system:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/)

---

## 🚀 Installation & Running the Project

1. **Clone or download** this project directory.

2. **Create a folder for MySQL volume** (if it doesn't already exist):

   ```bash
   mkdir mysql
Run the containers:

bash
Copy
Edit
docker-compose up -d
Visit the WordPress site in your browser:

arduino
Copy
Edit
http://localhost:8089
🔧 Configuration Details
Docker Services
WordPress

Image: wordpress:latest

Port: 8089 (host) → 80 (container)

Custom static IP: 10.56.1.21

MySQL

Image: mysql:5.7

Persistent data stored in ./mysql folder

Environment Variables
Variable	WordPress	MySQL
WORDPRESS_DB_HOST	mysql	
WORDPRESS_DB_USER	root	
WORDPRESS_DB_PASSWORD	coffee	coffee
WORDPRESS_DB_NAME	wordpress	wordpress
MYSQL_ROOT_PASSWORD		coffee
MYSQL_DATABASE		wordpress

🌐 Networking
A custom bridge network is created with this subnet:

yaml
Copy
Edit
networks:
  ohyeah:
    ipam:
      config:
        - subnet: "10.56.1.0/24"
The WordPress container is assigned static IP 10.56.1.21. However, this IP is internal to Docker and not accessible directly from the browser. You should use:

arduino
Copy
Edit
http://localhost:8089
🧹 Stopping & Cleaning Up
To stop and remove all containers, volumes, and the custom network:

bash
Copy
Edit
docker-compose down
To remove volumes as well (destructive):

bash
Copy
Edit
docker-compose down -v
📌 Notes
Your WordPress content will persist in the container and MySQL volume.

If you change the docker-compose.yml file, you may need to rebuild or restart the containers.

This setup is good for local development or learning. For production, consider securing the setup and using external volumes.
