# GITHUB PROFESSIONAL

This repository documents my hands-on learnig journey whit **GitHub Actions**, form the fundamenltal of Git and GitHub collaboration to advanced CI/CD pipelines, reusable workflows, Infrasctructure as Code (IaC), AWS deployments, custom Actions and self-hosted runners. 

The main goal of this repository is to pratice real world automation patterns and build a solid foundations for **Devops, Cloud Engineering, Plataform Engineering and CI/CD.** 

- - - 
  
### Module 1 - Getting Started with GitHub and GitHub Actions 

- Git Version control and collaboration with GitHub
- Introduction to GitHub Actions 
- GitHub account and repository setup
- Creating the first GitHub workflow
- Understanding workflow
- Understanding jobs
- Understanding steps
- Introduction to Actions
- Hands-on Workflow challenge
- Module review

- - -

### Module 2 — Improving Git Workflows and Collaboration

- Solving the first workflow challenge
- Understanding Git Flow
- Organizing repository workflows
- Pull Requests
- Pull Request best practices
- Branch Protection Rules
- Repository protection strategies
- CODEOWNERS
- Improving team collaboration

---

### Module 3 — GitHub Actions Triggers

Working with different events that can trigger workflows.

#### Repository Events

- `branch_protection_rule`
- `create`
- `delete`

#### Deployment and Collaboration Events

- `deployment`
- `discussion`
- `gollum`

#### Development Events

- `issues`
- `pull_request`
- `push`

#### Automation Events

- `schedule`
- `status`
- `workflow_dispatch`

#### Workflow Composition

- `workflow_call`
- `workflow_run`
- Reusable workflows
- Practical automation challenge

---

### Module 4 — Contexts, Security, Scripts, and GitHub Packages

#### GitHub Actions Security

- GitHub Actions security fundamentals
- Workflow security best practices
- Understanding permissions
- Protecting secrets and credentials

#### GitHub Actions Contexts

Working with contexts such as:

- `github`
- `vars`
- `secrets`
- `env`

#### Workflow Scripts

- Running shell scripts inside workflows
- Moving complex logic outside YAML files
- Organizing automation logic

#### GitHub Packages

- GitHub Packages
- GitHub Container Registry
- Publishing packages
- Publishing Docker images
- Practical module challenge

---

### Module 5 — Flow Control, Dependencies, and Debugging

- Understanding job and step identifiers
- Working with `needs`
- Job dependencies
- Conditional execution
- Building complete CI pipelines
- Lint stages
- Test stages
- Build stages
- Composite Actions
- Custom Actions
- GitHub Actions logs
- Workflow debugging
- Troubleshooting failed pipelines

--- 

# Building Custom GitHub Actions

This section focuses on creating and publishing custom Actions.

Topics include:

- Designing the architecture of a GitHub Action
- Working with GitHub Issues
- Working with GitHub Projects
- Linking Issues and Projects
- Exploring the GitHub Actions Marketplace
- Creating an `action.yml`
- Structuring custom Action functions
- Building custom Action components
- Preparing an Action for distribution
- Publishing an Action to the GitHub Marketplace

---

## Automated Testing with GitHub Actions

Integration of automated testing into CI pipelines.

Topics covered:

- GitHub Codespaces
- Automated tests
- Branch protection based on test results
- Tests with multiple programming languages
- Python tests
- Go tests
- Matrix strategies
- Testing multiple environments and versions

Example matrix:

```yaml
strategy:
  matrix:
    version: ["1.0", "2.0", "3.0"]
```  

# Workflow Cache and Optimization

Improving workflow performance using caching.

Topics include:

- Understanding GitHub Actions Cache
- Dependency caching
- Improving workflow execution time
- Reusing cached dependencies
-  Cache strategies
- Workflow optimization
- Adding status badges for builds and tests

Example:

```
- name: Cache dependencies
  uses: actions/cache@v4
  with:
    path: ~/.cache
    key: ${{ runner.os }}-${{ hashFiles('**/lockfiles') }} 
``` 

