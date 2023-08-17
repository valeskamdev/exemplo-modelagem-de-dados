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

INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id)
VALUES ('Xbox Series S', 'Velocidade e desempenho de última geração', 1977, 5, 8), ('Notebook Motion', 'Intel Dual Core 4GB de RAM, 128GB SSD e Tela 14,1 polegadas', 1213.65, 8, 7);
```

## READ

### SELECT

#### PRODUTOS

```sql
SELECT * FROM produtos;

SELECT nome, preco FROM produtos;
SELECT preco, nome FROM produtos;

SELECT nome, preco, quantidade FROM produtos WHERE preco < 5000;

-- Mostre nome e descrição somente dos produtos da Apple
SELECT nome, descricao FROM produtos WHERE fabricante_id = 3;
```
##### OPERADORES LÓGICOS: AND, OR, NOT

###### AND

```sql
SELECT nome, preco FROM produtos WHERE preco >= 2000 AND preco <= 6000;

--A query abaixo não retorna registros
-- já que as condições não são foram totalmente atendidas
SELECT nome, preco FROM produtos WHERE preco > 5000 AND preco <= 6000;
```
###### OR
    
```sql
SELECT nome, preco FROM produtos WHERE preco > 5000 OR preco <= 3000;

-- Exiba nome e proço somente dos produtos da Apple e da Samsung
SELECT nome, preco FROM produtos WHERE fabricante_id = 3 OR fabricante_id = 5;
SELECT nome, preco FROM produtos WHERE fabricante_id IN(3, 5); -- IN é uma abreviação para OR
SELECT nome, preco FROM produtos WHERE fabricante_id NOT IN(3, 5); -- NOT IN serve para negar o IN 
```
###### NOT

```sql
SELECT nome, descricao, preco FROM produtos WHERE NOT fabricante_id = 8;
SELECT nome, descricao, preco FROM produtos WHERE fabricante_id != 8; -- != é uma abreviação para NOT
```
## UPDATE

### UPDATE

#### FABRICANTES

```sql
UPDATE fabricantes SET nome = 'Asus do Brasil' WHERE id = 1;
```

#### PRODUTOS

```sql
UPDATE produtos SET preco = 6549.74 WHERE id = 4;   

-- Altere a quantidade dos produtos da Apple e da Samsung para 20
UPDATE produtos SET quantidade = 20 WHERE fabricante_id IN(3, 5);
```	