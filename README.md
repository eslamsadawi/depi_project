# Zay Shop App CI/CD Pipeline Project

## INTRODUCTION

This presentation outlines the development and implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline for automating the deployment of a website from GitHub to a Kubernetes cluster. The pipeline leverages a variety of tools including Jenkins, Ansible, Docker, and Kubernetes to create a streamlined, efficient process that ensures the web application is continuously integrated, deployed, and updated based on changes to the source code repository.

## Tools and Technologies Used

- **Jenkins**: Automation server used for building the CI/CD pipeline.
- **Ansible**: Configuration management tool used to automate deployment processes.
- **Kubernetes**: Container orchestration system for automating application deployment.
- **Docker**: Containerization platform for deploying applications in lightweight containers.
- **GitHub**: Source control platform used to store the application's code.
- **Git**: Source version control system.
- **Minikube**: Local Kubernetes cluster for development and testing.

## Project Structure

```
├── Ansible/              # Ansible playbooks for automation
│   ├── create-image-cafe-app.yml  # Builds Docker image
│   ├── inventory         # Ansible inventory file
│   └── k8s-deploy.yml    # Deploys app to Kubernetes
├── K8S/                  # Kubernetes manifests
│   ├── depi-shop-deployment.yml    # Pod deployment config
│   └── dpei-shop-svc.yml  # Service configuration
├── assets/               # Web app static assets
├── Jenkinsfile           # Jenkins pipeline definition
├── docker-compose.yml    # Local Docker deployment config
└── [HTML files]          # Web application source
```

## Pipeline Workflow

1. **Code Changes**: Developer pushes changes to GitHub repository
2. **Jenkins Trigger**: Webhook triggers Jenkins pipeline
3. **Checkout**: Jenkins pulls the latest code
4. **Transfer**: Code is transferred to Ansible server
5. **Build**: Ansible builds Docker image
6. **Test**: Basic tests are executed
7. **Verify Kubernetes**: Pipeline checks Kubernetes cluster connectivity
8. **Deploy**: Application is deployed to Kubernetes with:
   - Pods running the containerized application
   - Service exposing the application
9. **Expose Service**: Application is made accessible via public IP

## Setup Instructions

### Prerequisites

- Jenkins server with necessary plugins
- Ansible server
- Kubernetes cluster (Minikube)
- Docker installed on build server
- Git repository access

### Jenkins Setup

1. Install required plugins:
   - Git Integration
   - SSH Agent
   - Pipeline

2. Configure Jenkins credentials:
   - Add SSH credentials for Ansible server
   - Add GitHub webhook

### Deployment Configuration

1. Ensure Minikube is running:
   ```bash
      minikube start
   ```

2. Access the application:
   - The application is exposed on port 8080
   - Access via: http://[server-public-ip]:8080

## Troubleshooting

### Common Issues

1. **ImagePullBackOff Error**:
   - Ensure Docker image is built correctly
   - Check image is loaded into Minikube with: `minikube image load depi-shop:latest`

2. **Service Not Accessible**:
   - Verify port forwarding is active
   - Check security group settings if using cloud provider
   - Ensure the service is running with: `kubectl get svc`

3. **Pipeline Failures**:
   - Check Jenkins logs
   - Verify SSH connectivity to Ansible server

## Design



## Demo

![Screenshot from 2025-04-16 21-28-28](https://github.com/user-attachments/assets/ba9666c0-3235-41c8-bed1-cd413442694e)

## Future Enhancements

1. **Auto-scaling Configuration**: Implement Kubernetes Horizontal Pod Autoscaler
2. **Blue/Green Deployment**: Implement zero-downtime deployment strategy
3. **SSL/TLS Configuration**: Secure the application with HTTPS
4. **Multi-environment Support**: Add staging and production environments

## Contributors

- Eslam Mahmoud Sadawi
- Mohamed Mahmoud Sabek
- Ahmed Magdy Amin
- Samira Ashraf Mohamed
- Fares Mohamed Ali

## License

This project is licensed under the MIT License - see the LICENSE file for details.


