# 📚 Complete DevOps & Cloud Internship Roadmap
## 16 Sessions | 12-16 Weeks | 10 hrs/week

**Goal:** Land 50k+ internship with portfolio projects  
**Approach:** Learn-by-doing, deploy every week, interview-ready

---

## 🎯 Quick Overview

| Phase | Sessions | Duration | Focus |
|-------|----------|----------|-------|
| **Foundations** | 1-9 | Weeks 1-4 | Linux, Git, Python, Networking |
| **Cloud Basics** | 10-14 | Weeks 5-8 | AWS EC2, IAM, VPC, S3, RDS |
| **Containers & IaC** | 15-16 | Weeks 9-10 | Docker, Terraform |
| **CI/CD & Automation** | 17-18 | Weeks 11-12 | GitHub Actions, deployment |
| **Portfolio Projects** | 19-20 | Weeks 13-14 | Build 2-3 real projects |
| **Interview Prep** | 21-22 | Weeks 15-16 | Polish, mock interviews, apply |

---

# 🔥 PHASE 1: FOUNDATIONS (Weeks 1-4)

## Session 1: Linux Fundamentals I
**Duration:** 6-8 hours  
**Topics:**
- Linux filesystem hierarchy (/, /home, /etc, /var, /usr, /bin)
- File types and inodes
- Kernel, shell, and the boot process
- Basic commands: pwd, ls, cd, mkdir, touch, cat, cp, mv, rm

**Hands-on Lab:**
- Navigate the filesystem
- Create files and folders
- Practice file operations
- Understand directory structure

**Deliverable:**
- Screenshot of `tree` output showing your folder structure
- Commit to GitHub with message: "Session 1: Linux filesystem navigation"

**Resources:**
- Linux man pages: `man ls`, `man cd`
- Ultimate Linux Guide: https://github.com/iam-veeramalla/ultimate-linux-guide

---

## Session 2: Linux Fundamentals II - Permissions & Users
**Duration:** 6-8 hours  
**Topics:**
- File permissions model (rwx, octal notation)
- chmod and chown commands
- Users, groups, and ownership
- sudo and sudo privileges
- Package managers (apt on Ubuntu/Debian)
- Basic system monitoring (top, ps, df, du)

**Hands-on Lab:**
- Create test files with different permissions
- Practice chmod (777, 755, 644, 600)
- Understand owner/group/others
- Install a simple package (curl, wget)
- Monitor system resources

**Deliverable:**
- Bash script demonstrating permission changes
- Screenshot of `ls -la` output with various permissions
- Commit: "Session 2: File permissions and user management"

**Interview Question Prep:**
- What does chmod 755 mean?
- Difference between chmod and chown?
- What's the difference between sudo and su?

---

