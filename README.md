# Instructor Guide: WD1450 — Introduction to AWS

## Week 5: DevOps & Automation in Cloud Computing

This week focuses on CI/CD pipelines, Infrastructure as Code (IaC), and cloud monitoring to automate deployments. Students will implement GitHub Actions workflows, deploy cloud resources with Pulumi, and automate full-stack applications. The week concludes with a hands-on assignment to automate a full-stack deployment using CI/CD and IaC and a quiz to assess knowledge.

---

## Learning Outcomes

By the end of this week, students will be able to:

1. Implement CI/CD pipelines using GitHub Actions for cloud applications
2. Deploy cloud infrastructure with Pulumi (IaC)
3. Automate full-stack deployments (frontend, backend, database)
4. Monitor CI/CD pipelines with AWS CloudWatch/Azure Monitor/GCP Logging
5. Compare CI/CD tools across AWS, Azure, and Google Cloud
6. Implement rollback strategies and security best practices for pipelines

---

## Curriculum Overview

The following activities, lessons, and knowledge checks have been included for your use in their suggested order:

| Type       | Title                                           | Time   | Markdown Link                                                |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ |
| Lesson     | CI/CD Fundamentals in Cloud Computing          | 120    | [lesson-cicd-fundamentals.md](lessons/lesson-cicd-fundamentals.md) |
| Activity   | Comparing CI/CD Services Across AWS, Azure, GCP | 60     | [activity-comparing-cicd-tools.md](activities/activity-comparing-cicd-tools.md) |
| Lesson     | Building CI/CD Pipelines with GitHub Actions    | 90     | [lesson-github-actions.md](lessons/lesson-github-actions.md) |
| Activity   | Deploying a React App via GitHub Actions       | 60     | [activity-github-actions-deployment.md](activities/activity-github-actions-deployment.md) |
| Lesson     | Infrastructure as Code (IaC) with Pulumi       | 90     | [lesson-pulumi-iac.md](lessons/lesson-pulumi-iac.md) |
| Activity   | Deploying Cloud Resources with Pulumi          | 60     | [activity-pulumi-deployment.md](activities/activity-pulumi-deployment.md) |
| Lesson     | Automating Full-Stack Deployments              | 120    | [lesson-fullstack-automation.md](lessons/lesson-fullstack-automation.md) |
| Activity   | CI/CD Pipeline for React + Node.js + Database  | 60     | [activity-fullstack-cicd.md](activities/activity-fullstack-cicd.md) |
| Lesson     | Monitoring & Securing CI/CD Pipelines          | 90     | [lesson-cicd-monitoring.md](lessons/lesson-cicd-monitoring.md) |
| Activity   | Setting Up CloudWatch Alerts for Pipelines     | 60     | [activity-cloudwatch-alerts.md](activities/activity-cloudwatch-alerts.md) |
| Assignment | Automate a Full-Stack App with CI/CD & IaC     | 360    | [assignment-automated-fullstack.md](assignments/assignment-automated-fullstack.md) |
| Quiz       | Week 5 Quiz                                    | 15     | [quiz-week5.md](knowledge-checks/quiz-week5.md) |
|            | **Learner Hours**                              | **19.5** |  |

---

## Day 1: CI/CD Fundamentals

| Type       | Title                                           | Time   | Markdown Link                                                | Points |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ | ------ |
| Lesson     | CI/CD Fundamentals in Cloud Computing          | 120    | [lesson-cicd-fundamentals.md](lessons/lesson-cicd-fundamentals.md) |        |
| Activity   | Comparing CI/CD Services Across AWS, Azure, GCP | 60     | [activity-comparing-cicd-tools.md](activities/activity-comparing-cicd-tools.md) |        |
|            | **Learner Hours**                              | **3**  |                                                              |        |

### Lesson: CI/CD Fundamentals in Cloud Computing

This lesson covers:
- **Principles of CI/CD and benefits for cloud deployments**
- **Comparison of AWS CodePipeline, Azure DevOps, and GCP Cloud Build**
- **Security best practices for pipelines**
- **Rollback strategies for failed deployments**

#### Stretch Goals
- Research blue/green deployment strategies
- Explore Jenkins as an alternative CI/CD tool

### Activity: Comparing CI/CD Services

This activity involves analyzing CI/CD features across cloud providers and documenting use cases for each.

#### Stretch Goals
- Build a simple pipeline in AWS CodePipeline
- Compare pricing models across providers

---

## Day 2: GitHub Actions for Cloud Deployments

| Type       | Title                                           | Time   | Markdown Link                                                | Points |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ | ------ |
| Lesson     | Building CI/CD Pipelines with GitHub Actions    | 90     | [lesson-github-actions.md](lessons/lesson-github-actions.md) |        |
| Activity   | Deploying a React App via GitHub Actions       | 60     | [activity-github-actions-deployment.md](activities/activity-github-actions-deployment.md) |        |
|            | **Learner Hours**                              | **2.5** |                                                              |        |

### Lesson: Building CI/CD Pipelines with GitHub Actions

This lesson covers:
- **YAML workflow structure and syntax**
- **Automating build, test, and deployment stages**
- **Secrets management for cloud credentials**
- **Environment-specific deployments**

