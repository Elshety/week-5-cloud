# Final Project: Automating a Full-Stack Cloud Application with CI/CD and IaC

## Project Objective
The objective of this project is to apply the concepts learned in cloud computing by developing and automating a full-stack cloud application. The goal is to create a scalable, automated deployment pipeline that integrates the frontend, backend, and database services across AWS using CI/CD pipelines and Infrastructure as Code (IaC).

---

## Prerequisites

#### 1. Accounts & Services
- **AWS Account** (with permissions for EC2, RDS, S3, IAM, and CloudWatch)
- **GitHub Account** (for repository management and GitHub Actions)
- **Pulumi Account** (for IaC deployment)

#### 2. Software & Tools
- **Git & GitHub CLI** (version control)
- **Pulumi CLI** (AWS infrastructure automation)
- **VS Code (or preferred IDE)** (code editing)
- **AWS CLI** (AWS service management)
- **Node.js (LTS version)** (runtime for Pulumi and backend)

#### 3. Environment Setup
- Install and configure the AWS CLI (`aws configure`).
- Install the Pulumi CLI (`npm install -g pulumi`).
- Set up a GitHub repository and configure GitHub Actions.

---

# Starter Files
You will build the project from scratch, but a pre-configured folder structure is available for reference:


- `/frontend`        # React/Next.js application
- `/backend`         # Node.js/Express API
- `/infrastructure`  # Pulumi IaC definitions

---

# Project Walkthrough

## 1. Installing Required Tools

