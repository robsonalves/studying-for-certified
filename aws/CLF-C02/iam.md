## 16. Identity and Access Management (IAM)

### Conceito

O **IAM (Identity and Access Management)** é um serviço **global** (não regional) da AWS que ajuda a controlar de forma segura o acesso a serviços e recursos da AWS.

- ✅ **Global Service**: as políticas e permissões se aplicam globalmente, não sendo restritas a uma região específica.
- ✅ **Globally resilient**: os dados e acessos são seguros em todas as regiões.

---

### O que será aprendido

- Como usar **políticas (policies)** para conceder ou negar permissões de acesso.
- Os **três tipos de identidades**:
  - **Users**
  - **Groups**
  - **Roles**
- Princípio do **menor privilégio (least privilege)**.
- Como configurar a **Autenticação Multifator (MFA)** para os usuários e por que ela é importante.
- Como criar **Access Keys** para acesso programático via CLI.


📌 IAM é essencial para **segurança e governança** na nuvem AWS.

---

### Políticas de Permissão (IAM Policies)

- Usuários IAM podem ser atribuídos com **políticas de permissão** para controlar o acesso a serviços e recursos.
- Deve-se seguir o princípio do **menor privilégio**, garantindo apenas as permissões mínimas necessárias.
- Existem dois tipos principais de políticas:
  - **Inline Policies**: embutidas diretamente em um usuário, grupo ou role.
  - **Managed Policies**: políticas independentes que podem ser associadas a múltiplos usuários, grupos ou roles.
    - **AWS Managed**: criadas pela AWS.
    - **Customer Managed**: criadas pelo cliente.

📘 As políticas são escritas em **JSON** e definem ações (`Action`), recursos (`Resource`) e efeitos (`Effect`), como `Allow` ou `Deny`.

#### Avaliação de Políticas

- Ordem de avaliação:
  1. `Explicit Deny`
  2. `Explicit Allow`
  3. `Implicit Deny` (padrão)

📷 ![IAM Policies](../assets/iam-policies.jpeg)

---

### Exemplo de Política em JSON

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowFullAccessToS3",
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::*"
    },
    {
      "Sid": "DenyAccessToSecretBucket",
      "Effect": "Deny",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::secretbucket-ff2277xx",
        "arn:aws:s3:::secretbucket-ff2277xx/*"
      ]
    }
  ]
}
```

📷 ![IAM Policy Example](../assets/iam-policy-json.jpeg)



📷 ![IAM Overview](../assets/iam-overview.jpeg)

---

### IAM Roles

As **IAM Roles** permitem conceder permissões temporárias para acessar serviços e recursos da AWS sem a necessidade de usar credenciais permanentes.

- São **assumidas** por:
  - Serviços da AWS
  - Usuários na mesma conta AWS
  - Usuários de contas diferentes da AWS
  - Aplicações confiáveis (trusted applications)
  
- Podem ser usadas para:
  - Conceder acesso temporário a recursos
  - Delegar acesso entre contas
  - Permitir acesso a aplicações externas
  - Atribuir permissões a serviços da AWS (como EC2, Lambda etc.)

- As permissões são atribuídas por **IAM Policies**, assim como ocorre com usuários.
- É possível limitar o escopo da Role a recursos específicos (por exemplo, acesso a um bucket específico do S3).

📷 ![IAM Roles](../assets/iam-roles.jpeg)

---

### IAM User Groups

- **IAM Groups** permitem organizar e gerenciar usuários IAM de forma lógica e conveniente.
- **Grupos podem receber permissões** para executar ações específicas ou acessar recursos. Os **usuários herdam essas permissões** dos grupos aos quais pertencem (além das permissões individuais).
- Isso permite **atribuir permissões a vários usuários de uma vez**, sem precisar configurar permissões individualmente.
- Usuários podem ser adicionados ou removidos de grupos conforme necessário, facilitando o gerenciamento de acesso.
- Um usuário pode pertencer a **até 10 grupos diferentes**.
- **Grupos não podem ser aninhados** (não é possível incluir grupos dentro de outros grupos).
- Não existe grupo padrão (default group) que inclua automaticamente todos os usuários da conta.
- Quotas da conta:
  - Até **5.000 usuários**
  - Até **500 grupos**
  - Não há limite de usuários por grupo

📷 ![IAM User Groups](../assets/iam-user-groups.jpeg)
