# Node.js CI/CD Pipeline with Jenkins and Docker
A fully automated CI/CD pipeline built for a Node.js application using **Jenkins**, **Docker**, **Git/GitHub**, and hosted on a local Windows environment.




Tech Stack Used

Jenkins: For automating the CI/CD pipeline.
Docker: For containerizing the application.
Node.js: A simple sample application.
GitHub: For source code version control.


Project Workflow & Architecture

Source Code Management: Code changes are pushed to GitHub.
CI/CD Automation: Jenkins (configured as a Windows service) automatically polls/fetches the repository using a declarative Jenkinsfile.
Containerization: Jenkins executes Docker commands to build a lightweight container image using node:18-alpine.
Automated Deployment: The pipeline stops/removes any existing containers, handles port conflicts, and successfully deploys the new container instance.


Jenkinsfile Pipeline Stages

The pipeline consists of 3 primary declarative stages:
Checkout: Pulls the latest source code from the main branch.
Build Docker Image: Builds a tagged Docker image (my-node-app:${env.BUILD_NUMBER}).
Deploy: Automatically manages container lifecycles and maps the container port 8080 to host port 8081.


Application Access
Once the pipeline reaches the SUCCESS state, the application is live and accessible at:
http://localhost:8081