# Infrastructure as Code with Terraform

Using GitHub Actions to automate infrastructure management.

The repository explores CI/CD workflows for Terraform, including:

- Infrastructure as Code concepts
- Terraform automation
- Infrastructure for Amazon EC2
- Infrastructure for Amazon EKS
- Reusable Terraform workflows
- Terraform validation
- Terraform Plan
- Terraform Apply
- Terraform Destroy
- Improving Terraform workflow reusability

Example pipeline structure:

```
 Pull Request
    │
    ▼
Terraform Validate
    │
    ▼
Terraform Plan
    │
    ▼
Code Review
    │
    ▼
Terraform Apply 
``` 
# AWS CI/CD Pipelines

Building CI/CD pipelines targeting AWS services.

AWS services explored include:

- Amazon EC2
- Amazon ECS
- Amazon EKS
- Amazon ECR  


# Continuous Integration Pipeline

Example CI pipeline architecture:

```
Developer
    │
    ▼
Git Push / Pull Request
    │
    ▼
GitHub Actions
    │
    ├── Lint
    │
    ├── Tests
    │
    ├── Build
    │
    ├── Security Scan
    │
    └── Container Build
            │
            ▼
        Amazon ECR
```
Topics include:

- Application builds
- Automated testing
- Docker image builds
- Vulnerability scanning
- Container image scanning
- Publishing images to Amazon ECR
- CI pipeline automation 

# Continuous Deployment

Building reusable deployment pipelines for different AWS environments.

Amazon EC2:
```
GitHub Actions
      │
      ▼
Build Application
      │
      ▼
Create Artifact / Container
      │
      ▼
Deploy
      │
      ▼
Amazon EC2 
```  

# Amazon ECS
```
GitHub Actions
      │
      ▼
Docker Build
      │
      ▼
Amazon ECR
      │
      ▼
Amazon ECS
Amazon EKS
GitHub Actions
      │
      ▼
Build & Test
      │
      ▼
Docker Image
      │
      ▼
Amazon ECR
      │
      ▼
GitOps Repository
      │
      ▼
Argo CD
      │
      ▼
```
# Amazon EKS

Topics include:

- EC2 deployment pipelines
- ECS deployment pipelines
- EKS deployment pipelines
- Argo CD
- GitOps concepts
- Reusable deployment workflows
- AWS authentication
- OpenID Connect (OIDC)
- Reducing the use of long-lived AWS credentials
♻️# Reusable Workflows

Creating reusable CI/CD components using:

``` 
on:
  workflow_call:
``` 

The goal is to avoid duplicated workflow code and create reusable automation building blocks.

Examples include:

- Reusable CI pipelines
- Reusable Terraform workflows
- Reusable deployment pipelines
- Centralized workflow configuration 

# GitHub OIDC with AWS

Using OpenID Connect (OIDC) to authenticate GitHub Actions with AWS without storing long-lived AWS credentials.

Architecture:

```
GitHub Actions
      │
      │ OIDC Token
      ▼
AWS IAM
      │
      ▼
Assume Role
      │
      ├── Amazon ECR
      ├── Amazon EC2
      ├── Amazon ECS
      └── Amazon EKS
```
# GitHub Runners

Understanding how GitHub Actions runners execute workflows.

Topics include:

- GitHub-hosted runners
- Self-hosted runners
- Runner configuration
- Running workflows on custom infrastructure
- Self-hosted runners inside Kubernetes
- Runner security
- Runner isolation

Example architecture:

```
GitHub
   │
   ▼
GitHub Actions
   │
   ▼
Self-Hosted Runner
   │
   ▼
Kubernetes Cluster 
```
# GitHub Organizations

Exploring GitHub features for teams and organizations.

Topics include:

- GitHub Organizations
- Repository permissions
- Organization-level workflows
- Shared Actions
- Shared runners
- Centralized CI/CD
- Team collaboration 

# Composite Actions

Creating reusable groups of steps using Composite Actions.

Example structure:

