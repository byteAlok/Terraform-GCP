# 🚀 Terraform with Google Cloud Platform (GCP)

![Terraform](https://img.shields.io/badge/Terraform-IaC-844FBA?logo=terraform&logoColor=white)
![GCP](https://img.shields.io/badge/Google_Cloud-GCP-4285F4?logo=googlecloud&logoColor=white)
![HCL](https://img.shields.io/badge/Language-HCL-blue)
![Status](https://img.shields.io/badge/Learning-In_Progress-blue)

A hands-on learning repository dedicated to **Terraform and Infrastructure as Code (IaC) on Google Cloud Platform (GCP)**. This repository contains configuration files, essential commands, learning notes, and practical examples for provisioning and managing Google Cloud infrastructure using Terraform.

## 📌 About This Repository

The goal of this repository is to understand how Terraform automates cloud infrastructure using declarative configuration files written in HashiCorp Configuration Language (HCL).

Topics, code examples, and practical exercises will be added progressively as I learn and practice Terraform with GCP.

## 🎯 Learning Objectives

- 🚀 Understand Infrastructure as Code (IaC).
- 🧩 Learn HCL syntax and Terraform configuration.
- ⚙️ Work with providers, resources, and data sources.
- 🔄 Understand the Terraform workflow: Init, Plan, Apply, and Destroy.
- ☁️ Provision and manage GCP resources using Terraform.
- 🔐 Configure Google Cloud authentication securely.
- 📦 Understand Terraform state and reusable modules.
- 🛠️ Automate cloud infrastructure through hands-on exercises.

## 🧰 Tech Stack

| Technology | Purpose |
|---|---|
| Terraform | Infrastructure provisioning and automation |
| Google Cloud Platform | Cloud infrastructure provider |
| HCL | Terraform configuration language |
| Google Cloud CLI (`gcloud`) | Google Cloud command-line interaction |
| Git & GitHub | Version control and documentation |
| Visual Studio Code | Code editor |

## 📚 Topics Covered

### 1. Terraform Fundamentals

- Introduction to Terraform and IaC
- Terraform architecture and workflow
- Installation and configuration
- HCL syntax and configuration blocks
- Providers, resources, and data sources
- Input variables and output values
- Local values and expressions
- Resource dependencies

### 2. Essential Terraform Commands

- `terraform -version` — Check the installed version
- `terraform init` — Initialize the working directory
- `terraform fmt` — Format configuration files
- `terraform validate` — Validate configuration syntax
- `terraform plan` — Preview infrastructure changes
- `terraform apply` — Apply configuration changes
- `terraform destroy` — Destroy managed resources
- `terraform state list` — List resources tracked in state

### 3. Terraform with GCP

- Configure the Google Cloud provider
- Authenticate using Application Default Credentials (ADC)
- Configure Google Cloud projects and regions
- Enable required Google Cloud APIs
- Create and manage cloud resources
- Understand projects, regions, and zones
- Reference existing resources
- Use variables and outputs for reusable configurations

### 4. GCP Infrastructure Practice

Practical exercises may include:

- 🖥️ Compute Engine — Virtual machines
- 🪣 Cloud Storage — Object storage buckets
- 🌐 Virtual Private Cloud (VPC) — Cloud networking
- 🔒 Firewall Rules — Network traffic control
- 🔑 IAM — Identity and access management
- ⚖️ Cloud Load Balancing — Traffic distribution
- 📊 Cloud Monitoring — Infrastructure monitoring

*These are planned learning areas. Resources will be added as the exercises are completed.*

### 5. State Management & Reusability

- Terraform state fundamentals
- Local and remote state management
- Google Cloud Storage (GCS) backend
- State locking and concurrent operations
- Input variables and output values
- Reusable Terraform modules
- Environment-specific configurations

## 📂 Repository Structure

```text
Terraform-GCP/
│
├── README.md
├── basics/
│   ├── provider.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── project/
│   └── main.tf
│
├── compute-engine/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── cloud-storage/
│   └── main.tf
│
├── vpc/
│   └── main.tf
│
└── modules/
```

*This is a suggested structure. Directories and files will be created as the repository grows.*

## ⚙️ Getting Started

### Prerequisites

Install the following tools:

- [Terraform CLI](https://developer.hashicorp.com/terraform/install)
- [Google Cloud CLI](https://cloud.google.com/sdk/docs/install)
- [Google Cloud Console](https://console.cloud.google.com/)
- [Visual Studio Code](https://code.visualstudio.com/)

### Step 1: Authenticate with Google Cloud

Sign in through the Google Cloud CLI:

```bash
gcloud auth login
```

Set the active project:

```bash
gcloud config set project YOUR_PROJECT_ID
```

Configure Application Default Credentials for Terraform:

```bash
gcloud auth application-default login
```

Verify the active configuration:

```bash
gcloud config list
```

Ensure billing is enabled where required and that your identity has the appropriate permissions.

### Step 2: Create a Terraform Configuration

Create a file named `main.tf`:

```hcl
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "~> 7.0"
    }
  }
}

provider "google" {
  project = "YOUR_PROJECT_ID"
  region  = "asia-south1"
}

resource "google_storage_bucket" "example" {
  name                        = "YOUR_GLOBALLY_UNIQUE_BUCKET_NAME"
  location                    = "ASIA-SOUTH1"
  uniform_bucket_level_access = true
}
```

This example configures the Google provider and defines a Cloud Storage bucket. Replace the project ID and bucket name with your own values. Bucket names must be globally unique.

### Step 3: Initialize Terraform

```bash
terraform init
```

### Step 4: Format and Validate

```bash
terraform fmt
terraform validate
```

### Step 5: Preview and Apply Changes

```bash
terraform plan
terraform apply
```

Review the proposed changes before confirming. Ensure the correct project is selected and the required APIs and permissions are available.

### Step 6: Clean Up Resources

When you no longer need the resources created by this configuration:

```bash
terraform destroy
```

Review the destruction plan carefully before confirming.

## 🔐 Security Best Practices

- Never commit service account private keys, access tokens, or credentials.
- Prefer Application Default Credentials, attached service accounts, or workload identity federation as appropriate.
- Follow the principle of least privilege for IAM permissions.
- Never commit Terraform state files or sensitive saved plan files.
- Add sensitive local files and Terraform-generated directories to `.gitignore`.
- Protect remote state storage with appropriate access controls.
- Review every plan before applying or destroying infrastructure.
- Monitor cloud resource usage and remove unused resources to avoid unnecessary charges.

## 🗓️ Learning Progress

- [x] Create the Terraform-GCP repository
- [ ] Terraform installation and setup
- [ ] HCL fundamentals
- [ ] Essential Terraform commands
- [ ] Google Cloud CLI authentication
- [ ] Google provider configuration
- [ ] Project and API configuration
- [ ] Compute Engine provisioning
- [ ] Cloud Storage buckets
- [ ] VPC and firewall rules
- [ ] Variables and outputs
- [ ] Remote state management
- [ ] Reusable Terraform modules
- [ ] Advanced Terraform practices

*Progress will be updated as each topic is completed.*

## 🌐 Related Repositories

- ☁️ **Terraform-AWS** — Terraform with Amazon Web Services
- 🔷 **Terraform-Azure** — Terraform with Microsoft Azure
- 🌎 **Terraform-GCP** — Terraform with Google Cloud Platform

Each repository focuses on its respective cloud provider, including provider-specific configurations, infrastructure examples, and learning notes.

## 👨‍💻 Author

**Alok Maurya**  
Full Stack Engineer | Cloud & DevOps Learner

- GitHub: [@byteAlok](https://github.com/byteAlok)

---

⭐ If you find this repository useful, consider giving it a star.

**Learning by building. Automating Google Cloud infrastructure with Terraform.**
