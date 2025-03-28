# Weaviate Vector Database Deployment Guide

This repository provides all necessary configurations and scripts to deploy the Weaviate vector database locally or on AWS EKS. The deployment includes support for the `img2vec-neural` and `text2vec-openai` models.

## Overview
Weaviate is a scalable, open-source vector search engine that allows efficient similarity searches across various data types. This setup provides:
- **Weaviate** as the core vector database
- **img2vec-neural** for image vectorization
- **text2vec-openai** for text embeddings
- **Persistent storage** configurations
- **Ingress and networking setup**

## Prerequisites
- Install [Docker](https://www.docker.com/)
- Install [kubectl](https://kubernetes.io/docs/tasks/tools/)
- Install [AWS CLI](https://aws.amazon.com/cli/) (for AWS deployment)
- Install [eksctl](https://eksctl.io/) (for AWS EKS management)

## Deploying with `deploy-k8s`
The `deploy-k8s` script automates the deployment and update process for both local and AWS environments.

### Usage
```sh
deploy-k8s deploy|update prod|dev
```

#### What the script does:
1. **Deployment or Update**: Installs or updates the Weaviate stack.
2. **Namespace Management**: Ensures Kubernetes namespaces exist.
3. **Storage Setup**: Configures persistent volume claims and storage classes.
4. **Secrets Handling**: Manages credentials for Weaviate and external services.
5. **Ingress Configuration**: Sets up networking for external access.
6. **Model Deployment**: Deploys Weaviate along with `img2vec-neural` and `text2vec-openai` models.
7. **Verification**: Ensures all services are running correctly.

#### Examples
- Deploy to production:
  ```sh
  deploy-k8s deploy prod
  ```
- Update development environment:
  ```sh
  deploy-k8s update dev
  ```

### Notes
- Ensure the security groups and IAM roles are correctly configured for EKS.
- Update `k8s/secret-weaviate.yaml` with the correct credentials before applying.
- Check Kubernetes pod statuses using:
  ```sh
  kubectl get pods -n weaviate
  ```

This guide helps you efficiently set up and manage a Weaviate-based vector search solution with integrated AI models. 🚀