## Session 3: Shell Scripting I - Basics
**Duration:** 8-10 hours  
**Topics:**
- Shebang (#!/bin/bash)
- Variables and quoting rules (single vs double quotes)
- echo and printf
- Read user input
- Conditionals: if/then/else, test operators
- Comparison operators: -eq, -ne, -lt, -gt, -z, -n

**Hands-on Lab - Write 3 Scripts:**

**Script 1: Hello World & Variables**
```bash
#!/bin/bash
NAME="$1"
echo "Hello, $NAME!"
```

**Script 2: User Input & Conditional**
```bash
#!/bin/bash
read -p "Enter your age: " age
if [ $age -ge 18 ]; then
    echo "You are an adult"
else
    echo "You are a minor"
fi
```

**Script 3: File Check**
```bash
#!/bin/bash
FILE="$1"
if [ -f "$FILE" ]; then
    echo "File exists"
elif [ -d "$FILE" ]; then
    echo "Directory exists"
else
    echo "File/directory not found"
fi
```

**Deliverable:**
- 3 working bash scripts in `LABS/bash-scripts/`
- Test each script and show output
- Commit: "Session 3: Bash scripting basics - variables and conditionals"

---

## Session 4: Shell Scripting II - Loops & Functions
**Duration:** 8-10 hours  
**Topics:**
- Loops: for, while, until
- Loop control: break, continue
- Functions: definition, arguments, return values
- Exit codes and error handling
- Defensive scripting: set -euo pipefail
- Logging and debugging

**Hands-on Lab - Write 4 Scripts:**

**Script 1: For Loop**
```bash
#!/bin/bash
for i in {1..5}; do
    echo "Iteration $i"
done
```

**Script 2: While Loop (File Processing)**
```bash
#!/bin/bash
while IFS= read -r line; do
    echo "Line: $line"
done < "$1"
```

**Script 3: Function**
```bash
#!/bin/bash
greet() {
    local name=$1
    echo "Hello, $name!"
}
greet "Alice"
greet "Bob"
```

**Script 4: System Health Monitor** (Project!)
```bash
#!/bin/bash
set -euo pipefail

log() {
    echo "[$(date +'%Y-%m-%d %H:%M:%S')] $1"
}

check_disk() {
    local usage=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')
    log "Disk usage: $usage%"
    if [ $usage -gt 80 ]; then
        log "WARNING: Disk usage high!"
    fi
}

check_memory() {
    local mem=$(free | awk 'NR==2 {printf("%.0f", $3/$2 * 100)}')
    log "Memory usage: $mem%"
}

log "System Health Check Started"
check_disk
check_memory
log "System Health Check Completed"
```

**Deliverable:**
- 4 working bash scripts
- System Health Monitor script fully functional
- Commit: "Session 4: Bash loops, functions, and system monitoring script"

**Interview Question Prep:**
- What's the difference between `$()` and backticks?
- Explain `set -euo pipefail`
- How do you pass arguments to a bash function?

---

## Session 5: Git Fundamentals
**Duration:** 6-8 hours  
**Topics:**
- Git concepts: distributed version control
- Three-stage architecture: working directory → staging → repository
- Git config (user.name, user.email)
- Basic commands: init, add, commit, log, status
- Viewing changes: diff, show
- Undoing changes: restore, reset, revert

**Hands-on Lab:**
- Initialize a git repo from scratch
- Create files, stage, and commit
- View commit history
- Make changes and use diff
- Practice undo operations

**Deliverable:**
- Git repo with 10+ commits with meaningful messages
- Screenshot of `git log --oneline`
- Commit: "Session 5: Git fundamentals mastered"

---

## Session 6: Git Branching & GitHub Workflow
**Duration:** 6-8 hours  
**Topics:**
- Branches: create, switch, merge, delete
- Merge conflicts and resolution
- GitHub PR workflow
- Code review best practices
- Branch protection rules
- Tags and releases

**Hands-on Lab:**
- Create feature branches
- Make changes and create pull requests
- Review and merge PRs
- Resolve merge conflicts
- Set up branch protection on main

**Deliverable:**
- 5+ merged pull requests on your repo
- Screenshot of PR workflow
- Commit: "Session 6: Git branching and GitHub PR workflow"

---

## Session 7: Networking Fundamentals
**Duration:** 8-10 hours  
**Topics:**
- IP addressing: IPv4, IPv6, classes
- Subnetting and CIDR notation
- Network layers: OSI model, TCP/IP stack
- DNS: how domain names resolve to IPs
- Ports and protocols (HTTP, HTTPS, SSH)
- TCP vs UDP
- Firewalls and basic network troubleshooting

**Hands-on Lab:**
- Calculate subnets (10.0.0.0/24, 192.168.1.0/25, etc.)
- Use nslookup/dig for DNS queries
- Understand netstat output
- SSH key generation and usage
- Firewall basics with iptables (conceptual)

**Deliverable:**
- Subnetting exercise document (10 examples)
- Screenshot of SSH connection
- Commit: "Session 7: Networking fundamentals and subnetting"

**Interview Question Prep:**
- What's the difference between TCP and UDP?
- Explain CIDR notation
- How does DNS resolution work?
- What are the 7 layers of the OSI model?

---

## Session 8: Python for Automation I
**Duration:** 8-10 hours  
**Topics:**
- Python basics: variables, data types, operators
- Strings, lists, dictionaries, tuples
- Conditionals and loops
- Functions and error handling (try/except)
- File I/O: reading and writing files
- os module: working with filesystem
- pathlib: modern file path handling

**Hands-on Lab - Write 3 Scripts:**

**Script 1: File Operations**
```python
import os
from pathlib import Path

# Create files
for i in range(5):
    Path(f"test_{i}.txt").write_text(f"Content {i}")

# List files
for file in Path(".").glob("test_*.txt"):
    print(f"File: {file.name}, Size: {file.stat().st_size}")
```

**Script 2: Log Parser**
```python
def parse_log(filename):
    errors = []
    with open(filename, 'r') as f:
        for line in f:
            if "ERROR" in line:
                errors.append(line.strip())
    return errors

errors = parse_log("app.log")
for error in errors:
    print(error)
```

**Script 3: System Monitor (Python)**
```python
import os
import psutil

cpu = psutil.cpu_percent()
memory = psutil.virtual_memory().percent
disk = psutil.disk_usage('/').percent

print(f"CPU: {cpu}%")
print(f"Memory: {memory}%")
print(f"Disk: {disk}%")

if cpu > 80 or memory > 80:
    print("WARNING: High resource usage!")
```

**Deliverable:**
- 3 working Python scripts
- Commit: "Session 8: Python automation scripts"

---

## Session 9: Python for Automation II - APIs & CLI Tools
**Duration:** 8-10 hours  
**Topics:**
- pip and virtual environments (venv)
- Installing packages: requests, PyYAML
- HTTP requests: GET, POST
- JSON and YAML parsing
- Command-line arguments with argparse
- Scheduling Python jobs (schedule module)
- Building a reusable CLI tool

**Hands-on Lab - Build a CLI Tool:**

**Project: Log Analyzer & Report Generator**
```python
#!/usr/bin/env python3
import argparse
import json
from pathlib import Path
from datetime import datetime

def analyze_logs(logfile, keyword):
    """Find lines containing keyword in logfile"""
    results = []
    with open(logfile, 'r') as f:
        for line in f:
            if keyword.lower() in line.lower():
                results.append(line.strip())
    return results

def generate_report(results, output_file):
    """Generate JSON report"""
    report = {
        "timestamp": datetime.now().isoformat(),
        "total_matches": len(results),
        "results": results
    }
    with open(output_file, 'w') as f:
        json.dump(report, f, indent=2)
    print(f"Report saved to {output_file}")

if __name__ == "__main__":
    parser = argparse.ArgumentParser(description="Analyze logs and generate reports")
    parser.add_argument("logfile", help="Path to log file")
    parser.add_argument("--keyword", default="ERROR", help="Keyword to search")
    parser.add_argument("--output", default="report.json", help="Output file")
    
    args = parser.parse_args()
    
    results = analyze_logs(args.logfile, args.keyword)
    generate_report(results, args.output)
```

**Usage:**
```bash
python log_analyzer.py app.log --keyword ERROR --output error_report.json
```

**Deliverable:**
- Complete CLI tool with argparse
- Works with actual log files
- Generates JSON reports
- README explaining usage
- Commit: "Session 9: Python CLI tool for log analysis (project)"

**Interview Question Prep:**
- What's the difference between a library and a framework?
- How do you handle exceptions in Python?
- Explain list comprehensions
- What are virtual environments and why use them?

---

# 🚀 PHASE 2: CLOUD BASICS (Weeks 5-8)

## Session 10: AWS Global Infrastructure & EC2 Basics
**Duration:** 8-10 hours  
**Topics:**
- AWS regions, availability zones, edge locations
- AWS global infrastructure architecture
- Shared Responsibility Model
- EC2 overview: instances, AMIs, instance types
- Instance families: t2 (burstable), m5 (general), c5 (compute)
- Pricing: on-demand, reserved, spot
- Launching your first EC2 instance

**Hands-on Lab:**
- Create AWS account (should already have)
- Navigate AWS Console
- Launch t2.micro instance (free tier)
- Connect via SSH
- Terminate instance
- Understand billing

**Deliverable:**
- Screenshots of AWS Console
- Successful SSH connection to EC2
- Document: "Session 10: AWS EC2 and global infrastructure"
- Commit: "Session 10: AWS EC2 first instance launched"

**Interview Question Prep:**
- What's the difference between a region and an AZ?
- Explain the Shared Responsibility Model
- Why use t2.micro for learning?
- How is EC2 pricing calculated?

---

## Session 11: EC2 Security & Configuration
**Duration:** 8-10 hours  
**Topics:**
- Security Groups: inbound/outbound rules
- Network ACLs (stateful vs stateless)
- Key pairs: generation, management, best practices
- User data scripts (EC2 initialization)
- EC2 metadata service
- EBS volumes: types, snapshots, encryption
- Elastic IPs: static public IPs
- Hardening EC2 instances

**Hands-on Lab:**
- Create security group with SSH (22) and HTTP (80) access
- Launch EC2 with custom user data script:
```bash
#!/bin/bash
apt update && apt install -y nginx
systemctl start nginx
echo "Server: $(hostname)" > /var/www/html/index.html
```
- Access web server via browser
- Create and restore EBS snapshots
- Attach additional EBS volume

**Deliverable:**
- Working EC2 instance accessible via HTTP
- Screenshot of web server
- Commit: "Session 11: EC2 security and hardened configuration"

---

## Session 12: AWS IAM - Identity & Access Management
**Duration:** 8-10 hours  
**Topics:**
- IAM concepts: users, groups, roles, policies
- Least privilege principle
- Policy documents: JSON structure
- AWS managed vs customer managed policies
- Role assumption and trust relationships
- MFA (Multi-Factor Authentication)
- Programmatic access: access keys and secret keys
- IAM best practices

**Hands-on Lab:**
- Create IAM user for EC2 management
- Attach policies to user
- Create EC2-specific role with restricted permissions
- Set up MFA on root account
- Generate access keys
- Test programmatic access with AWS CLI

**Deliverable:**
- IAM user with S3 read-only access
- EC2 IAM role with CloudWatch access
- Screenshot of IAM policies
- Commit: "Session 12: IAM user and role management"

**Interview Question Prep:**
- What's the principle of least privilege?
- Difference between users and roles?
- Explain IAM policy structure
- Why shouldn't you use root account for daily work?

---

## Session 13: VPC & AWS Networking Deep Dive
**Duration:** 10-12 hours  
**Topics:**
- VPC (Virtual Private Cloud) architecture
- Subnets: public and private
- Route tables and routing
- Internet Gateway (IGW)
- NAT Gateway / NAT Instance
- VPC peering
- Security Groups vs Network ACLs
- VPC Flow Logs
- Bastion hosts / jump boxes

**Hands-on Lab - Build Custom VPC:**
- Create VPC with CIDR 10.0.0.0/16
- Create 2 public subnets (10.0.1.0/24, 10.0.2.0/24)
- Create 2 private subnets (10.0.10.0/24, 10.0.11.0/24)
- Attach Internet Gateway
- Create NAT Gateway for private subnets
- Launch EC2 in public subnet (accessible from internet)
- Launch EC2 in private subnet (accessible only via bastion)
- Create security group rules

**Deliverable:**
- Custom VPC with public/private subnets
- Architecture diagram (use draw.io)
- Screenshots showing subnet configuration
- Commit: "Session 13: Custom VPC with public-private subnet architecture"

**Interview Question Prep:**
- Explain public vs private subnets
- How does NAT Gateway work?
- Difference between IGW and NAT?
- What's a bastion host?
- Stateful vs stateless security controls?

---

## Session 14: AWS Storage & Databases
**Duration:** 10-12 hours  
**Topics:**
- S3: buckets, objects, storage classes
- S3 versioning, lifecycle policies
- S3 security: bucket policies, ACLs
- RDS: Relational Database Service
- RDS engines: MySQL, PostgreSQL, MariaDB
- Multi-AZ deployments
- Read replicas
- Backups and snapshots
- DynamoDB: NoSQL basics (optional for this phase)

**Hands-on Lab:**
- Create S3 bucket with unique name
- Upload files and manage versions
- Create bucket policy for public read access
- Launch RDS PostgreSQL instance
- Connect to RDS from EC2
- Create database and table
- Take manual snapshot
- Enable automated backups

**Database Setup Script:**
```bash
#!/bin/bash
# Run on EC2 instance with RDS endpoint

sudo apt install -y postgresql-client

psql -h <RDS_ENDPOINT> -U admin -d postgres -c "
CREATE DATABASE myapp;
\c myapp
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
"
```

**Deliverable:**
- S3 bucket with versioning enabled
- RDS instance with sample database
- Connection script from EC2 to RDS
- Commit: "Session 14: S3 and RDS database setup"

**Interview Question Prep:**
- What are S3 storage classes?
- Explain lifecycle policies
- Multi-AZ vs read replicas?
- How does RDS backup work?
- Security considerations for databases?

---

# 💾 PHASE 3: CONTAINERS & IaC (Weeks 9-10)

## Session 15: Docker I - Images & Containers
**Duration:** 8-10 hours  
**Topics:**
- Virtualization vs containerization
- Docker architecture: daemon, images, containers, registries
- Dockerfile: FROM, RUN, COPY, WORKDIR, CMD, ENTRYPOINT
- Image layers and caching
- Multi-stage builds for optimization
- Docker Hub and image repositories
- Image scanning and security

**Hands-on Lab - Containerize Python App:**

**Create Python App (app.py):**
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello from Docker! 🐳"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

**Create Dockerfile:**
```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

EXPOSE 5000

CMD ["python", "app.py"]
```

**Create requirements.txt:**
```
Flask==2.0.1
```

**Build and Run:**
```bash
docker build -t my-flask-app:1.0 .
docker run -p 5000:5000 my-flask-app:1.0
```

**Deliverable:**
- Working Flask Docker image
- Dockerfile with best practices
- Docker image uploaded to Docker Hub
- Screenshot of running container
- Commit: "Session 15: Flask app containerized with Docker"

---

## Session 16: Docker II - Networking & Compose
**Duration:** 8-10 hours  
**Topics:**
- Docker networking modes: bridge, host, overlay
- Port mapping and exposure
- Docker volumes: named volumes, bind mounts
- Data persistence
- Docker Compose: orchestrating multi-container apps
- Docker Compose YAML syntax
- Environment variables and .env files
- Container security best practices

**Hands-on Lab - Multi-container App with Docker Compose:**

**docker-compose.yml:**
```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5000:5000"
    environment:
      - FLASK_ENV=production
      - DB_HOST=db
    depends_on:
      - db
    volumes:
      - ./app:/app

  db:
    image: postgres:13
    environment:
      - POSTGRES_USER=admin
      - POSTGRES_PASSWORD=secret
      - POSTGRES_DB=myapp
    volumes:
      - db_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

volumes:
  db_data:
```

**Updated app.py (with database):**
```python
from flask import Flask
import psycopg2

app = Flask(__name__)

@app.route('/')
def hello():
    conn = psycopg2.connect(host="db", user="admin", password="secret", database="myapp")
    cur = conn.cursor()
    cur.execute("SELECT version();")
    db_version = cur.fetchone()
    cur.close()
    conn.close()
    return f"Hello from Docker! DB: {db_version[0]}"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

**Usage:**
```bash
docker-compose up -d
docker-compose logs -f
docker-compose down
```

**Deliverable:**
- Multi-container app (Flask + PostgreSQL)
- Docker Compose file with proper volumes
- Application running and accessible
- Screenshot showing both containers running
- Commit: "Session 16: Multi-container Flask-PostgreSQL with Docker Compose"

**Interview Question Prep:**
- What's the difference between COPY and ADD in Dockerfile?
- Explain CMD vs ENTRYPOINT
- Docker networking modes explained
- Why use Docker Compose?
- Container security best practices?

---

# 🏗️ PHASE 4: INFRASTRUCTURE AS CODE (Weeks 11-12)

## Session 17: Terraform Fundamentals
**Duration:** 10-12 hours  
**Topics:**
- Infrastructure as Code (IaC) principles
- Terraform basics: resources, providers, variables, outputs
- HCL (HashiCorp Configuration Language) syntax
- Terraform state file
- Providers: AWS provider configuration
- Variables: input variables, locals, data sources
- Outputs: exporting values

**Hands-on Lab - Provision AWS Infrastructure:**

**main.tf:**
```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.0"
    }
  }
}

