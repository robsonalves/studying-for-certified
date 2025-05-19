# AWS Certified Cloud Practitioner - Estudo Completo

Este documento reúne todos os tópicos estudados para a certificação AWS Certified Cloud Practitioner, com foco acadêmico e explicações visuais extraídas de slides.

---

## 15. Exemplos de Serviços – IaaS, PaaS, SaaS

### Exemplo de PaaS (Platform as a Service)

A AWS Elastic Beanstalk é um exemplo clássico de **PaaS (Plataforma como Serviço)**, pois permite aos desenvolvedores implantar aplicações sem precisar gerenciar a infraestrutura subjacente (como servidores, balanceadores de carga ou instâncias EC2).  

💡 **Elastic Beanstalk cuida automaticamente do provisionamento, balanceamento de carga, escalabilidade e monitoramento da aplicação.**

#### Comparações com outros modelos:

- **Dropbox** e **Gmail** são exemplos de **SaaS (Software as a Service)**: o usuário consome a aplicação pronta, sem interagir com a infraestrutura ou plataforma.
- **Microsoft Azure** refere-se à plataforma completa de nuvem da Microsoft, podendo englobar IaaS, PaaS e SaaS – não é um exemplo específico de PaaS.

![Exemplo de PaaS - Elastic Beanstalk](../assets/exemplo-paas-elastic-beanstalk.png)

## 14. Shared Responsibility Model (Modelo de Responsabilidade Compartilhada)


A AWS opera sob um modelo de responsabilidade compartilhada entre a **plataforma da AWS** e o **cliente**.

---

### Explicação Adicional

O modelo de responsabilidade compartilhada da AWS define claramente quais aspectos da segurança são de responsabilidade da AWS e quais pertencem ao cliente:

- A **AWS é responsável pela segurança da *infraestrutura da nuvem*** (*security "of" the cloud*), incluindo a segurança física dos data centers, hardware, software base (como hipervisores) e rede.

- O **cliente é responsável pela segurança *dentro da nuvem*** (*security "in" the cloud*), o que inclui:
  - Dados e criptografia (lado do cliente e do servidor)
  - Configurações do sistema operacional, rede e firewall
  - Gerenciamento de usuários e permissões via IAM
  - Segurança da aplicação e dados sensíveis

💡 As responsabilidades podem variar de acordo com o serviço utilizado (EC2 vs Lambda, por exemplo).

📌 A AWS oferece recursos como **IAM, Security Groups, KMS, backup automático** e outras ferramentas para ajudar os clientes a protegerem seus ambientes.

📷 ![Shared Responsibility Model](../assets/shared-responsibility-model.jpeg)

