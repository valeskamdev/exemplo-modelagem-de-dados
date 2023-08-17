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
## DELETE

### DELETE

#### FABRICANTES

```sql
DELETE FROM fabricantes WHERE id = 1;
DELETE FROM fabricantes WHERE id = 4;
DELETE FROM fabricantes WHERE id = 3;   
```

## SELECT: outras formas de uso

```sql
SELECT * FROM produtos ORDER BY nome; -- Ordena os registros em ordem alfabética
SELECT * FROM produtos ORDER BY preco; ; -- Ordena os registros em ordem crescente de preço
SELECT * FROM produtos ORDER BY preco DESC; -- Ordena os registros em ordem decrescente de preço 
SELECT * FROM produtos WHERE quantidade = 20 ORDER BY nome; -- Ordena os registros que possuem quantidade igual a 20 em ordem alfabética
```

## Busca de dados

```sql
SELECT nome, descricao FROM produtos WHERE descricao LIKE '%sistema'; -- Busca todos os produtos que terminam com a palavra sistema
SELECT nome, descricao FROM produtos WHERE descricao LIKE 'versão%'; -- Busca todos os produtos que começam com a palavra versão
SELECT nome, descricao FROM produtos WHERE descricao LIKE '%tablet%'  OR  nome LIKE '%tela%'; -- Busca todos os produtos que possuem a palavra tablet na descrição ou a palavra tela no nome
```
## Operações e funções de agregação

```sql
SELECT SUM(preco) FROM produtos; -- Soma todos os preços dos produtos
SELECT SUM(preco) AS Total FROM produtos; -- Soma todos os preços dos produtos e renomeia a coluna para Total

SELECT nome AS Produto, preco AS 'Preço' FROM produtos; -- Renomeia as colunas nome e preco para Produto e Preço respectivamente  
SELECT nome Produto, preco 'Preço' FROM produtos; -- Renomeia as colunas nome e preco para Produto e Preço respectivamente (SEM AS)

SELECT AVG(preco) AS 'Média dos Preços' FROM produtos; -- Calcula a média dos preços dos produtos
SELECT ROUND(AVG(preco), 2) AS 'Média dos Preços' FROM produtos; -- Calcula a média dos preços dos produtos e arredonda para 2 casas decimais

SELECT COUNT(id) as "Quantidade de Produtos" FROM produtos; -- Conta a quantidade de produtos
SELECT COUNT(DISTINCT fabricante_id) as "Quantidade de Fabricantes em Produtos" FROM produtos; -- Conta a quantidade de fabricantes em produtos (DISTINCT é uma cláusula/flag que elimina os valores duplicados)
```

## Operadores matemáticos

```sql
SELECT nome, preco, quantidade, (preco * quantidade) AS 'Total' FROM produtos; -- Calcula o total de cada produto
```

## Segmentação/Agrupamento de dados

```sql
SELECT fabricante_id, SUM(preco) AS Total FROM produtos GROUP BY fabricante_id; -- Agrupa os produtos por fabricante e soma os preços de cada um
