Equipe:
Lucas Vasconcelos e Yaggo 
Atividade Extra
Engenharia da Computação - UNINORTE 
Quarto Período 
2025

# 🚀 TechManage - Sistema de Gestão de Projetos

Sistema CRUD completo desenvolvido para a TechManage Solutions, automatizando o controle de usuários, projetos e tarefas que anteriormente era feito manualmente.

## 📋 Sobre o Projeto

A TechManage Solutions enfrentava problemas de gestão manual de informações, resultando em inconsistências e perda de dados. Este sistema web resolve esses problemas através de uma API REST completa com CRUD para todas as entidades.

## 🛠 Tecnologias Utilizadas

### Backend
- **Node.js** - Ambiente de execução JavaScript
- **Express.js** - Framework web para criação do servidor
- **Sequelize ORM** - Mapeamento objeto-relacional
- **MySQL** - Sistema gerenciador de banco de dados
- **bcryptjs** - Criptografia de senhas
- **cors** - Controle de acesso entre origens
- **dotenv** - Gerenciamento de variáveis de ambiente

### Ferramentas de Desenvolvimento
- **Nodemon** - Reinicialização automática em desenvolvimento
- **Sequelize CLI** - Interface de linha de comando

## 🗃 Modelagem de Dados

### Entidades
- **usuario** (Usuários) - Gestão de usuários do sistema
- **projeto** (Projetos) - Controle de projetos
- **tarefa** (Tarefas) - Gestão de tarefas dos projetos

### Relacionamentos
Users (1) ----< Projects (1) ----< Tasks

### Estrutura do Banco
```sql
-- Tabela usuario
id, nome, email, senha, perfil

-- Tabela Projeto  
id, titulo, descricao, data_inicio, data_fim, id_usuario

-- Tabela Tarefa
id, titulo, status, prioridade, id_projeto

Pré-requisitos
Node.js (versão 18 ou superior)

MySQL (versão 8.0 ou superior)

npm ou yarn

Configure o banco de dados
-- Crie o banco de dados
CREATE DATABASE techmanage;

Crie um arquivo .env na raiz do projeto:
DB_HOST=localhost
DB_PORT=3306
DB_NAME=techmanage
DB_USER=root
DB_PASS=sua_senha
PORT=3000
NODE_ENV=development

Execute a aplicação

# Desenvolvimento (com nodemon)
npm run dev

# Produção
npm start

--Definição das pastas 
techmanage/
config/config.json --Configurações do Sequelize

controllers/ -- Lógica de negócio
usuarioController.js
projetoController.js
tarefaController.js

models/ --Modelos de dados
index.js
usuario.js
projeto.js
tarefa.js

routes/ --Definição de rotas
index.js
usuarioRoutes.js
projetoRoutes.js
tarefaRoutes.js

migrations/ -- Controle de versão do banco

seeders/
20251109174914-initial-data.js --Dados iniciais

.env --Variáveis de ambiente
index.js --Servidor principal
package.json --Dependências do projeto

Configuração do Banco
-- Tabela usuario
CREATE TABLE usuario (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  senha VARCHAR(255) NOT NULL,
  perfil VARCHAR(50) DEFAULT 'usuario',

);

-- Tabela projeto
CREATE TABLE projeto (
  id INT AUTO_INCREMENT PRIMARY KEY,
  titulo VARCHAR(255) NOT NULL,
  descricao TEXT,
  data_inicio DATE,
  data_fim DATE,
  id_usuario INT NOT NULL,

  FOREIGN KEY (id_usuario) REFERENCES usuario(id) ON DELETE CASCADE
);

-- Tabela tarefa
CREATE TABLE tarefa (
  id INT AUTO_INCREMENT PRIMARY KEY,
  titulo VARCHAR(255) NOT NULL,
  status VARCHAR(50) DEFAULT 'pendente',
  prioridade VARCHAR(50) DEFAULT 'media',
  id_projeto INT NOT NULL,

  FOREIGN KEY (id_projeto) REFERENCES projeto(id) ON DELETE CASCADE
);
