+++
title = 'Infraestrutura como Código com Terraform: como organizei meu projeto'
date = 2025-06-16T13:59:33-03:00
draft = false
translationKey = "terraform"
+++

No primeiro post, eu mostrei uma visão geral de como coloquei meu site no ar usando AWS, HTTPS e deploy automatizado. Agora vamos entrar nos detalhes: como organizei tudo com **Terraform**, aplicando boas práticas de estrutura, reuso e controle de estado.

---

## 📁 Estrutura do projeto

Eu dividi o código em dois repositórios:

- `diego2.0-infra`: infraestrutura em Terraform

- `diego2.0-site`: código do site (Hugo)

No repositório de infraestrutura, adotei uma estrutura de módulos reutilizáveis:

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

Cada pasta em `modules/` representa um serviço da AWS, com código isolado e reutilizável.

---

## 🚧 Backend remoto com S3 + DynamoDB

Para manter o state remoto e evitar conflitos em time (ou entre ambientes), configurei o backend com:

- Bucket S3 para armazenar o `terraform.tfstate`

- Tabela DynamoDB para controle de locking

Exemplo do bloco:

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

Esse trecho deve ser incluído no `main.tf` após criar o bucket e a tabela via Terraform.

---

## 🏋️ Boas práticas aplicadas

- Modularização: cada recurso da AWS tem seu próprio módulo

- Separar variáveis e valores (`variables.tf` + `terraform.tfvars`)

- Uso de outputs para conectar módulos

- Nomenclatura consistente entre os recursos e arquivos

- State remoto e versionado, garantindo segurança e rastreabilidade

---

## 🚀 Próximo passo

Com a base do Terraform pronta, seguimos para a próxima etapa: Criar o bucket S3 para hospedar o site estático e preparar o deploy.

Se você nunca criou um site com S3, vai ver como é simples e poderoso. Até lá!




