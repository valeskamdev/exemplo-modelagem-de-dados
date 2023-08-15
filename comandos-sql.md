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