### Node.js Installation
#### Option A: Official Installer (Recommended for Beginners)
1. Download the LTS version from the [Node.js website](https://nodejs.org/).
2. Run the installer with default settings.

#### Option B: Using nvm (Advanced Users)
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash  
nvm install --lts  
nvm use --lts  
```
**Verification:**
```bash
node --version  # Expected: v18.x or later  
npm --version   # Expected: 9.x or later  
```

### Pulumi Installation
```bash
curl -fsSL https://get.pulumi.com | sh  
```

### AWS CLI Installation
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"  
unzip awscliv2.zip  
sudo ./aws/install  
aws --version  # Verify installation  
```

### Git Installation
#### Linux (Debian/Ubuntu):
```bash
sudo apt-get update && sudo apt-get install git -y  
```
#### Mac (via Homebrew):
```bash
brew install git  
```
**Verification:**
```bash
git --version  
```

## 2. Configuring AWS Credentials
Run:
```bash
aws configure  
```
Enter the following when prompted:
- **AWS Access Key ID** (from IAM user)
- **AWS Secret Access Key**
- **Default Region** (e.g., `us-east-1`)
- **Default Output Format** (`json`)

> **Security Note:** Never use root account credentials—always create an IAM user with least-privilege permissions.

## 3. Setting Up the GitHub Repository

### Creating the Repository
1. Go to [GitHub.com](https://github.com/).
2. Click `+ New repository`.
3. Name it (e.g., `final-fullstack-cloud-project`).
4. Set to **Private** (recommended).
5. Do not initialize with a README (we’ll do this manually).
6. Click **Create repository**.

### Cloning & Initial Setup
```bash
git clone https://github.com/your-username/final-fullstack-cloud-project.git  
cd final-fullstack-cloud-project  
echo "# Fullstack Cloud Project" > README.md  
git add README.md  
git commit -m "Initial commit"  
git push origin main  
```

## VS Code Integration (Recommended Setup)
1. Open VS Code → `File` → `Open Folder` (select project directory).
2. Install recommended extensions:
   - **ESLint** (JavaScript/TypeScript linting)
   - **Prettier** (code formatting)
   - **Pulumi** (IaC support)

---

## Project Structure

A well-organized project structure is essential for:

- **Separation of Concerns** – Clear division between frontend, backend, and infrastructure.
- **Maintainability** – Easier debugging, updates, and scalability.
- **Collaboration** – Streamlined teamwork with modular components.
- **CI/CD Integration** – Automated workflows depend on a logical directory layout.
- **System Architecture Clarity** – Reflects the application’s design at a glance.

### Final Directory Layout

```plaintext
final-fullstack-cloud-project/  
├── frontend/            # Frontend application (React, Vue, etc.)  
│   ├── public/          # Static assets (HTML, images)  
│   ├── src/             # Application code (components, styles)  
│   └── package.json     # Dependencies and scripts  
├── backend/             # Backend services (Node.js, Python, etc.)  
│   ├── src/             # API routes, business logic  
│   ├── config/          # Database/cloud configurations  
│   └── package.json     # Server dependencies  
├── infrastructure/      # Infrastructure as Code (Pulumi)  
│   ├── index.ts         # AWS resource definitions  
│   └── Pulumi.yaml      # Project configuration  
├── .github/             # GitHub Actions workflows  
│   └── workflows/       # CI/CD pipeline definitions  
└── README.md            # Project overview, setup, and usage  
```


---



## 3.Frontend (React) Setup

### 1. Initializing the React Application

#### Creating the React App

**Command:**

```bash
npx create-react-app frontend --template typescript
cd frontend
```

#### What Happens?
- `npx` downloads and runs `create-react-app` without global installation.
- Creates a `frontend/` directory with:
  - TypeScript preconfigured (`tsconfig.json`).
  - Starter files (`.tsx` instead of `.js`).
  - All required dependencies installed.

#### Key Generated Files:

| File           | Purpose                         |
|---------------|---------------------------------|
| `tsconfig.json` | TypeScript configuration       |
| `src/App.tsx`  | Main React component           |
| `src/index.tsx` | Entry point                    |
| `package.json` | Dependencies and scripts       |

#### Verification:

```bash
npm start
```

- Starts dev server at `http://localhost:3000`.
- Displays default React welcome page.
- Stop server: Press `Ctrl+C` in the terminal.

---

### 2. Building the Frontend Application

#### Modifying `App.tsx`

**Location:** `frontend/src/App.tsx`

**Key Features:**
- **State Management**: `useState` for dynamic data.
- **API Calls**: `fetch` to connect to the backend.
- **TypeScript**: Define interfaces for type safety (replace `any[]` later).
- **Error Handling**: Basic `try/catch` for API errors.

---

### 3. Configuring Environment Variables

#### Creating `.env`

**Location:** `frontend/.env`

**Purpose:**
- Store environment-specific settings (e.g., API URLs).
- Keep secrets out of source control.

#### Content:

```env
REACT_APP_API_URL=http://your-ec2-public-ip:3001
```

#### Rules:
- Variables must start with `REACT_APP_` to be accessible in React.
- Add `.env` to `.gitignore` to avoid exposing secrets.

---

### 4. Testing the Frontend Locally

#### Steps:

1. Start the dev server:

    ```bash
    cd frontend
    npm start
    ```

2. Verify:
   - App opens at `http://localhost:3000`.
   - No errors in the browser console.
  
---

## 4. Backend (Node.js) Setup

### 1. Initializing the Backend Project

#### Creating the Node.js Project

Commands:

```bash
# Navigate to backend directory
cd ../backend

# Initialize Node.js project (creates package.json)
npm init -y

# Install production dependencies
npm install express cors pg dotenv

# Install development dependencies (TypeScript support)
npm install --save-dev typescript @types/express @types/cors @types/node @types/pg nodemon
```

#### Key Dependencies:

| Package    | Purpose                               |
|-----------|---------------------------------------|
| express   | Web framework                         |
| cors      | Cross-Origin Resource Sharing        |
| pg        | PostgreSQL client                    |
| dotenv    | Environment variables                |
| typescript| TypeScript compiler                  |
| nodemon   | Auto-restart server during development |

---

### 2. Configuring TypeScript

#### Initialize TypeScript:

```bash
npx tsc --init
```

This generates `tsconfig.json` with default settings.

#### Recommended `tsconfig.json` Adjustments:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  }
}
```

---

### 3. Creating the Backend Application

#### Main Application File (`src/index.ts`)

Location: `backend/src/index.ts`

---

### 4. Database Initialization

#### SQL Script (`src/db-init.sql`)

Location: `backend/src/db-init.sql`

---

### 5. Environment Configuration

#### Create `.env` File

```bash
touch .env
```

#### Sample `.env` Content:

```env
DB_USER=admin
DB_HOST=localhost
DB_NAME=mydatabase
DB_PASSWORD=securepassword
DB_PORT=5432
PORT=3001
```

#### Security Note:

- Add `.env` to `.gitignore`
- Never commit sensitive data to version control

---

### 6. Development Setup

#### `package.json` Scripts

```json
"scripts": {
  "build": "tsc",
  "start": "node dist/index.js",
  "dev": "nodemon src/index.ts",
  "watch": "tsc -w"
}
```

#### Nodemon Configuration (`nodemon.json`)

```json
{
  "watch": ["src"],
  "ext": "ts,json",
  "ignore": ["src/**/*.spec.ts"],
  "exec": "ts-node src/index.ts"
}
```

---

### 7. Running the Backend

#### Development Mode

```bash
npm run dev
```

- Auto-restarts server on file changes
- Uses `ts-node` for direct TypeScript execution

#### Testing Endpoints

1. **Health Check:**
   
   `http://localhost:3001/api/health`
   
   Expected Response:
   
   ```json
   {"status":"OK"}
   ```
   
2. **Test Message:**
   
   `http://localhost:3001/api/message`
   
   Expected Response:
   
   ```json
   {"message":"Hello from backend!"}
   


---

## 5. Pulumi Infrastructure as Code

### Initialize Pulumi Project

```
cd ../infrastructure
pulumi new aws-javascript
# Follow prompts to name your project (e.g., fullstack-cloud) and stack (e.g., dev)
```

### Install Required Pulumi Packages

```
npm install @pulumi/aws @pulumi/awsx @pulumi/pulumi
Create Infrastructure Code
```

### Create infrastructure/index.js:

```javascript
const aws = require("@pulumi/aws");
const awsx = require("@pulumi/awsx");
const pulumi = require("@pulumi/pulumi");

// Create a VPC
const vpc = new awsx.ec2.Vpc("fullstack-vpc", {
    cidrBlock: "10.0.0.0/16",
    numberOfAvailabilityZones: 2,
    subnets: [{ type: "public" }, { type: "private" }],
});

// Create an S3 bucket for the frontend
const frontendBucket = new aws.s3.Bucket("frontend-bucket", {
    website: {
        indexDocument: "index.html",
        errorDocument: "index.html",
    },
    acl: "public-read",
});

// Create a bucket policy to allow public read access
const bucketPolicy = new aws.s3.BucketPolicy("bucketPolicy", {
    bucket: frontendBucket.bucket,
    policy: frontendBucket.bucket.apply(bucketName => JSON.stringify({
        Version: "2012-10-17",
        Statement: [{
            Effect: "Allow",
            Principal: "*",
            Action: ["s3:GetObject"],
            Resource: [`arn:aws:s3:::${bucketName}/*`],
        }],
    })),
});

// Create an RDS PostgreSQL instance
const dbSubnetGroup = new aws.rds.SubnetGroup("db-subnet-group", {
    subnetIds: vpc.privateSubnetIds,
});

const dbSecurityGroup = new aws.ec2.SecurityGroup("db-security-group", {
    vpcId: vpc.vpcId,
    ingress: [{
        protocol: "tcp",
        fromPort: 5432,
        toPort: 5432,
        cidrBlocks: ["0.0.0.0/0"],
    }],
    egress: [{
        protocol: "-1",
        fromPort: 0,
        toPort: 0,
        cidrBlocks: ["0.0.0.0/0"],
    }],
});

const rdsInstance = new aws.rds.Instance("backend-db", {
    engine: "postgres",
    instanceClass: "db.t3.micro",
    allocatedStorage: 20,
    dbSubnetGroupName: dbSubnetGroup.name,
    vpcSecurityGroupIds: [dbSecurityGroup.id],
    username: "admin",
    password: "securepassword123", // In production, use a secret manager
    skipFinalSnapshot: true,
    publiclyAccessible: true,
});

// Create an EC2 instance for the backend
const ec2SecurityGroup = new aws.ec2.SecurityGroup("backend-security-group", {
    vpcId: vpc.vpcId,
    ingress: [
        {
            protocol: "tcp",
            fromPort: 22,
            toPort: 22,
            cidrBlocks: ["0.0.0.0/0"],
        },
        {
            protocol: "tcp",
            fromPort: 3001,
            toPort: 3001,
            cidrBlocks: ["0.0.0.0/0"],
        },
    ],
    egress: [{
        protocol: "-1",
        fromPort: 0,
        toPort: 0,
        cidrBlocks: ["0.0.0.0/0"],
    }],
});

const ami = aws.ec2.getAmi({
    filters: [
        { name: "name", values: ["amzn2-ami-hvm-*-x86_64-gp2"] },
    ],
    owners: ["137112412989"], // Amazon
    mostRecent: true,
}).then(ami => ami.id);

const userData = `#!/bin/bash
sudo yum update -y
sudo amazon-linux-extras install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
`;

const ec2Instance = new aws.ec2.Instance("backend-instance", {
    instanceType: "t3.micro",
    vpcSecurityGroupIds: [ec2SecurityGroup.id],
    subnetId: vpc.publicSubnetIds[0],
    ami: ami,
    keyName: "your-key-pair-name", // Replace with your EC2 key pair name
    userData: userData,
    tags: {
        Name: "BackendServer",
    },
});

// Export the outputs
exports.frontendUrl = pulumi.interpolate`http://${frontendBucket.websiteEndpoint}`;
exports.backendUrl = pulumi.interpolate`http://${ec2Instance.publicIp}:3001`;
exports.dbEndpoint = rdsInstance.endpoint;
```


---