``` 
.github/
└── actions/
    └── custom-action/
        └── action.yml 

``` 
Example:

``` 
name: "Custom Composite Action"

runs:
  using: "composite"
  steps:
    - name: First Step
      shell: bash
      run: echo "Running custom action" 
```
# JavaScript Actions

Creating GitHub Actions using JavaScript.

Topics include:

- Action metadata
- JavaScript-based Actions
- Inputs
- Outputs
- GitHub Actions Toolkit
- Packaging Actions
- Publishing Actions

Example structure:

```
custom-action/
├── action.yml
├── package.json
├── src/
│   └── index.js
└── dist/
    └── index.js
``` 

# Security Topics

Security is an important part of every CI/CD pipeline.

Topics explored throughout the project include:

- GitHub Secrets
- Environment variables
- Repository permissions
- Workflow permissions
- Dependency security
- Container vulnerability scanning
- Branch Protection Rules
- CODEOWNERS
- Secure AWS authentication
- OIDC
- Least privilege
- Secure self-hosted runners 

# Technologies

This learning repository includes hands-on experience with:

- Git
- GitHub
- GitHub Actions
- YAML
- Bash
- Docker
- GitHub Container Registry
- GitHub Packages
- Terraform
- AWS
- Amazon EC2
- Amazon ECS
- Amazon EKS
- Amazon ECR
- Kubernetes
- Argo CD
- Python
- Go
- JavaScript
- Linux  

#  Skills Developed

By working through this repository, I am developing practical experience with:

- Continuous Integration
- Continuous Delivery
- Continuous Deployment
- Infrastructure as Code
- GitOps
- Workflow automation
- CI/CD architecture
- Cloud deployments
- Container pipelines
- Automated testing
- Security scanning
- Reusable pipelines
- GitHub repository governance
- Infrastructure automation
- DevOps best practices 


# Repository Structure

A possible structure for the repository is:

```
.
├── .github/
│   ├── actions/
│   │   └── custom-actions/
│   │
│   └── workflows/
│       ├── ci.yml
│       ├── tests.yml
│       ├── terraform-plan.yml
│       ├── terraform-apply.yml
│       ├── terraform-destroy.yml
│       ├── deploy-ec2.yml
│       ├── deploy-ecs.yml
│       └── deploy-eks.yml
│
├── terraform/
│   ├── ec2/
│   └── eks/
│
├── scripts/
├── examples/
├── Dockerfile
└── README.md 
``` 


# Learning Progress
-  Git and GitHub fundamentals
-  First GitHub Actions workflow
-  Jobs and Steps
-  Git Flow
-  Pull Requests
-  Branch Protection Rules
-  CODEOWNERS
-  Workflow triggers
-  GitHub Actions contexts
-  Secrets and environment variables
-  GitHub Actions security
-  GitHub Packages
-  GitHub Container Registry
-  Conditionals and dependencies
-  Logs and debugging
-  Composite Actions
-  Custom GitHub Actions
-  GitHub Actions Marketplace
-  Automated testing
-  Matrix builds
-  Workflow caching
-  Build badges
-  Terraform automation
-  Terraform Plan
-  Terraform Apply
-  Terraform Destroy
-  Docker CI pipeline
-  Vulnerability scanning
-  Amazon ECR integration
-  Amazon EC2 deployment
-  Amazon ECS deployment
-  Amazon EKS deployment
-  Reusable workflows
-  AWS OIDC authentication
-  Argo CD
-  GitOps
-  GitHub Organizations
-  Self-hosted runners
-  Kubernetes runners
-  JavaScript Actions 

# Status

This repository is continuously evolving as I progress through the course and build new CI/CD experiments.

The goal is not only to learn GitHub Actions syntax, but to understand how to design ***secure, reusable, scalable, and production-oriented automation pipelines.***

👨‍💻 Author

***Cesar Santos***

Information Systems graduate focused on:

-Cloud Engineering
-DevOps
-Platform Engineering
-Kubernetes
-Infrastructure as Code
-CI/CD
-Linux
-AWS
