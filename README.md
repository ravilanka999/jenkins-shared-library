# Jenkins Shared Library

Reusable Jenkins pipeline library for standardising CI/CD delivery across microservices with built-in DevSecOps gates.

## Pipelines Included

| Pipeline | Language | Description |
|---|---|---|
| javaEKSPipeline | Java/Maven | Build, scan and deploy Java services to EKS |
| nodejsEKSPipeline | Node.js | Build, scan and deploy Node.js services to EKS |
| pythonEKSPipeline | Python | Build, scan and deploy Python services to EKS |
| samplePipeline | Any | Template pipeline for reference |

## Pipeline Stages
```
1. Checkout        → Pull source code from Git
2. Build           → Compile/package the application
3. Unit Tests      → Run application tests
4. Trivy Scan      → Container image vulnerability scanning
5. SonarQube       → Code quality and security analysis
6. Docker Build    → Build and tag container image
7. ECR Push        → Push image to Amazon ECR
8. Deploy to EKS   → Update Helm chart via Argo CD
```

## Features

- ✅ Single library for Java, Node.js and Python services
- ✅ Trivy image scanning at every build
- ✅ SonarQube quality gates enforced
- ✅ Automated ECR push with image tagging
- ✅ Argo CD deployment trigger post-build
- ✅ Standardised across all microservices teams

## Usage
```groovy
@Library('jenkins-shared-library') _

nodejsEKSPipeline {
  serviceName = 'catalogue'
  ecrRepo = '<YOUR_AWS_ACCOUNT_ID>.dkr.ecr.<YOUR_AWS_REGION>.amazonaws.com/catalogue'
  namespace = 'roboshop'
}
```

## Setup

1. Add this repo as a shared library in Jenkins
2. Configure AWS credentials for ECR push
3. Configure SonarQube token
4. Configure GitHub credentials

## Related Repos

- [catalogue-cd](https://github.com/ravilanka999/catalogue-cd) — Example CD pipeline
- [eks-argocd](https://github.com/ravilanka999/eks-argocd) — GitOps platform