#### Stretch Goals
- Implement branch protection rules
- Explore matrix builds for multi-environment testing

### Activity: Deploying a React App via GitHub Actions

This activity involves creating a workflow to deploy a React app to S3/Firebase using environment variables.

#### Stretch Goals
- Add automated testing (Jest) to the pipeline
- Implement caching for node_modules

---

## Day 3: Infrastructure as Code (Pulumi)

| Type       | Title                                           | Time   | Markdown Link                                                | Points |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ | ------ |
| Lesson     | Infrastructure as Code (IaC) with Pulumi       | 90     | [lesson-pulumi-iac.md](lessons/lesson-pulumi-iac.md) |        |
| Activity   | Deploying Cloud Resources with Pulumi          | 60     | [activity-pulumi-deployment.md](activities/activity-pulumi-deployment.md) |        |
|            | **Learner Hours**                              | **2.5** |                                                              |        |

### Lesson: Infrastructure as Code with Pulumi

This lesson covers:
- **Pulumi vs. Terraform comparison**
- **Writing Pulumi scripts in Python/TypeScript**
- **Managing cloud resource state**
- **Collaboration and team workflows**

#### Stretch Goals
- Explore Pulumi's automation API
- Research multi-cloud deployment strategies

### Activity: Deploying Cloud Resources with Pulumi

This activity involves writing a Pulumi script to deploy an EC2 instance or Azure App Service.

#### Stretch Goals
- Modify the script to add auto-scaling
- Implement tagging for cost tracking

---

## Day 4: Full-Stack Automation

| Type       | Title                                           | Time   | Markdown Link                                                | Points |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ | ------ |
| Lesson     | Automating Full-Stack Deployments              | 120    | [lesson-fullstack-automation.md](lessons/lesson-fullstack-automation.md) |        |
| Activity   | CI/CD Pipeline for React + Node.js + Database  | 60     | [activity-fullstack-cicd.md](activities/activity-fullstack-cicd.md) |        |
|            | **Learner Hours**                              | **3**  |                                                              |        |

### Lesson: Automating Full-Stack Deployments

This lesson covers:
- **Frontend deployment automation (S3/Firebase/Azure Blob)**
- **Backend API deployment (EC2/App Service/Cloud Run)**
- **Database provisioning (RDS/Azure SQL/Cloud SQL)**
- **Environment configuration management**

#### Stretch Goals
- Implement canary deployments
- Explore feature flag systems

### Activity: Full-Stack CI/CD Pipeline

This activity involves setting up a pipeline that deploys a React frontend, Node.js backend, and SQL database.

#### Stretch Goals
- Add database migration steps
- Implement health checks

---

## Day 5: Monitoring & Security

| Type       | Title                                           | Time   | Markdown Link                                                | Points |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ | ------ |
| Lesson     | Monitoring & Securing CI/CD Pipelines          | 90     | [lesson-cicd-monitoring.md](lessons/lesson-cicd-monitoring.md) |        |
| Activity   | Setting Up CloudWatch Alerts for Pipelines     | 60     | [activity-cloudwatch-alerts.md](activities/activity-cloudwatch-alerts.md) |        |
|            | **Learner Hours**                              | **2.5** |                                                              |        |

### Lesson: Monitoring & Securing CI/CD Pipelines

This lesson covers:
- **CloudWatch/Azure Monitor/GCP Logging integration**
- **Pipeline security with IAM roles and policies**
- **Vulnerability scanning in pipelines**
- **Incident response workflows**

#### Stretch Goals
- Implement OPA (Open Policy Agent) for policy enforcement
- Explore third-party monitoring tools

### Activity: CloudWatch Alerts Setup

This activity involves enabling logging and configuring alerts for pipeline failures.

#### Stretch Goals
- Set up Slack notifications
- Create custom dashboards

---

## Day 6: Assignments and Assessments

| Type       | Title                                           | Time   | Markdown Link                                                | Points |
| ---------- | ----------------------------------------------- | ------ | ------------------------------------------------------------ | ------ |
| Assignment | Automate a Full-Stack App with CI/CD & IaC     | 360    | [assignment-automated-fullstack.md](assignments/assignment-automated-fullstack.md) | 100    |
| Quiz       | Week 5 Quiz                                    | 15     | [quiz-week5.md](knowledge-checks/quiz-week5.md) | 10     |
|            | **Learner Hours**                              | **6.25** |                                                              |        |

### Assignment: Automate a Full-Stack App with CI/CD & IaC

This assignment requires students to:
1. Use Pulumi to provision:
   - Frontend hosting (S3/Firebase/Azure Blob)
   - Backend service (EC2/App Service/Cloud Run)
   - Database (RDS/Azure SQL/Cloud SQL)
2. Implement GitHub Actions workflows for:
   - Infrastructure provisioning
   - Application deployment
   - Database migrations
3. Configure:
   - Environment-specific variables
   - Monitoring and alerts
   - Security controls

#### Stretch Goals
- Implement multi-region deployment
- Add performance testing to pipeline

### Quiz: Week 5 Quiz

This quiz assesses knowledge on:
- CI/CD concepts and tools
- Infrastructure as Code principles
- Pipeline monitoring and security
- Multi-cloud deployment strategies