Fonte: [https://aws.amazon.com/compliance/shared-responsibility-model/](https://aws.amazon.com/compliance/shared-responsibility-model/)

### Responsabilidades do Cliente (Security *in* the Cloud)

- **Dados do cliente**
- **Gerenciamento de identidade e acesso (IAM)**
- **Configuração de sistema operacional, rede e firewall**
- **Criptografia no lado do cliente e integridade dos dados**
- **Criptografia no lado do servidor (sistema de arquivos ou dados)**
- **Proteção do tráfego de rede (criptografia, integridade, identidade)**

### Responsabilidades da AWS (Security *of* the Cloud)

- **Infraestrutura global da AWS**
  - Regiões
  - Zonas de Disponibilidade (AZs)
  - Edge Locations
- **Serviços de Software**
  - Compute
  - Storage
  - Database
  - Networking

📌 Fonte oficial: [Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)

## 12. Infraestrutura Global da AWS

A infraestrutura global da AWS é composta por:

- **Regiões (Regions)**: localizações físicas ao redor do mundo onde a AWS tem data centers.
- **Zonas de Disponibilidade (Availability Zones - AZs)**: grupos de um ou mais data centers distintos dentro de uma região.

### Conceitos Importantes

- Cada **região** é composta por **múltiplas AZs**, projetadas para serem isoladas umas das outras em falhas físicas.
- Os dados podem ser replicados entre AZs para garantir alta disponibilidade e tolerância a falhas.
- Clientes podem escolher a região onde os recursos serão implantados, o que afeta latência, conformidade e custo.

📌 Link oficial da AWS sobre infraestrutura global:  
[https://aws.amazon.com/about-aws/global-infrastructure/regions_az/](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)

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


---

## 11. Cloud Computing – Visão Geral e Vantagens

### Conceito

- Modelo de entrega de serviços de TI pela internet.
- Fornece **armazenamento, poder computacional e software** sob demanda.
- Principais provedores: **AWS, Azure, Google Cloud**.

### Benefícios Principais

1. **Trade fixed expense (CapEx) for variable expense (OpEx)**  
   - CapEx: grandes investimentos iniciais.  
   - OpEx: paga-se apenas pelo uso.

2. **Benefit from massive economies of scale**  
   - Preços baixos devido ao uso agregado por milhares de clientes.

3. **Stop guessing capacity**  
   - Escalabilidade elástica conforme necessidade, com aviso prévio de minutos.

4. **Increase speed and agility**  
   - Novos recursos podem ser implantados quase instantaneamente.

5. **Stop spending money running and maintaining data centers**  
   - Foco no cliente, não em infraestrutura de TI.

6. **Go global in minutes**  
   - Baixa latência e melhor experiência para clientes ao redor do mundo.

### Características Fundamentais segundo o NIST

De acordo com a publicação especial 800-145 do NIST (National Institute of Standards and Technology), o modelo de computação em nuvem apresenta **cinco características essenciais**:

1. **On-demand self-service**  
   - O usuário pode provisionar e liberar recursos conforme necessário, sem interação humana com o provedor.

2. **Broad network access**  
   - Os recursos estão disponíveis na rede e acessíveis por meio de dispositivos como notebooks, smartphones e tablets.

3. **Multi-tenancy & Resource pooling**  
   - Os recursos são agrupados e alocados dinamicamente para diferentes usuários conforme a demanda.
   - Multi-tenancy permite que múltiplos clientes compartilhem a mesma infraestrutura com segurança e isolamento de dados.

4. **Rapid elasticity**  
   - Capacidade de expandir ou reduzir recursos de maneira rápida para se adaptar à demanda.

5. **Measured service**  
   - O uso de recursos é monitorado e reportado, permitindo cobrança baseada no consumo (modelo pay-as-you-go).

---

### NIST – 5 Características da Computação em Nuvem

Baseado na publicação [NIST SP 800-145](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-145.pdf), as cinco características definidoras de computação em nuvem são:

1. **On-demand self-service**  
   - Usuários podem provisionar e liberar recursos automaticamente sem intervenção humana direta.

2. **Broad network access**  
   - Recursos são acessíveis via rede por meio de dispositivos heterogêneos como laptops, celulares e tablets.

3. **Multi-tenancy & Resource pooling**  
   - Recursos são compartilhados entre múltiplos usuários (multi-tenancy) e alocados dinamicamente conforme a demanda.

4. **Rapid elasticity**  
   - Capacidade de escalar recursos de maneira rápida e elástica, com crescimento ou redução sob demanda.

5. **Measured service**  
   - O uso de recursos é monitorado, controlado e relatado, permitindo cobrança sob demanda com transparência.

---

### ❌ Característica que NÃO é típica da Computação em Nuvem

- **Single-tenancy** não é considerada uma característica fundamental da computação em nuvem.
- O modelo padrão é o **multi-tenancy**, no qual múltiplos usuários (tenants) compartilham os mesmos recursos (como armazenamento ou aplicações), cada um com seu próprio espaço seguro e isolado.
- Single-tenancy pode existir em cenários específicos (como compliance ou segurança), mas **não é uma característica essencial** segundo os princípios do NIST.

---

## 13. Fundamentos de Alta Disponibilidade e Recuperação de Desastres

### Alta Disponibilidade (High Availability)

- Refere-se à capacidade de um sistema permanecer funcional mesmo diante de falhas parciais.
- Implementado por meio de:
  - Recursos distribuídos entre múltiplas **Availability Zones (AZs)**.
  - **Load Balancers** para distribuir tráfego.
  - **Auto Scaling Groups** para substituir instâncias automaticamente.
- Exemplo na AWS: usar RDS em modo **Multi-AZ** ou aplicações distribuídas com **Elastic Load Balancer**.

### Recuperação de Desastres (Disaster Recovery)

- Estratégias para restaurar serviços em caso de falha catastrófica.
- Conceitos-chave:
  - **RTO (Recovery Time Objective)**: quanto tempo o sistema pode ficar fora do ar.
  - **RPO (Recovery Point Objective)**: quanto de dados a empresa pode perder.
- Estratégias comuns:
  - **Backup & Restore**: mais simples e barato, mas com maior RTO.
  - **Pilot Light**: recursos mínimos ativos, ativação rápida do ambiente completo.
  - **Warm Standby**: ambiente funcional, porém com capacidade reduzida.
  - **Multi-site Active/Active**: ambientes replicados e ativos em mais de uma região.

---

### Exemplo Visual – Alta Disponibilidade e Recuperação de Desastres

A imagem abaixo representa um cenário típico de alta disponibilidade (HA) e recuperação de desastres (DR) em duas regiões diferentes da AWS:

- **Região us-west-1**: mostra um EC2 Service distribuído entre duas AZs (AZ-a e AZ-b), com uma instância rodando em AZ-a.
- **Região us-east-1 (N. Virginia)**: mostra duas instâncias EC2 distribuídas em AZ-a e AZ-b, configuradas para alta disponibilidade.
- Esse tipo de arquitetura é usado **para tolerar falhas de zona** e possibilitar **baixa latência e recuperação de desastres entre regiões**.

📌 **Destaque**:  
A região **N. Virginia** (us-east-1) é frequentemente usada em exemplos da AWS por conter o maior número de **Availability Zones (6 AZs)**.

Essa abordagem ilustra a importância de distribuir suas cargas de trabalho entre múltiplas AZs e até mesmo entre **regiões diferentes** para garantir resiliência e continuidade dos serviços.

---

### Definições Complementares – HA & DR

📌 **High Availability (HA)**:  
É a capacidade de um sistema, serviço ou aplicação permanecer acessível e funcional com **mínimo tempo de inatividade**, mesmo diante de falhas de hardware, software, manutenção programada ou eventos inesperados.

📌 **Disaster Recovery (DR)**:  
Conjunto de estratégias e serviços usados para proteger, restaurar e garantir a **recuperação de sistemas críticos de TI e dados**, após eventos catastróficos ou interrupções significativas.

#### Dois principais tipos de replicação:

- **Replicação entre Zonas de Disponibilidade (AZs)**:
  - Foco em Alta Disponibilidade (HA) e recuperação de desastres em nível de zona.
  - Minimiza o tempo de inatividade.
  
- **Replicação entre Regiões**:
  - Foco em latência reduzida e recuperação de desastres regionais.
  - Aproxima os serviços dos clientes e garante continuidade mesmo em falhas amplas.

🗺️ Exemplo visual reforça:
- **us-west-1**: apenas uma instância EC2 em uma AZ.
- **us-east-1**: instâncias em duas AZs distintas para alta disponibilidade.
- Ilustra as práticas de replicação entre AZs e entre Regiões.

---
