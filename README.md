# Db-Mysql-lanchonete
# 🍔 Sistema de Banco de Dados para Lanchonete

Este projeto foi desenvolvido como parte dos meus estudos em SQL, utilizando o **MySQL Workbench**, com o objetivo de criar um sistema completo de gerenciamento para uma lanchonete. O projeto simula a operação de um negócio real, com foco em modelagem de dados, relacionamento entre tabelas e inserção de dados em massa.

---

## 🛠️ Tecnologias Utilizadas
- **MySQL Workbench** (ambiente de desenvolvimento)
- **SQL** (linguagem para criação e manipulação do banco de dados)

---

## 📦 Estrutura do Banco de Dados

O banco de dados `lanchonete` foi construído com as seguintes tabelas:

- `funcionarios`: informações pessoais, cargos e salários dos colaboradores
- `clientes`: cadastro de clientes
- `produtos`: cardápio da lanchonete com preços e categorias
- `info_produtos`: ingredientes e fornecedores dos produtos
- `pedidos`: pedidos realizados, com data, status e vínculo com clientes e funcionários

---

## ✨ Funcionalidades Desenvolvidas

- Criação de todas as tabelas com **chaves primárias e estrangeiras**
- Inserção de dados realistas com mais de **30 registros de clientes e pedidos**
- Definição de relacionamentos complexos entre tabelas (JOINs)
- Simulação de operações reais de um sistema de pedidos

---

## 📊 Exemplos de Consultas

```sql
-- Produtos e seus fornecedores
SELECT p.nome, i.fornecedor
FROM produtos p
JOIN info_produtos i ON p.id_produto = i.id_produto;

-- Pedidos pendentes
SELECT * FROM pedidos WHERE status = 'Pendente';

-- Funcionários com salário acima de R$ 3.000
SELECT nome, cargo, salario FROM funcionarios WHERE salario > 3000;

