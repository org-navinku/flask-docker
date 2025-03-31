```markdown
# Flask-Docker Application

A Dockerized Flask web application with SQLAlchemy integration, automated builds, and GitHub Actions deployment.

## Features

- Flask web framework
- SQLAlchemy for database operations
- Docker containerization
- Automated builds and pushes to Docker Hub on Git tags
- Gunicorn production server

## Prerequisites

- Python 3.9+
- Docker
- Docker Hub account
- Git

## Setup & Installation

### 1. Clone the repository
```bash
git clone git@github.com:org-navinku/flask-docker.git
cd flask-docker
```

### 2. Set up Python virtual environment
```bash
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

## Running the Application

### Development mode
```bash
export FLASK_APP=app.py
flask run
```

### Production mode (using Gunicorn)
```bash
gunicorn --bind 0.0.0.0:5000 app:app
```

## Docker Commands

### Build the Docker image
```bash
docker build -t navinkumarkc/flask-docker:v1.0.0 .
```

### Run the container
```bash
docker container run -d -p 5000:5000 navinkumarkc/flask-docker:v1.0.0
```

### Check running containers
```bash
docker ps
```

### Stop a container
```bash
docker stop <container-id>
```

## Docker Hub Deployment

### Login to Docker Hub
```bash
docker login -u navinkumarkc
```

### Push to Docker Hub
```bash
docker push navinkumarkc/flask-docker:v1.0.0
```

## Automated Deployment with GitHub Actions

The repository includes a GitHub Actions workflow that automatically builds and pushes the Docker image when you create a Git tag:

1. Create and push a new tag:
```bash
git tag -a v1.1.0 -m "Version 1.1.0"
git push origin v1.1.0
```

2. The workflow will:
   - Build the Docker image
   - Tag it with both the version number and 'latest'
   - Push to Docker Hub

## Requirements

The project uses these specific package versions:
```
Flask==2.0.3
Flask-SQLAlchemy==2.5.1
Flask-WTF==0.15.1
werkzeug==2.0.3
email-validator==2.1.1
SQLAlchemy==1.3.24
Flask-Chartjs==0.1.dev1
gunicorn
psycopg2-binary
```

## Troubleshooting

- **"externally-managed-environment" error**: Use a virtual environment as shown above
- **ModuleNotFoundError**: Make sure all dependencies are installed from requirements.txt
- **Docker push denied**: Ensure you're logged in to Docker Hub with `docker login`
