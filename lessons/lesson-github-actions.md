# Lesson: Building CI/CD Pipelines with GitHub Actions

## Introduction

GitHub Actions is an integrated CI/CD platform that automates software development workflows directly within GitHub repositories. It enables teams to automate building, testing, and deploying applications through YAML-configured workflows triggered by GitHub events like pushes or pull requests. With its event-driven architecture and extensive marketplace of pre-built actions, GitHub Actions streamlines development processes while maintaining security and flexibility.


## Learning Outcomes

By the end of this lesson, you will:

1. Understand GitHub Actions' role in CI/CD and its key components: workflows, jobs, steps, and runners.
2. Create and configure YAML-based workflows to automate builds, tests, and deployments.
3. Implement secure cloud deployments (e.g., AWS) using GitHub Secrets for authentication.
4. Design end-to-end pipelines that trigger on GitHub events and enforce quality checks.
5. Apply best practices for secret management, error handling, and workflow optimization.

---

## 1. Introduction to GitHub Actions Workflows

### What is GitHub Actions, and how does it fit into CI/CD?

GitHub Actions is a CI/CD (Continuous Integration/Continuous Deployment) platform integrated into GitHub. It allows you to automate workflows for building, testing, and deploying applications directly from your repository.

### Key Features:

- **Event-Driven**: Workflows are triggered by GitHub events like push, pull request, or issue creation.
- **Customizable**: Define workflows using YAML files to suit your project's needs.
- **Extensible**: Use pre-built actions from the GitHub Marketplace or create your own.

### How do GitHub Actions workflows automate development processes?

GitHub Actions workflows are defined in YAML files and can automate tasks like:

- Running tests on every pull request.
- Building and deploying applications.
- Sending notifications or alerts.

### What are the key components of a GitHub Actions workflow?

- **Jobs**: A set of steps that run on the same runner (e.g., build, test). Jobs can run in parallel or sequentially.
- **Steps**: Individual tasks within a job (e.g., install dependencies, run tests).
- **Runners**: Machines (or containers) that execute the workflow.
- **Actions**: Reusable units of code that perform specific tasks (e.g., checking out code, building an application).

### How do you create and configure a GitHub Actions workflow file?

1. Create a `.github/workflows` directory in your repository.
2. Add a YAML file (e.g., `ci.yml`) to define the workflow.

#### Example Workflow:

```yaml
name: CI Pipeline  
on: [push]  
jobs:  
  build:  
    runs-on: ubuntu-latest  
    steps:  
      - name: Checkout code  
        uses: actions/checkout@v2  
      - name: Install dependencies  
        run: npm install  
      - name: Run tests  
        run: npm test  
```

---

## 2. Automating Build, Test, and Deployment Steps

### Automating Builds

- **Purpose**: Compile or package your application into a deployable artifact (e.g., a JAR file, Docker image, or binary).
- **Example:**

```yaml
- name: Build application  
  run: mvn clean package  
```

### Automating Tests

- **Purpose**: Run automated tests (e.g., unit tests, integration tests) to ensure code quality.
- **Example:**

```yaml
- name: Run unit tests  
  run: npm test  
```

#### Best Practices for Running Unit Tests in CI/CD Workflows:

- Run tests in parallel to save time.
- Use caching for dependencies to speed up test execution.
- Fail the build if tests fail.

### Automating Deployment

- **Purpose**: Deploy the application to a target environment (e.g., staging, production) after successful builds and tests.
- **Example (AWS Deployment):**

```yaml
- name: Deploy to AWS  
  uses: aws-actions/configure-aws-credentials@v2  
  with:  
    aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}  
    aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}  
    aws-region: us-east-1  
- name: Deploy application  
  run: aws s3 cp build/ s3://my-bucket/ --recursive  
```

### Example Workflow for Build, Test, and Deploy:

```yaml
name: CI/CD Pipeline  
on:  
  push:  
    branches:  
      - main  
jobs:  
  build-and-test:  
    runs-on: ubuntu-latest  
    steps:  
      - name: Checkout code  
        uses: actions/checkout@v3  
      - name: Set up Node.js  
        uses: actions/setup-node@v3  
        with:  
          node-version: '16'  
      - name: Install dependencies  
        run: npm install  
      - name: Run tests  
        run: npm test  
  deploy:  
    needs: build-and-test  
    runs-on: ubuntu-latest  
    steps:  
      - name: Checkout code  
        uses: actions/checkout@v3  
      - name: Deploy to AWS  
        uses: aws-actions/configure-aws-credentials@v2  
        with:  
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}  
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}  
          aws-region: us-east-1  
      - name: Deploy application  
        run: aws s3 cp build/ s3://my-bucket/ --recursive  
```

---

## 3. Using GitHub Actions Secrets for Cloud Authentication

### What are GitHub Actions Secrets?

- **Overview**: Secrets are encrypted environment variables stored in your GitHub repository. They are used to store sensitive information like API keys, passwords, and credentials.
- **Purpose**: Securely manage and use sensitive data in your workflows without exposing it in the code.

### How to Add Secrets

1. Go to your GitHub repository.
2. Navigate to **Settings > Secrets and variables > Actions**.
3. Click **New repository secret**.
4. Enter the secret name (e.g., `AWS_ACCESS_KEY_ID`) and value.
5. Save the secret.

### Best Practices for Secrets

1. **Limit Access**: Only grant access to secrets to trusted users and workflows.
2. **Rotate Secrets**: Regularly update and rotate secrets to minimize security risks.
3. **Audit Usage**: Monitor and audit the use of secrets in your workflows.

### Common CI/CD Pipeline Issues and Troubleshooting

- **Failed Tests**: Check test logs for errors.
- **Build Failures**: Verify dependencies and configurations.
- **Deployment Issues**: Check credentials and permissions.

### Real-World Use Cases for GitHub Actions in Cloud Deployments

- **Deploying to AWS EC2**: Use SSH to deploy applications.
- **Deploying Containers**: Push Docker images to ECR and deploy to ECS.
- **Infrastructure as Code**: Use Terraform to provision cloud resources.

---

## Conclusion

GitHub Actions transforms CI/CD by embedding automation directly into the development lifecycle. By mastering workflow configuration, secure deployments, and pipeline design, teams can achieve faster, more reliable software delivery. Whether deploying to cloud platforms or running tests, GitHub Actions reduces manual effort while ensuring consistency and security across projects.
