# 📊 Projeto Integrador: Persistência Poliglota Northwind

- Modelagem e Análise Híbrida de Dados (PostgreSQL + MongoDB)

- Instituição: IPOG

- Unidade 04 - Projeto Área 03 (Banco de Dados)

- Status: 🚀 Em Desenvolvimento (Sprint 01/07)

# 📖 1. Visão Geral (Kick-off)

- Este projeto faz parte do Projeto Integrador em Inteligência Artificial Baseada em Dados.

- O objetivo principal é implementar uma solução híbrida para o dataset clássico Northwind, 

comparando o desempenho e a flexibilidade entre um SGBD Relacional (PostgreSQL) e um SGBD NoSQL (MongoDB Atlas).

# 🎯 Objetivos de Negócio

- Garantir a integridade financeira e transacional via SQL.

- Otimizar o catálogo de produtos e a leitura de documentos complexos via NoSQL.

- Avaliar o ROI técnico na escolha entre consistência (ACID) e escalabilidade (Base).

# 🛠️ 2. Tecnologias & FerramentasRelacional: 

- PostgreSQL (Hospedado localmente/Docker).

- NoSQL: MongoDB Atlas (Cloud Tier).

- Modelagem: DBeaver / LucidChart (Diagrama ER).

- Integração: Python 3.x (Psycopg2, PyMongo).

- Metodologia: CRISP-DM & Scrum.

### 📅 Sprint 03: Modelagem Relacional (PostgreSQL)
**Período:** 25/02 a 03/03  
**Fase CRISP-DM:** Data Preparation / Modeling

| Item | Descrição Detalhada |
| :--- | :--- |
| **Objetivos** | • Implementar o modelo relacional otimizado no PostgreSQL.<br>• Criar o schema completo com constraints e regras de validação. |
| **Atividades** | • Desenvolvimento do script DDL (Data Definition Language).<br>• Criação de Índices Estratégicos para otimização de busca.<br>• Implementação de Views e funções para relatórios.<br>• População das tabelas com o dataset Northwind. |
| **Entregáveis** | • Arquivo `.sql` com o Schema (Tabelas, PKs, FKs).<br>• Scripts de Constraints e Validações implementadas.<br>• Script de carga de dados (DML). |
| **Foco Técnico** | Garantir a **Integridade Referencial** e a **3ª Forma Normal**. |

# 🗄️ 4. Arquitetura da Solução

# 🔵 PostgreSQL (Camada Transacional)

Focado em dados que exigem alta consistência:

- Orders, 

- Order_Details, 

- Shippers, 

- Suppliers.

Destaque: Implementação de triggers para validação de estoque.

# 🟢 MongoDB Atlas (Camada de Experiência)

Focado em agilidade e dados não estruturados:

- Products (Catálogo), Customers (Perfil rico), Employees (Bio e Fotos).

- Destaque: Uso de Extended Reference para otimizar a visualização de categorias.

# 🧪 5. Casos de Teste de Agnosticidade

Para validar a robustez do banco, o projeto foca em registros críticos:

- Vins et alcools Chevalier: Teste de codificação UTF-8 e acentuação francesa.

- Andrew Fuller: Gerenciamento de ativos binários (fotos) via URL externa.

- Hierarchy: Mapeamento do campo ReportsTo em estrutura de árvore no NoSQL.

# 🚀 6. Como Executar o Projeto

1. **Clone o repositório:**
   ```bash
   git clone [https://github.com/seu-usuario/projeto-ipog-northwind.git](https://github.com/seu-usuario/projeto-ipog-northwind.git)
   cd projeto-ipog-northwind

# 🛠️ Configuração do Ambiente e Execução

## Setup do Ambiente Virtual (Recomendado)
Cria um ambiente isolado para instalar as bibliotecas necessárias (Pandas, Psycopg2, PyMongo) sem conflitar com seu sistema:

```bash
# Criar o ambiente virtual
python -m venv venv

# Ativar o ambiente (Linux/Mac)
source venv/bin/activate

# Ativar o ambiente (Windows)
.\venv\Scripts\activate

# Instalar as dependências
pip install -r requirements.txt

## Setup SQL (PostgreSQL)
Com o PostgreSQL instalado e o serviço rodando, utilize os comandos abaixo para preparar a base Northwind:

# Criar o banco de dados (caso ainda não exista)
createdb -U seu_usuario northwind

# Importar o script de estrutura e dados (DML/DDL)
psql -U seu_usuario -d northwind -f sql/northwind_psql.sql

## Migração para NoSQL (MongoDB Atlas)
Após configurar sua connection_string no arquivo .env, execute o script de transformação e carga:

# Rodar o script de migração (Postgres -> MongoDB)
python scripts/migrate_to_nosql.py