provider "aws" {
  region = var.aws_region
}

resource "aws_vpc" "main" {
  cidr_block           = var.vpc_cidr
  enable_dns_hostnames = true

  tags = {
    Name = "main-vpc"
  }
}

resource "aws_subnet" "public" {
  vpc_id            = aws_vpc.main.id
  cidr_block        = var.subnet_cidr
  availability_zone = data.aws_availability_zones.available.names[0]

  tags = {
    Name = "public-subnet"
  }
}

resource "aws_instance" "web" {
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.public.id

  tags = {
    Name = "web-server"
  }
}
```

**variables.tf:**
```hcl
variable "aws_region" {
  description = "AWS region"
  default     = "us-east-1"
}

variable "vpc_cidr" {
  description = "VPC CIDR block"
  default     = "10.0.0.0/16"
}

variable "subnet_cidr" {
  description = "Subnet CIDR block"
  default     = "10.0.1.0/24"
}
```

**outputs.tf:**
```hcl
output "instance_id" {
  value = aws_instance.web.id
}

output "public_ip" {
  value = aws_instance.web.public_ip
}
```

**Workflow:**
```bash
terraform init      # Initialize working directory
terraform plan      # Preview changes
terraform apply     # Apply configuration
terraform destroy   # Clean up
```

**Deliverable:**
- Working Terraform configuration
- VPC + EC2 instance created via Terraform
- terraform.tfstate committed (with note on not committing in production)
- Commit: "Session 17: Terraform IaC for VPC and EC2"

---

## Session 18: Terraform Advanced & AWS Automation
**Duration:** 10-12 hours  
**Topics:**
- Modules: creating reusable infrastructure
- Workspaces: managing multiple environments
- Remote state backends: S3 + DynamoDB
- Terraform fmt, validate, plan
- Data sources: querying existing AWS resources
- Locals and complex variable structures
- Security: managing secrets and sensitive variables

**Hands-on Lab - Modular Terraform:**

**Directory structure:**
```
terraform/
├── main.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
└── modules/
    ├── vpc/
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    └── ec2/
        ├── main.tf
        ├── variables.tf
        └── outputs.tf
