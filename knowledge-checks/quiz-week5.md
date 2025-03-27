# DevOps & Automation in Cloud Computing 

## Quiz 1: Introduction to CI/CD in Cloud Computing

### Question 1: What is CI/CD?  
**Question:** What does CI/CD stand for in DevOps?  
- A. Continuous Inspection/Continuous Delivery  
- B. Continuous Integration/Continuous Deployment  
- C. Cloud Infrastructure/Cloud Deployment  
- D. Code Integration/Code Deployment  

**Correct Answer:** `B. Continuous Integration/Continuous Deployment`  
**Feedback:** CI/CD stands for Continuous Integration (automated code merging and testing) and Continuous Deployment/Delivery (automated deployment to production).

---

### Question 2: CI/CD Benefits  
**Question:** Which of the following is NOT a benefit of CI/CD?  
- A. Faster release cycles  
- B. Manual deployment approvals for every change  
- C. Early detection of bugs  
- D. Automated testing  

**Correct Answer:** `B. Manual deployment approvals for every change`  
**Feedback:** CI/CD reduces manual intervention by automating testing and deployments.

---

### Question 3: Cloud CI/CD Tools  
**Question:** Which tool is NOT typically used for CI/CD?  
- A. GitHub Actions  
- B. Jenkins  
- C. AWS S3  
- D. Azure Pipelines  

**Correct Answer:** `C. AWS S3`  
**Feedback:** AWS S3 is a storage service, not a CI/CD tool.

---

## Quiz 2: GitHub Actions for CI/CD

### Question 1: GitHub Actions Workflow  
**Question:** Where are GitHub Actions workflows defined?  
- A. In a `Dockerfile`  
- B. In a `.github/workflows/` YAML file  
- C. In the `package.json`  
- D. In AWS CloudFormation templates  

**Correct Answer:** `B. In a .github/workflows/ YAML file`  
**Feedback:** Workflows are defined in YAML files inside the `.github/workflows/` directory.

---

### Question 2: GitHub Secrets  
**Question:** What is the purpose of GitHub Secrets?  
- A. To store encrypted environment variables  
- B. To hide repository names  
- C. To bypass CI/CD checks  
- D. To manage GitHub user passwords  

**Correct Answer:** `A. To store encrypted environment variables`  
**Feedback:** GitHub Secrets securely store sensitive data like API keys.

---

### Question 3: Deployment with GitHub Actions  
**Question:** Which step is NOT part of a typical CI/CD pipeline?  
- A. Linting code  
- B. Manual code review for every commit  
- C. Running automated tests  
- D. Deploying to a cloud provider  

**Correct Answer:** `B. Manual code review for every commit`  
**Feedback:** CI/CD automates most checks, reducing manual reviews per commit.

---

## Quiz 3: Infrastructure as Code (IaC) with Pulumi

### Question 1: What is IaC?  
**Question:** What is the main advantage of Infrastructure as Code?  
- A. Manual server configuration  
- B. Version-controlled, repeatable infrastructure deployments  
- C. Higher cloud costs  
- D. Slower deployment times  

**Correct Answer:** `B. Version-controlled, repeatable infrastructure deployments`  
**Feedback:** IaC ensures infrastructure is defined in code for consistency and automation.

---

### Question 2: Pulumi vs. Terraform  
**Question:** How does Pulumi differ from Terraform?  
- A. Pulumi uses YAML, Terraform uses HCL  
- B. Pulumi supports general-purpose languages (Python, JavaScript), Terraform uses HCL  
- C. Pulumi is cloud-agnostic, Terraform is AWS-only  
- D. Pulumi doesn’t support IaC  

**Correct Answer:** `B. Pulumi supports general-purpose languages, Terraform uses HCL`  
**Feedback:** Pulumi allows using familiar programming languages for IaC.

---

### Question 3: Pulumi Deployment  
**Question:** What does Pulumi deploy when you run `pulumi up`?  
- A. Only the frontend  
- B. Only the database  
- C. The infrastructure defined in the Pulumi program  
- D. Nothing; it only validates code  

**Correct Answer:** `C. The infrastructure defined in the Pulumi program`  
**Feedback:** `pulumi up` deploys the cloud resources specified in the code.

---

## Quiz 4: Full-Stack CI/CD Automation

### Question 1: Frontend Deployment  
**Question:** Which service is commonly used to deploy a React frontend?  
- A. AWS EC2  
- B. AWS S3 + CloudFront  
- C. Google Cloud SQL  
- D. Azure Functions  

**Correct Answer:** `B. AWS S3 + CloudFront`  
**Feedback:** Static websites (React) are often hosted on S3 with CloudFront for CDN.

---

### Question 2: Backend Deployment  
**Question:** Which is a serverless option for backend deployment?  
- A. AWS EC2  
- B. AWS Lambda  
- C. Azure Virtual Machines  
- D. Google Compute Engine  

**Correct Answer:** `B. AWS Lambda`  
**Feedback:** Lambda is serverless, unlike EC2/VMs.

---

### Question 3: Database Automation  
**Question:** Which IaC tool can automate AWS RDS provisioning?  
- A. GitHub Actions  
- B. Pulumi  
- C. Docker  
- D. Kubernetes  

**Correct Answer:** `B. Pulumi`  
**Feedback:** Pulumi can define and deploy databases like RDS.

---

## Quiz 5: Monitoring & Rollback in CI/CD

### Question 1: CI/CD Monitoring  
**Question:** Which AWS service monitors CI/CD pipelines?  
- A. AWS CloudWatch  
- B. AWS S3  
- C. AWS IAM  
- D. AWS Redshift  

**Correct Answer:** `A. AWS CloudWatch`  
**Feedback:** CloudWatch tracks logs and metrics for deployments.

---

### Question 2: Rollback Strategies  
**Question:** What is a common rollback strategy?  
- A. Deleting all logs  
- B. Automatically reverting to the last stable deployment  
- C. Ignoring failed deployments  
- D. Manually rebuilding servers  

**Correct Answer:** `B. Automatically reverting to the last stable deployment`  
**Feedback:** Automated rollbacks restore previous working versions.

---

### Question 3: Securing Pipelines  
**Question:** How can you secure a CI/CD pipeline?  
- A. Using IAM roles for least privilege access  
- B. Storing secrets in plaintext  
- C. Disabling all logs  
- D. Allowing public write access  

**Correct Answer:** `A. Using IAM roles for least privilege access`  
**Feedback:** IAM roles restrict permissions to minimize security risks.
