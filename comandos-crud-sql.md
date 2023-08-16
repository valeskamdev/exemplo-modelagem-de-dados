# Comandos para operações CRUD no Banco de dados

## Resumo

- C -> **CREATE** (inserir dados usando o comando `INSERT`)
- R -> **READ** (ler dados usando o comando `SELECT`)
- U -> **UPDATE** (atualizar dados usando o comando `UPDATE`)
- D -> **DELETE** (deletar dados usando o comando `DELETE`)

## CREATE

### INSERT

#### FABRICANTES

```sql
INSERT INTO fabricantes (nome) VALUES ('Asus');
INSERT INTO fabricantes (nome) VALUES ('Dell');
INSERT INTO fabricantes (nome) VALUES ('Apple');

INSERT INTO fabricantes (nome) VALUES ('LG'), ('Samsung'), ('Brastemp');
INSERT INTO fabricantes (nome) VALUES ('Positivo'), ('Microsoft');
```
#### PRODUTOS

```sql
INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id)
VALUES ('Ultrabook', 'Equipamento de alto desempenho', 3500, 7, 2);

INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id)
VALUES ('Tablet Android', 'Tablet com a versão 14 do Android', 1500.99, 5, 5);

INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id)
VALUES ('Geladeira', 'Geladeira Frost Free', 5000, 12, 6), ('iPhone 18 Pro Max', 'Diversas cores', 12666, 3, 3), ('iPad Mini', 'Com tela de 7 polegadas', 4999.01, 5, 3);
```