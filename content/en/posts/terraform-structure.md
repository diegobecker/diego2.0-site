+++
title = 'Infrastructure as Code with Terraform: How I Organized My Project'
date = 2025-06-16T15:11:51-03:00
draft = false
translationKey = "terraform"
+++

---

In the first post, I shared an overview of how I launched my personal site using AWS, HTTPS, and automated deploys. Now let’s dive into the details: how I organized everything using **Terraform**, applying best practices for structure, reuse, and state management.

---

## 📁 Project Structure

I split the code into two separate repositories:

- `diego2.0-infra`: infrastructure written in Terraform  
- `diego2.0-site`: site source code (built with Hugo)

In the infrastructure repository, I adopted a reusable modules structure:

```
diego2.0-infra/
├── main.tf
├── variables.tf
├── terraform.tfvars
├── modules/
│   ├── s3/
│   ├── route53/
│   ├── acm/
│   ├── cloudfront/
│   └── dns_records/

```

Each folder inside `modules/` represents an AWS service, with isolated and reusable code.

---

## 🚧 Remote Backend with S3 + DynamoDB

To keep the Terraform state remote and avoid conflicts in team settings (or across environments), I configured the backend with:

- An S3 bucket to store the `terraform.tfstate`
- A DynamoDB table to manage locking

Here’s the configuration block:

```hcl
terraform {
  backend "s3" {
    bucket         = "diego2.0-tfstate"
    key            = "global/terraform.tfstate"
    region         = "sa-east-1"
    dynamodb_table = "diego2.0-terraform-locks"
    encrypt        = true
  }
}
```

This block should be added to your `main.tf` after creating the bucket and table using Terraform.

---

## 🏋️ Applied Best Practices

- Modularization: each AWS resource has its own module

- Separate variables and values (`variables.tf` + `terraform.tfvars`)

- Use of outputs to connect modules

- Consistent naming across resources and files

- Remote and versioned state, ensuring traceability and safety

---

## 🚀 Next Step

With the Terraform foundation in place, we move to the next step: Creating the S3 bucket to host the static site and preparing the deploy.

If you've never created a static website with S3, you'll see how simple and powerful it can be. See you there!