```

**modules/vpc/main.tf:**
```hcl
resource "aws_vpc" "main" {
  cidr_block = var.cidr_block
  tags = {
    Name = var.name
  }
}

resource "aws_subnet" "public" {
  vpc_id     = aws_vpc.main.id
  cidr_block = var.subnet_cidr
  tags = {
    Name = "${var.name}-public"
  }
}
```

**modules/vpc/variables.tf:**
```hcl
variable "name" {
  type = string
}

variable "cidr_block" {
  type = string
}

variable "subnet_cidr" {
  type = string
}
```

**modules/vpc/outputs.tf:**
```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}

output "subnet_id" {
  value = aws_subnet.public.id
}
```

**Main terraform/main.tf:**
```hcl
module "vpc" {
  source = "./modules/vpc"
  
  name       = "production"
  cidr_block = "10.0.0.0/16"
  subnet_cidr = "10.0.1.0/24"
}

module "ec2" {
  source = "./modules/ec2"
  
  instance_type = "t2.micro"
  subnet_id     = module.vpc.subnet_id
}
```

**Deliverable:**
- Modular Terraform code
- Multiple environments (dev, prod)
- Clean outputs and variables
- Documentation on module usage
- Commit: "Session 18: Modular Terraform with reusable components"

**Interview Question Prep:**
- What's the difference between modules and workspaces?
- How do you manage Terraform state securely?
- Explain data sources in Terraform
- What's the purpose of backend configuration?

---

# 🔄 PHASE 5: CI/CD & AUTOMATION (Weeks 13-14)

## Session 19: GitHub Actions - Continuous Integration
**Duration:** 8-10 hours  
**Topics:**
- CI/CD concepts and benefits
- GitHub Actions workflows, jobs, steps
- Runners: GitHub-hosted and self-hosted
- Workflow triggers: push, pull_request, schedule
- Jobs and conditional execution
- Artifacts and caching
- Secrets management

**Hands-on Lab - Build Docker Image on Push:**

**.github/workflows/docker-build.yml:**
```yaml
name: Docker Build & Push

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v2
      
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v1
      
      - name: Build Docker image
        uses: docker/build-push-action@v2
        with:
          context: .
          file: ./Dockerfile
          push: false
          tags: my-app:${{ github.sha }}
      
      - name: Test image
        run: |
          docker build -t test-image .
          docker run test-image python -m pytest
