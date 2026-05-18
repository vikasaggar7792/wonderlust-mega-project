Jenkins CI/CD Pipeline for Kubernetes Deployment
This project leverages a Jenkins pipeline for Continuous Integration and Continuous Deployment (CI/CD) to automate the process of building, updating, and deploying the application on Kubernetes using ArgoCD. The pipeline follows these key steps:

Workspace Cleanup: The pipeline starts by cleaning up the workspace, ensuring that no residual files from previous builds remain, thus maintaining a clean environment for each new run.

Cloning the Repository: The latest version of the code is cloned from the GitHub repository to ensure that the pipeline always works with the most up-to-date code.

Docker Image Build: The pipeline then proceeds to build Docker images for both the backend and frontend applications. The images are tagged with the specified Docker tags (FRONTEND_DOCKER_TAG and BACKEND_DOCKER_TAG) to uniquely identify the versions being built.

Push Docker Images to DockerHub: After building the Docker images, the pipeline pushes the backend and frontend images to DockerHub, making them accessible for deployment in the Kubernetes environment.

Update Kubernetes Manifests: The pipeline updates the Kubernetes deployment manifests (backend.yaml and frontend.yaml) with the newly created Docker image tags. This ensures that the application in the Kubernetes cluster uses the latest version of the images.

Git Code Update and Push: The final step involves committing the updated Kubernetes manifests to the GitHub repository. This triggers the deployment process through ArgoCD, which automatically synchronizes the changes and deploys the updated application on the Kubernetes cluster.