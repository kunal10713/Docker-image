
JenkinsFlow Project
====================

Project Overview
----------------

This project is a Flask-based web application designed to be containerized using Docker. The application is built, tested, and deployed using Jenkins, following a CI/CD pipeline.

Application
-----------

The application is a simple Python-based web application that uses Flask as the web framework. The application dependencies are managed using a `requirements.txt` file, ensuring that all required packages are installed in a virtual environment.

Jenkins Pipeline
----------------

Jenkins is used to automate the process of building, testing, and deploying the application. The pipeline consists of multiple stages:

1.  **Checkout SCM**: Clones the latest code from the GitHub repository.

2.  **Setup**: Creates a Python virtual environment and installs dependencies.

3.  **Testing**: Runs unit tests using `pytest` to ensure application functionality.

4.  **Login to Docker Hub**: Authenticates Jenkins with Docker Hub.

5.  **Build Docker Image**: Creates a Docker image of the application.

6.  **Push to Docker Hub**: Uploads the built image to Docker Hub for deployment.

Why Docker?
-----------

Docker is used to ensure that the application runs consistently across different environments. It eliminates compatibility issues and makes deployment easier by packaging the application along with its dependencies into a single container.

How Docker Was Used
-------------------

-   **Dockerfile**: Defines the steps to create the Docker image, including using an official Python base image, copying the application files, installing dependencies, and defining the entry point.

-   **Docker Build**: The Jenkins pipeline executes `docker build -t <image-name> .` to create the Docker image.

-   **Docker Push**: The built image is pushed to Docker Hub using `docker push <image-name>`.

How the Container Image Was Created
-----------------------------------

The container image was built using the following steps:

1.  **Pull Base Image**: `python:3.12.0b3-alpine3.18` is used as the base image.

2.  **Copy Files**: Application files are copied into the container.

3.  **Install Dependencies**: `pip install -r requirements.txt` ensures all dependencies are installed.

4.  **Define Entrypoint**: The application is started using `CMD ["python", "app.py"]`.

This setup ensures a robust, automated deployment pipeline with Jenkins and Docker, making it easy to build, test, and deploy the Flask application efficiently.