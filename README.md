# 📊 Banco de Dados - Lanchonete e Consultas

Este projeto contém um banco de dados relacional para gerenciar **funcionários, clientes, produtos e pedidos** de uma lanchonete.  
O objetivo é fornecer um modelo completo que permita **cadastro, controle e análise de operações** do negócio.

---

## 📂 Estrutura do Banco de Dados

### 🧑 Funcionários (`funcionarios`)
Armazena dados dos colaboradores da lanchonete.
- `id_funcionario` (PK)
- `nome`
- `cpf`
- `data_nascimento`
- `endereço`
- `telefone`
- `email`
- `cargo`
- `salario`
- `data_admissao`

### 👥 Clientes (`clientes`)
Informações de clientes cadastrados.
- `id_cliente` (PK)
- `nome`
- `cpf`
- `data_nascimento`
- `endereço`
- `telefone`
- `email`
- `data_cadastro`

### 🍽️ Produtos (`produtos`)
Catálogo de produtos da lanchonete.
- `id_produto` (PK)
- `nome`
- `descrição`
- `preço`
- `categoria`

### 🧾 Pedidos (`pedidos`)
Registra os pedidos realizados, vinculando cliente, funcionário e produto.
- `id_pedido` (PK)
- `id_cliente` (FK → clientes)
- `id_funcionario` (FK → funcionarios)
- `id_produto` (FK → produtos)
- `quantidade`
- `preco`
- `data_pedido`
- `status`

### 📦 Informações de Produtos (`info_produtos`)
Detalhes adicionais de cada produto.
- `id_info` (PK)
- `id_produto` (FK → produtos)
- `ingredientes`
- `fornecedor`

---

## 📊 Exemplos de Consultas SQL

- Listar todos os pedidos com informações de cliente, funcionário e produto:
```sql
SELECT pe.id_pedido, pe.quantidade, pe.data_pedido,
       c.nome AS nome_cliente, f.nome AS nome_funcionario,
       p.nome AS nome_produto, p.preço
FROM pedidos pe
JOIN clientes c ON pe.id_cliente = c.id_cliente
JOIN funcionarios f ON pe.id_funcionario = f.id_funcionario
JOIN produtos p ON pe.id_produto = p.id_produto;
```

- Calcular a média de preços por categoria:
```sql
SELECT categoria, ROUND(AVG(preco),2) AS media_preco
FROM produtos
GROUP BY categoria;
```

- Buscar clientes que nunca fizeram pedido:
```sql
SELECT c.nome
FROM clientes c
LEFT JOIN pedidos p ON c.id_cliente = p.id_cliente
WHERE p.id_pedido IS NULL;
```

---

## 🛠️ Funções e Views Implementadas

- **View `resumo_pedido`** → resumo de cada pedido (cliente, funcionário, produto e total).  
- **Função `BuscaIngredientesProduto(id_produto)`** → retorna a lista de ingredientes de um produto.  
- **Função `mediaPedido(id_pedido)`** → compara o valor do pedido com a média dos demais pedidos.

---

## 🚀 Como Usar

1. Crie o banco de dados:
```sql
CREATE DATABASE Lanchonete;
USE Lanchonete;
```

2. Execute o script `Db (Lanchonete e Consultas).sql` para criar as tabelas e inserir os dados.

3. Explore as tabelas e consultas sugeridas para análise.

---

## 📌 Observações

- Os dados de exemplo incluem **funcionários, clientes, produtos, pedidos e fornecedores** fictícios.  
- O banco pode ser expandido com relatórios e dashboards conectados a ferramentas de análise como **Power BI, Tableau ou Python (Pandas/SQLAlchemy)**.

---
