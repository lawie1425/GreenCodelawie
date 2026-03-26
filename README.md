# GreenCode

GreenCode is a full-stack system designed to support environmental, sustainability, and community-impact projects under Bos-Com.  
It consists of a **Spring Boot backend API** and a **React frontend** (new addition), with future integrations planned.

---

## 🚀 Features

### Backend (Spring Boot)
- RESTful API
- JWT/OAuth authentication
- PostgreSQL database support
- Centralised configuration (`config/`, `.env`)
- Dockerized for easy deployment
- Swagger/OpenAPI documentation

### Frontend (React)
- Modern React (Create React App)
- React Router for navigation
- Axios for API communication
- Authentication UI (login, password reset flow)
- Responsive UI with Tailwind CSS (recommended)
- Ready to connect to backend reset API

---

## 📁 Project Structure
GreenCode/
├── src/                 # Spring Boot source code
├── config/              # external configuration & scripts
├── docs/                # architecture, API docs
├── greencode-frontend/  # React frontend (new)
├── pom.xml              # Maven build file
└── docker-compose.yml   # Docker orchestration

## ⚙️ Installation

Follow one of the two options below to run GreenCode locally: Docker (recommended) or local development (Java + Node). Replace values in `.env` as needed — an example file is provided in `env.example`.

### Prerequisites
- Java 11 or later
- Maven (for the backend build)
- Node.js 16+ and npm (for the frontend)
- Docker & Docker Compose (recommended for quick start)

### Option A — Quick start with Docker (recommended)
1. Copy the example environment file and edit any values you need:

```bash
cp env.example .env
# edit .env if you need to change DB credentials or ports
```

2. Start services with Docker Compose:

```bash
docker-compose up --build -d
```

3. Verify the services are running:

```bash
docker-compose ps
```

4. Open the frontend at http://localhost:3000 (or the port configured in `.env`) and the backend API at http://localhost:8080 (default Spring Boot port). If your project exposes Swagger/OpenAPI you can visit the Swagger UI (commonly `/swagger-ui.html` or `/swagger-ui/index.html`).

To stop and remove containers:

```bash
docker-compose down
```

### Option B — Local development (without Docker)
1. Create and activate a Python/Node virtual environment if preferred (backend uses Java/Maven; frontend uses Node):

Backend (Java/Maven):

```bash
# ensure Java and Maven are installed
mvn -v
```

2. Prepare environment variables:

```bash
cp env.example .env
# edit .env to point to a running PostgreSQL instance or local DB
```

3. Build and run the backend:

```bash
mvn clean package
mvn spring-boot:run
```

4. Start the frontend (in a separate terminal):

```bash
cd greencode-frontend
npm install
npm start
```

### Quick verification
- Backend logs should show Spring Boot started and listening on the configured port.
- Open the frontend in your browser and perform a quick action (login, or home page load).  
- If the repo exposes a health or status endpoint, you can `curl` it, for example:

```bash
curl -I http://localhost:8080/
```

## 🛠️ Troubleshooting
- If ports are already in use, edit the port values in `.env` and corresponding `docker-compose.yml`.
- Database connection errors usually mean the DB URL or credentials in `.env` need updating — check container logs with `docker-compose logs`.
- If the frontend cannot reach the backend in Docker, ensure both services are on the same Docker network and the frontend's API base URL points to the backend service name defined in `docker-compose.yml` (not `localhost`).

## 📦 Contribution notes
- When making changes, create a feature branch using the naming format `docs/<short-description>` or `fix/<short-description>`.
- Commit messages should be descriptive and follow a simple style, e.g. `docs: improve installation instructions`.


