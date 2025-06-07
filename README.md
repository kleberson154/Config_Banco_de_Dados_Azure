# ☁️ Configuração de Instância de Banco de Dados no Microsoft Azure

Este repositório documenta o processo passo a passo para criar e configurar uma **instância de Banco de Dados (DB)** na plataforma **Microsoft Azure**, utilizando o serviço **Azure Database** (ex: para SQL Server, MySQL, PostgreSQL, etc).

---

## 🎯 Objetivo

Aprender como provisionar uma instância de banco de dados gerenciado na nuvem, com foco em:

- Criar instância
- Configurar acesso seguro
- Conectar-se ao banco a partir de clientes externos

---

## 🧰 Pré-requisitos

- Conta ativa no [Microsoft Azure](https://portal.azure.com)
- Permissões para criar recursos no portal
- Cliente de banco de dados instalado (DBeaver, Azure Data Studio, MySQL Workbench, etc)

---

## 🚀 Etapas para Criar a Instância

### 1. Acesse o Portal

1. Entre no [portal Azure](https://portal.azure.com)
2. No menu lateral, clique em **"Criar um recurso"**
3. Pesquise por `Banco de Dados` e selecione o tipo desejado:
   - Azure SQL Database
   - Azure Database for MySQL
   - Azure Database for PostgreSQL

---

### 2. Configuração Básica

| Campo                | Exemplo                       |
|----------------------|-------------------------------|
| Assinatura           | Visual Studio / Pay-as-you-go |
| Grupo de Recursos    | `meu-grupo-db`                |
| Nome do Servidor     | `meudbserver`                 |
| Região               | `Brazil South`                |
| Tipo de Banco        | SQL / MySQL / PostgreSQL      |
| Nome da Instância    | `meubanco`                    |
| Usuário Admin        | `adminazure`                  |
| Senha                | `SenhaForte123!`              |
| Versão               | 5.7 / 13 / 15 (depende do banco) |

---

### 3. Escalabilidade e Preço

- **Camada de serviço**:
  - Basic (dev/teste)
  - General Purpose (produção)
  - Business Critical (alto desempenho)

- Escolha o **número de vCores**, memória e armazenamento.

---

### 4. Configuração de Rede

- Habilite **acesso público** se desejar conectar de fora do Azure.
- Configure regras de **firewall**:
  - Permitir seu IP local (ex: `187.23.x.x`)
  - Ou permitir **"Acesso a serviços do Azure"**

---

### 5. Criação e Provisionamento

- Clique em **"Revisar + Criar"**
- Valide os dados
- Clique em **"Criar"**
- Aguarde alguns minutos até a conclusão do provisionamento

---

## 🔗 Conectando-se ao Banco

### 🔐 Strings de Conexão

Você encontrará no painel da instância, em **"Strings de conexão"**, os formatos para:

- JDBC
- ADO.NET
- ODBC
- PHP, Python, Node.js

### 🧪 Teste de Conexão

Exemplo com `psql` para PostgreSQL:

```bash
psql --host=meudbserver.postgres.database.azure.com \
     --username=adminazure@meudbserver \
     --dbname=meubanco
```

### 🛡️ Boas Práticas de Segurança

- Use firewall por IP e restrinja o acesso somente aos IPs necessários.
- Ative SSL/TLS obrigatório para conexões criptografadas.
- Utilize o Azure Key Vault para armazenar e gerenciar segredos e senhas.
- Crie usuários com permissões mínimas para aplicações.
- Monitore acessos e logs regularmente.

### 🧹 Pós-Criação

- Crie e gerencie usuários e roles adequadamente.
- Estruture tabelas, índices e schemas conforme a necessidade do sistema.
- Automatize backups e restaurações (Azure oferece backups automáticos).
- Use o Azure Monitor para acompanhar métricas e desempenho do banco.
- Mantenha o banco sempre atualizado com patches e atualizações recomendadas.

### 🔐 Strings de Conexão

Você encontrará no painel da instância, em **"Strings de conexão"**, os formatos para:

- JDBC
- ADO.NET
- ODBC
- PHP, Python, Node.js

### 📎 Links Úteis

- Documentação do Azure SQL Database -> https://learn.microsoft.com/azure/azure-sql/
- Documentação do Azure Database for PostgreSQL -> https://learn.microsoft.com/azure/postgresql/
- Documentação do Azure Database for MySQL -> https://learn.microsoft.com/azure/mysql/
- Azure Key Vault -> https://learn.microsoft.com/azure/key-vault/
- Azure Monitor -> https://learn.microsoft.com/azure/azure-monitor/
