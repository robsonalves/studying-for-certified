# AWS Certified Cloud Practitioner - Estudo Completo

Este documento reúne todos os tópicos estudados para a certificação AWS Certified Cloud Practitioner, com foco acadêmico e explicações visuais extraídas de slides.

---

## 1. Introdução aos Bancos de Dados Gerenciados na AWS

### Amazon RDS

- Serviço relacional totalmente gerenciado.
- Suporta: **MySQL, PostgreSQL, SQL Server, MariaDB, Oracle**.
- Recursos:
  - Backup automatizado, patching e escalabilidade.
  - **Multi-AZ Deployment** para alta disponibilidade.
  - Repositórios de leitura para leitura escalável.
- Modos de implantação:
  - Single-AZ: uma instância.
  - Multi-AZ (2 instâncias): standby.
  - Multi-AZ cluster (3 instâncias): leitura escalável.

### Amazon DynamoDB

- Serviço NoSQL totalmente gerenciado.
- Modelos de dados: chave-valor e documento.
- Recursos:
  - Escalabilidade automática.
  - Alta disponibilidade embutida.
  - Suporte a milissegundos de latência.
  - Replicação entre regiões.
- Casos de uso:
  - Sessão de usuários, IoT, jogos, sistemas de recomendação.

---

## 2. Alta Disponibilidade no RDS

- Conversão de instância RDS para **Multi-AZ** via console.
- Redundância entre zonas de disponibilidade (AZs).
- Separação entre **instância primária** e **réplicas de leitura**.

---

## 3. AWS CloudFormation

- Permite **IaC (Infrastructure as Code)**.
- Benefícios:
  - Automatiza o provisionamento de infraestrutura.
  - Usa **templates YAML/JSON** para definir recursos.
  - Implantação repetível e auditável.
  - Reduz erros humanos.

---

## 4. AWS Outposts

- Solução híbrida da AWS.
- Extende infraestrutura AWS para ambientes **on-premises**.
- Casos de uso:
  - Baixa latência.
  - Processamento local de dados.
  - Integração com serviços AWS nativos.

---

## 5. Tópicos-Chave para Foco

1. **Serviços de computação**: EC2, EKS, ECS, Lambda.
2. **Modelos de preços**: On-demand, Reserved, Spot, Savings Plans.
3. **Containerização** na AWS.
4. **Serverless e modelo pay-as-you-go**.

---

## 6. Armazenamento em EC2

### Amazon EBS (Elastic Block Store)

- **Altamente disponível** e durável.
- **Escalável** sem downtime.
- **Snapshots** para backups e clonagem.
- Casos de uso:
  - Databases (SQL/NoSQL).
  - Big data, ERP/CRM.

### Amazon EFS (Elastic File System)

- Totalmente gerenciado.
- **Escalabilidade automática**.
- **Acesso simultâneo** por múltiplas instâncias EC2.
- Casos de uso:
  - Web serving, content management.
  - Ambientes de desenvolvimento.

### Instance Store

- Armazenamento **temporário** embutido na instância EC2.
- **Alta performance de I/O**.
- **Sem custo adicional**, mas **sem persistência**.
- Casos de uso:
  - Cache, buffers temporários, replicação.

---

## 7. Amazon S3

### Benefícios

- **Durabilidade**: 99.999999999%.
- **Escalabilidade** virtualmente ilimitada.
- **Segurança**: políticas de bucket e ACLs.
- **Versatilidade**: backup, dados, mídia, Big Data.

### Casos de Uso

- **Data backup**
- **Web hosting**
- **Distribuição de conteúdo**
- **Data lakes**

### Dicas para Prova

- S3 é **object storage**.
- Cada objeto possui: **data**, **key** (única por bucket), e **metadata**.

### Classes de Armazenamento

- **S3 Standard**: alta performance e baixa latência.
- **S3 Intelligent-Tiering**: movimentação automática com economia.
- **S3 Standard-IA**: acesso infrequente, acesso rápido.
- **S3 One Zone-IA**: barato, mas apenas em uma AZ.
- **S3 Glacier Instant Retrieval**: arquivamento com recuperação instantânea.
- **S3 Glacier Flexible Retrieval**: arquivamento, mas não imediato.
- **S3 Glacier Deep Archive**: armazenamento mais barato e mais lento.

---

## 8. Pergunta Exemplo

> **Como enviar 50.000 emails de forma eficiente?**  
> ✅ Resposta: **AWS Batch**  
> Motivo: permite agrupar e controlar lote de mensagens.  
> Lambda pode ser usado como gatilho, mas não para orquestração em larga escala.

---

## 9. Serverless Computing – AWS

### Características

- **Modelo de execução sem servidor**: o usuário não gerencia servidores.
- **Escalabilidade automática**.
- **Pagamento por uso (pay-as-you-go)**.

### Principais Serviços

- **AWS Lambda**
  - Executa código em resposta a eventos.
  - Suporta linguagens como Python, Node.js, Java, Go, etc.
  - Ideal para funções curtas e baseadas em eventos.
- **Amazon API Gateway**
  - Criação, publicação e monitoramento de APIs.
- **Amazon EventBridge**
  - Event-driven computing baseado em eventos de SaaS e AWS.
- **AWS Step Functions**
  - Orquestração de funções Lambda com estados e condições.

### Casos de Uso

- Backend de aplicações sem servidor.
- Processamento de arquivos em S3.
- Workflows baseados em eventos (ex: aprovação de documentos).
- APIs leves com escalabilidade automática.

---

## 10. Pergunta Exemplo – Serverless

> **Você precisa rodar código em resposta a um evento sem manter servidores. Qual o serviço ideal?**  
> ✅ Resposta: **AWS Lambda** 
> Motivo: permite executar funções sob demanda sem gerenciar infraestrutura.

---

## 📌 Continuação

Este documento será atualizado com:
- IAM e segurança
- CloudWatch e monitoramento
- CloudFront, Route53 e DNS
- EC2 Auto Scaling
- Certificação exam tips

---

### Atualizado em: 2025-05-18
