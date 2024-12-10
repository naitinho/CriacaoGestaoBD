# Criação e Gestão de um Banco de Dados

**Group 4 - Gestão de Projetos**

# Objetivo
O objetivo deste banco de dados é gerenciar informações sobre funcionários,
projetos, tarefas e alocações de recursos, facilitando o controle e a
organização de dados relevantes para as operações da empresa.

## Tabela: FUNCIONARIOS

| Coluna          | Tipo            | Restrição      | Descrição                        |
|-----------------|-----------------|---------------|----------------------------------|
| FUNCIONARIO_ID  | NUMBER          | PRIMARY KEY   | Identificador único do funcionário. |
| NOME            | VARCHAR2(100)   | NOT NULL      | Nome do funcionário.            |
| DATA_NASCIMENTO | DATE            |               | Data de nascimento do funcionário. |
| CARGO           | VARCHAR2(100)   |               | Cargo ocupado pelo funcionário. |
| SALARIO         | NUMBER(10,2)    |               | Salário do funcionário.         |
| DATA_ADMISSAO   | DATE            |               | Data de admissão na empresa.    |

## Tabela: TAREFAS

| Coluna          | Tipo            | Restrição                        | Descrição                             |
|-----------------|-----------------|----------------------------------|---------------------------------------|
| TAREFA_ID       | NUMBER          | PRIMARY KEY                     | Identificador único da tarefa.        |
| PROJETO_ID      | NUMBER          | FOREIGN KEY (PROJETOS.PROJETO_ID) | Relaciona a tarefa a um projeto.      |
| NOME            | VARCHAR2(100)   | NOT NULL                        | Nome da tarefa.                       |
| DESCRICAO       | CLOB            |                                  | Descrição detalhada da tarefa.        |
| RESPONSAVEL_ID  | NUMBER          | FOREIGN KEY (FUNCIONARIOS.FUNCIONARIO_ID) | Funcionário responsável pela tarefa.  |
| DATA_INICIO     | DATE            |                                  | Data de início da tarefa.             |
| DATA_FIM        | DATE            |                                  | Data prevista para finalização.       |
| STATUS          | VARCHAR2(50)    |                                  | Status atual da tarefa.               |

## Tabela: ALOCACOES_RECURSOS

| Coluna           | Tipo           | Restrição                           | Descrição                             |
|------------------|----------------|-------------------------------------|---------------------------------------|
| ALOCACAO_ID      | NUMBER         | PRIMARY KEY                        | Identificador único da alocação.      |
| PROJETO_ID       | NUMBER         | FOREIGN KEY (PROJETOS.PROJETO_ID)  | Relaciona a alocação a um projeto.    |
| FUNCIONARIO_ID   | NUMBER         | FOREIGN KEY (FUNCIONARIOS.FUNCIONARIO_ID) | Funcionário alocado no projeto.       |
| HORAS_TRABALHADAS| NUMBER(5,2)    |                                     | Horas trabalhadas no projeto.         |

## Cardinalidade dos Relacionamentos

1. **PROJETOS ↔ TAREFAS** (1:N)  
   Um projeto pode ter várias tarefas, mas cada tarefa pertence a um projeto.

2. **FUNCIONARIOS ↔ TAREFAS** (1:N)  
   Um funcionário pode ser responsável por várias tarefas, mas cada tarefa possui um responsável.

3. **PROJETOS ↔ ALOCACOES_RECURSOS** (1:N)  
   Um projeto pode ter várias alocações de recursos, mas cada alocação está associada a um único projeto.

4. **FUNCIONARIOS ↔ ALOCACOES_RECURSOS** (1:N)  
   Um funcionário pode estar alocado em vários projetos, mas cada alocação pertence a um único funcionário.

# Instruções

Conecte-se ao Oracle SQL*Plus ou SQL Developer como usuário com privilégios adequados

```sql
Execute o script de estrutura:

@estrutura.sql

-- Execute o script de dados:

@dados.sql

```sql

