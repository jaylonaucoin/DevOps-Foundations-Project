# DevOps Foundations Course: Calculator App Project

- **Submission by:** Jaylon AuCoin
- **Submission Date:** 03 DEC 2024
- **GitHub Repository:** [Calculator App Project](https://github.com/jaylonaucoin/DevOps-Foundations-Project)
- **Docker Hub Repository:** [DevOps Docker Repository](https://hub.docker.com/repository/docker/jaucoin29/devops)
- **ZIP File URL:** [DevOps Project ZIP](https://www.dropbox.com/scl/fi/8mbq3q4bndf3gyg84d2lw/Jaylon-AuCoin-DevOps-Foundations-Project.zip?rlkey=y6euqrsrdsn9oxc4z05pznybz&st=x04fnxta&dl=0)

## Project Overview

  This is a multi-container Docker application that provides a calculator service with both a backend API built in 
  Python (Flask) and a frontend interface built using React. The purpose of the application is to demonstrate 
  containerization, service orchestration using Docker Compose, and CI/CD pipelines for automated builds, tests, and deployments.

### Structure
  - `Dockerfile` (backend): To containerize the Flask API for portability and deployment.
  - `Dockerfile` (frontend): To containerize the React application for consistent deployment.
  - `docker-compose.yaml`: To orchestrate both the backend and frontend services, ensuring they work together.
  - `.github/workflows/github-actions.yml`: Defines the CI/CD pipeline for automated builds, tests, and Docker image pushes.

## Docker Implementation

- **Backend `Dockerfile`** (Python API):

  The backend Dockerfile uses `python:3.9-slim` as the base image and installs dependencies from requirements.txt. It 
  copies the application code and exposes port 5000. The command to run the Flask app is specified.


- **Frontend `Dockerfile`** (React App):

  The frontend Dockerfile uses `node:14-alpine` base image to build the React app. It installs dependencies and builds the 
  project.

## Docker Compose Implementation

- **Services:** 
  - `backend`: The Flask API service that runs on port 5000.
  - `frontend`: The React application service that runs on port 3000. It depends on the `backend` service.

## CI/CD Pipeline Implementation

- The pipeline triggers on pushes and pull requests from the `main` branch.
- Stages: 
  - `frontend`: *Builds the React app and runs tests.*
    - **Checkout code**: Checks out the frontend code.
    - **Setup Node.js**: Sets up Node.js.
    - **Install dependencies**: Installs the frontend dependencies.
    - **Run tests**: Runs the React tests.
    - **Build the React app**: Builds the React app.
  - `backend`: *Builds the Python API and runs tests.*
    - **Checkout code**: Checks out the backend code.
    - **Setup Python**: Sets up Python.
    - **Install dependencies**: Installs the backend dependencies.
    - **Run tests**: Runs the Python tests.
  - `docker`: *Pushes the Docker images to the Docker Hub.*
    - **Checkout code**: Checks out the code.
    - **Setup Docker**: Sets up Docker Buildx.
    - **Build frontend Docker image**: Builds the frontend Docker image with `docker build`.
    - **Build backend Docker image**: Builds the backend Docker image with `docker build`.
    - **Push images to Docker Hub**: The frontend and backend images are tagged and pushed to the Docker Hub.

## Assumptions

- The CI/CD pipeline assumes valid secrets for Docker Hub are available.
- The CLI prompted me to declare the `babel` dependencies, so I did.
- The Docker documentation told me I should use `setup-buildx-action` to setup Docker, so I did.

## Lessons Learned

- Gained practical insights into containerization, service orchestration, and automated CI/CD pipelines.
- Learned how to create Dockerfiles for Python and React applications.
- Understood how to use Docker Compose to manage multi-container applications.
- Learned how to define CI/CD pipelines using GitHub Actions.
- Gained experience with Docker Hub for image storage and deployment.
- Learned how to troubleshoot Docker and CI/CD issues.
- Gained a deeper understanding of the DevOps workflow and best practices.

## Future Improvements

- Implement more robust error handling in the backend.
- Expand CI/CD stages to include deployment to cloud services like AWS or Azure.