```

**Deliverable:**
- Working GitHub Actions workflow
- Automatic Docker build on push
- Build logs visible in GitHub
- Commit: "Session 19: GitHub Actions CI pipeline for Docker builds"

---

## Session 20: GitHub Actions - Continuous Deployment to AWS
**Duration:** 10-12 hours  
**Topics:**
- Deployment strategies: blue-green, rolling, canary
- AWS ECR (Elastic Container Registry)
- ECS (Elastic Container Service) task definitions
- Deploying containers to AWS
- Environment promotion (dev → staging → prod)
- Deployment notifications
- Rollback strategies

**Hands-on Lab - Deploy to AWS ECS:**

**.github/workflows/deploy.yml:**
```yaml
name: Deploy to ECS

on:
  push:
    branches: [main]

env:
  AWS_REGION: us-east-1
  ECR_REPOSITORY: my-app
  ECS_SERVICE: my-app-service
  ECS_CLUSTER: my-cluster
  CONTAINER_NAME: my-app

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v2
      
      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ${{ env.AWS_REGION }}
      
      - name: Login to ECR
        id: login-ecr
        uses: aws-actions/amazon-ecr-login@v1
      
      - name: Build, tag, and push to ECR
        env:
          ECR_REGISTRY: ${{ steps.login-ecr.outputs.registry }}
          IMAGE_TAG: ${{ github.sha }}
        run: |
          docker build -t $ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG .
          docker push $ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG
      
      - name: Deploy to ECS
        run: |
          aws ecs update-service \
            --cluster $ECS_CLUSTER \
            --service $ECS_SERVICE \
            --force-new-deployment
