# Solution: Automating a Full-Stack Cloud Application with CI/CD and IaC

## Objective
To develop and automate a **scalable full-stack application** on AWS using Infrastructure as Code (IaC) and CI/CD pipelines, integrating frontend (React), backend (Node.js), and database (RDS) services while ensuring security, reliability, and monitoring.

## Key Points
- **Infrastructure Automation**: Use **Pulumi** to provision AWS resources (EC2, RDS, S3) with reproducibility.
- **CI/CD Pipeline**: Implement **GitHub Actions** for automated deployments (frontend to S3, backend to EC2) with rollback mechanisms.
- **Security**: Apply least-privilege IAM roles, secure RDS-S3-EC2 connectivity, and secrets management.
- **Monitoring**: Configure **CloudWatch Logs/Alerts** for deployment failures, API errors, and resource thresholds (e.g., CPU ≥70%).

## Solution
The complete solution is documented in:  
`solution/solution-fullstack-aws-ci-cd-iac.md`

## Grading Rubric
**Total points: 100**

| Requirement                     | Notes                                      | Weight | Points |
|---------------------------------|-------------------------------------------|--------|--------|
| **Infrastructure as Code (IaC)** | Pulumi scripts deploy EC2, RDS, S3 with correct networking (VPC, security groups) | 20%    |        |
| **Frontend Deployment**         | React app deployed to S3 with public URL and backend API connectivity | 15%    |        |
| **Backend Deployment**          | Node.js API runs on EC2 with RDS integration | 20%    |        |
| **CI/CD Pipeline**              | GitHub Actions workflow automates deployments with secrets management  | 25%    |        |
| **Security & Monitoring**       | IAM roles, RDS, CloudWatch alerts for errors/CPU | 20%    |        |



## Solution Architecture

### 1. Infrastructure as Code (IaC) – Pulumi (20%)
- **AWS Resources Provisioned**:
  - **EC2** for backend deployment
  - **RDS (PostgreSQL/MySQL)** for database persistence
  - **S3** for frontend static hosting
- **Networking Configuration**:
  - **VPC, Subnets, and Security Groups** to enforce least-privilege access
  - **Private RDS Connectivity** (No public exposure)

### 2. Frontend Deployment – React on S3 (15%)
- **Automated CI/CD Deployment**:
  - React application built and deployed to **S3 via GitHub Actions**
  - **CloudFront CDN Integration** for low-latency global distribution
- **Secure API Connectivity**:
  - Proper **CORS configuration** for backend API communication

### 3. Backend Deployment – Node.js on EC2 (20%)
- **Node.js API Hosting**:
  - Deployed on **EC2 with auto-scaling capabilities**
  - **RDS Integration** with secrets managed via **AWS Secrets Manager**
- **CI/CD Automation**:
  - Automated testing and deployment triggered on Git pushes

### 4. CI/CD Pipeline – GitHub Actions (25%)
- **End-to-End Automation**:
  - **Build → Test → Deploy** workflow for both frontend and backend
  - **Rollback Mechanism** in case of deployment failures
- **Secure Secrets Handling**:
  - AWS credentials and database secrets stored in **GitHub Secrets**

### 5. Security & Monitoring – IAM & CloudWatch (20%)
- **Security Best Practices**:
  - **Least-Privilege IAM Roles** for CI/CD and application components
- **Observability & Alerting**:
  - **CloudWatch Alerts** for high CPU (≥70%), API errors, and deployment failures
  - **Centralized Logging** for troubleshooting and audit trails


## Conclusion
This project demonstrates **end-to-end cloud automation** skills, covering:
1. **IaC** (Pulumi for AWS provisioning)
2. **CI/CD** (GitHub Actions for seamless deployments)
3. **Security Best Practices** (IAM, encryption, least privilege)
4. **Observability** (CloudWatch for logs/alerts)

The solution emphasizes **real-world applicability**, ensuring scalability, security, and maintainability. Documentation in `solution-fullstack-aws-ci-cd-iac.md` includes setup instructions, best practices, and troubleshooting guidance.
