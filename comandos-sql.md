# Comandos SQL - Referências

## Modelagem Física com comandos DDL

### Criação de banco de dados

```sql
CREATE DATABASE vendas CHARACTER SET utf8mb4;
```

### Criação da tabela fabricantes

```sql
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

###  Visualizar detalhes estruturais da tabela

```sql
DESC fabricantes;
``` 

### Criação da tabela produtos

```sql
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2) NOT NULL,
    fabricante_id INT NOT NULL
);
```