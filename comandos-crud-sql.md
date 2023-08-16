# Comandos para operações CRUD no Banco de dados

## Resumo

- C -> **CREATE** (inserir dados usando o comando `INSERT`)
- R -> **READ** (ler dados usando o comando `SELECT`)
- U -> **UPDATE** (atualizar dados usando o comando `UPDATE`)
- D -> **DELETE** (deletar dados usando o comando `DELETE`)

## CREATE

### INSERT

```sql
INSERT INTO fabricantes (nome) VALUES ('Asus');
INSERT INTO fabricantes (nome) VALUES ('Dell');
INSERT INTO fabricantes (nome) VALUES ('Apple');

INSERT INTO fabricantes (nome) VALUES ('LG'), ('Samsung'), ('Brastemp');
INSERT INTO fabricantes (nome) VALUES ('Positivo'), ('Microsoft');
```