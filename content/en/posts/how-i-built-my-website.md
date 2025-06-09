+++
title = 'How I Built My Website'
date = 2025-06-08T17:58:17-03:00
draft = false
translationKey = "my-site"
+++

# How I Built My Website with a Custom Domain, HTTPS, and Infrastructure on AWS (Using Terraform)

Having a professional personal website with a custom domain and HTTPS might sound complex — but with the right tools, it’s totally achievable. In this first post, I’ll share an overview of the architecture I used to get my site online using **AWS**, **Terraform**, and **GitHub Actions**.

This series is aimed at people who are starting in tech or want to transition into cloud and learn infrastructure as code in practice.

---

## ✅ What the Site Includes

* Hosting on an **S3 bucket** configured for static website hosting
* **Automatic deploys** via GitHub Actions every time I push to the repo
* **Custom domain** managed with Route 53
* **HTTPS enabled**, with a valid SSL certificate from AWS (ACM)
* Fast and secure delivery through **CloudFront (CDN)**
* 100% of the infrastructure created and managed with **modularized Terraform**

---

## 📚 This Post Series

Esse é o primeiro post de uma série onde vou explicar **cada parte dessa arquitetura em detalhes**, com tutoriais práticos e código comentado. Aqui está a ordem planejada:

This is the first post in a series where I’ll explain **each part of this architecture in detail**, with practical tutorials and commented code. Here’s the planned structure:

1. **Terraform in practice**: how I organized modules, used remote state, and applied good practices
2. **Creating the S3 bucket to host your static website**
3. **Automating deploys with GitHub Actions** (Hugo build + S3 sync)
4. **Managing your domain and DNS with Route 53**
5. **Creating SSL certificates with ACM** (DNS validation)
6. **Distributing the site with CloudFront (CDN + HTTPS)**
7. **Configuring DNS records to point to CloudFront**

---

## 💡 Tech Stack Used

* **AWS**: S3, Route 53, ACM, CloudFront  
* **Terraform**: Infrastructure as code  
* **GitHub Actions**: CI/CD for site deployment  
* **Hugo**: Static site generator

---

## 💼 Result

With this stack and automation, I can maintain a professional, secure site with automatic deploys and fully controlled infrastructure. All of that with **low cost and high quality**.

If you want to learn how to do this too, stay tuned for the upcoming posts.

See you in the next chapter: **Terraform in Practice to Structure Your Infrastructure!**