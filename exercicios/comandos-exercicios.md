## Criando banco de dados

```sql
CREATE DATABASE catalogo_filmes CHARACTER SET utf8mb4;
```

## Criando tabelas

```sql
CREATE TABLE filme (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45) NOT NULL,
    ano YEAR(4) NOT NULL,
    genero_id INT NOT NULL
);
```

```sql
CREATE TABLE genero (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

## Relacionando as tabelas filme e genero

```sql
ALTER TABLE filme
    ADD CONSTRAINT fk_filme_genero
    FOREIGN KEY (genero_id) REFERENCES genero(id);
```