```

**Deliverable:**
- Full CI/CD pipeline: Git push → Build → Push to ECR → Deploy to ECS
- Application automatically deployed on code changes
- Working monitoring and logs
- Commit: "Session 20: Complete CI/CD pipeline to AWS ECS"

**Interview Question Prep:**
- Explain different deployment strategies
- What are GitHub Actions secrets?
- How does CI/CD reduce deployment time?
- Rollback strategy in ECS deployments?

---

# 🎯 PHASE 6: PORTFOLIO PROJECTS (Weeks 15-16)

## Session 21: Project 1 - Multi-tier Web Application
**Duration:** 16-20 hours  
**Project Overview:**
Build a complete 3-tier application deployed to AWS with full CI/CD

**Architecture:**
```
User (Browser)
   ↓
Load Balancer (ALB)
   ↓
Web Tier (EC2 with Docker - Flask)
   ↓
App Tier (Lambda Functions)
   ↓
Data Tier (RDS PostgreSQL)
```

**Tech Stack:**
- Frontend: Simple HTML/React
- Backend: Flask/FastAPI in Docker
- Database: PostgreSQL on RDS
- Infrastructure: Terraform
- CI/CD: GitHub Actions
- Monitoring: CloudWatch

**Requirements:**
1. Create a task management app (create, read, update, delete tasks)
2. Containerize backend with Docker
3. Deploy database on RDS
4. Set up load balancer
5. Create Terraform code for all infrastructure
6. Build GitHub Actions pipeline

**Deliverables:**
- GitHub repo with all code
- Live deployed application
- Architecture diagram
- Terraform code
- GitHub Actions workflow
- README with deployment instructions
- Screenshots of working app

**Interview-Ready Elements:**
- Explain architecture decisions
- How would you scale this?
- Handle database migrations
- Security considerations
- Cost optimization

**Commit:** "Project 1: Multi-tier Task Management App (Docker + Terraform + ECS + RDS)"

---

## Session 22: Project 2 - Cloud Infrastructure Monitoring
**Duration:** 12-16 hours  
**Project Overview:**
Build monitoring and alerting for multi-server infrastructure

**What You'll Build:**
- Multiple EC2 instances with Terraform
- CloudWatch dashboards
- Custom metrics and alarms
- SNS notifications
- Log aggregation
- Cost tracking dashboard

**Requirements:**
1. Provision 3 EC2 instances with Terraform
2. Install CloudWatch agent on each
3. Create custom metrics (CPU, memory, disk, custom app metrics)
4. Set up alarms for threshold breaches
5. Create dashboard showing all metrics
6. Log application events to CloudWatch
7. Set up SNS for notifications

**Sample Monitoring Script (on EC2):**
```bash
#!/bin/bash
while true; do
    CPU=$(top -bn1 | grep "Cpu(s)" | awk '{print $2}' | cut -d'%' -f1)
    MEM=$(free | grep Mem | awk '{printf("%.0f\n", $3/$2 * 100)}')
    DISK=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')
    
    aws cloudwatch put-metric-data \
        --metric-name CustomCPU \
        --value $CPU \
        --namespace MyApp/Performance
    
    if (( $(echo "$CPU > 80" | bc -l) )); then
        aws sns publish \
            --topic-arn arn:aws:sns:... \
            --message "CPU Usage High: $CPU%"
    fi
    
    sleep 60
