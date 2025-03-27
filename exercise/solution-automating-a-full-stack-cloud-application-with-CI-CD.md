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
| **Backend Deployment**          | Node.js API runs on EC2 (Docker optional) with RDS integration | 20%    |        |
| **CI/CD Pipeline**              | GitHub Actions workflow automates deployments with secrets management and rollback | 25%    |        |
| **Security & Monitoring**       | IAM roles, encrypted RDS, CloudWatch alerts for errors/CPU | 20%    |        |

## Conclusion
This project demonstrates **end-to-end cloud automation** skills, covering:
1. **IaC** (Pulumi for AWS provisioning)
2. **CI/CD** (GitHub Actions for seamless deployments)
3. **Security Best Practices** (IAM, encryption, least privilege)
4. **Observability** (CloudWatch for logs/alerts)

The rubric prioritizes **CI/CD (25%)** and **Security (20%)**, reflecting real-world emphasis on automation and security. Learners prove competency in building **production-ready, scalable cloud applications**.
