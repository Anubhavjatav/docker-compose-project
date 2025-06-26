🔁 Nginx reverse proxy (routes /service1 and /service2)

🐹 Service 1: A Go-based API

🐍 Service 2: A Python Flask API

📁 Folder Structure

.
├── docker-compose.yml
├── nginx
│   ├── Dockerfile
│   └── nginx.conf
├── service_1
│   ├── Dockerfile
│   ├── go.mod
│   └── main.go
├── service_2
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
└── README.md

🚀 How to Run

Make sure you have Docker + Docker Compose installed.

Step 1: Clone the Repository

git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

Step 2: Build and Run

docker-compose up --build

This will:

Build each service and Nginx

Create a custom bridge network

Wait until both services are healthy

Start Nginx reverse proxy

Step 3: Access in Browser

🐹 Service 1 → http://localhost:8080/

🐍 Service 2 → http://localhost:8080/

🧠 How Routing Works (Nginx)

Nginx listens on port 8080 and routes based on path:

/service1 → Service 1 (Go)

/service2 → Service 2 (Python)

The nginx.conf file removes the path prefix using rewrite and forwards requests internally.

Logs are stored in the container at /var/log/nginx/access.log.

🧪 Health Checks

Both services include a health check:

Checks root / route on port 5000

Nginx only starts after both are healthy

🧼 Clean Up

To stop and remove containers + volumes:

docker-compose down --volumes