done
```

**Deliverables:**
- Terraform code for monitored infrastructure
- CloudWatch dashboards
- Custom metrics collection script
- Alarm configuration
- SNS notifications working
- Detailed README
- Screenshots of dashboards and alerts

**Commit:** "Project 2: Multi-server monitoring with CloudWatch and SNS alerts"

---

# 📝 PHASE 7: INTERVIEW PREP & POLISH (Weeks 17-18)

## Session 21: Resume, LinkedIn & GitHub Optimization

**Resume Focus:**
- Quantify your projects: "Deployed multi-tier web app serving 100+ requests/sec using Docker, Terraform, and GitHub Actions"
- Use action verbs: Implemented, Architected, Automated, Deployed
- Show impact: Cost savings, performance improvements, automation benefits

**Sample Resume Points:**
```
PROJECTS

Multi-tier Web Application (Docker, Terraform, AWS ECS)
- Designed and deployed 3-tier architecture on AWS using Terraform
- Containerized Flask backend with Docker, automated deployment via GitHub Actions
- Reduced deployment time from 30 min to 2 min with CI/CD pipeline
- Managed PostgreSQL RDS database with automated backups

Infrastructure Monitoring System (CloudWatch, SNS)
- Built real-time monitoring dashboard for multi-server infrastructure
- Created custom CloudWatch metrics and alarms for CPU, memory, disk usage
- Automated alerts via SNS reducing incident response time by 40%
- Implemented log aggregation for 3 servers using CloudWatch Logs
```

**LinkedIn Optimization:**
- Headline: "DevOps Engineer | AWS | Docker | Terraform | CI/CD (Learning)"
- Summary: "Passionate about cloud infrastructure and automation..."
- Add project links
- Share weekly learning posts

**GitHub Polish:**
- Ensure all repos have proper READMEs
- Add architecture diagrams (draw.io, Lucidchart)
- Include deployment instructions
- Add badges (build status, license, etc.)
- Pin 2-3 best projects

---

## Session 22: Interview Preparation & Mock Interviews

**System Design Questions:**
- Design a scalable web application
- Design a monitoring system
- Design a CI/CD pipeline
- Design an auto-scaling infrastructure

**AWS Questions:**
- Explain your multi-tier architecture
- How would you ensure high availability?
- Cost optimization strategies
- Security best practices
- Disaster recovery planning

**DevOps Questions:**
- CI/CD pipeline walkthrough
- Docker and containerization benefits
- Infrastructure as Code advantages
- Monitoring and alerting strategy
- Deployment strategies

**Coding Questions:**
- Fix a failing deployment
- Debug a slow application
- Optimize infrastructure costs
- Write a monitoring script

**Mock Interview Preparation:**
- Record yourself answering questions
- Do 5-10 mock interviews
- Review with mentor/peers
- Practice explaining technical decisions

---

# 📊 Summary Timeline

| Week | Phase | Sessions | Projects |
|------|-------|----------|----------|
| 1-4 | Foundations | 1-9 | Bash scripts, Python CLI |
| 5-8 | Cloud Basics | 10-14 | AWS EC2, VPC, RDS |
| 9-10 | Containers & IaC | 15-18 | Docker, Terraform |
| 11-12 | CI/CD | 19-20 | GitHub Actions pipeline |
| 13-14 | Projects | 21-22 | 2 portfolio projects |
| 15-16 | Interview Prep | 23 | Polish, mock interviews |

---

# 🎯 Success Metrics by End of Course

✅ 3+ GitHub repositories with real projects  
✅ Live deployed applications  
✅ 50+ AWS hands-on labs completed  
✅ Terraform code managing production-grade infrastructure  
✅ Full CI/CD pipeline from commit to deployment  
✅ Resume optimized with quantified achievements  
✅ LinkedIn profile complete and active  
✅ Mock interviews passed  
✅ Applied to 10+ internship positions  
✅ **Goal: 50k+ stipend DevOps/Cloud internship offer** 🚀
