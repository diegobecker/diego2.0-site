+++
title = 'Como coloquei meu site no ar com domínio próprio, HTTPS e infraestrutura na AWS (com Terraform)'
date = 2025-06-08T17:58:17-03:00
draft = false
translationKey = "my-site"
+++

Ter um site pessoal profissional, com seu próprio domínio e HTTPS, pode parecer complicado — mas com as ferramentas certas, é totalmente viável. Neste primeiro post, vou mostrar uma visão geral da arquitetura que usei para colocar meu site no ar usando **AWS**, **Terraform** e **GitHub Actions**.

Essa série é voltada para quem está começando na área de tecnologia ou quer migrar para a nuvem e aprender infraestrutura como código na prática.

---

## ✅ O que o site tem

* Hospedagem em **bucket S3** configurado como site estático  
* **Deploy automático** via GitHub Actions sempre que atualizo o repositório  
* **Domínio próprio** configurado com o Route 53  
* **HTTPS ativado**, com certificado válido da AWS (ACM)  
* Entrega rápida e segura através do **CloudFront (CDN)**  
* Infraestrutura 100% criada e gerenciada com **Terraform modularizado**  

---

## 🏛 Arquitetura Geral

![Diagrama de arquitetura](/images/arquitetura-site.png)

---

## 📚 Essa série de posts

Esse é o primeiro post de uma série onde vou explicar **cada parte dessa arquitetura em detalhes**, com tutoriais práticos e código comentado. Aqui está a ordem planejada:

1. **Terraform na prática**: como organizei os módulos, usei state remoto e boas práticas  
2. **Criando o bucket S3 para hospedar seu site estático**  
3. **Automatizando o deploy com GitHub Actions** (build do Hugo + sync no S3)  
4. **Gerenciando domínio e DNS com Route 53**  
5. **Criando certificados SSL com ACM** (validação via DNS)  
6. **Distribuindo o site com CloudFront (CDN + HTTPS)**  
7. **Configurando registros DNS para apontar para o CloudFront**

---

## 💡 Tecnologias usadas

* **AWS**: S3, Route 53, ACM, CloudFront  
* **Terraform**: Infraestrutura como código  
* **GitHub Actions**: CI/CD para o deploy do site  
* **Hugo**: Gerador de site estático

## 💼 Resultado

Com essa stack e automação, consigo manter um site profissional, seguro, com deploy automático e infraestrutura sob controle. Tudo isso com **baixo custo e alta qualidade**.

Se você quer aprender como fazer isso também, acompanhe os próximos posts.

Nos vemos no próximo capítulo: **Terraform na prática para organizar sua infraestrutura!**
