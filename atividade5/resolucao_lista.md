# Resolução Atividade 5 -- 2° Bimestre

## Exercício 1
```pgsql
insert into categoria (nome)
  values ('Informática');
insert into categoria (nome)
  values ('Escritório');
insert into categoria (nome)
  values ('Eletrônicos');
insert into categoria (nome)
  values ('Acessórios');
insert into categoria (nome)
  values ('Games');
```

| id_categoria | nome        |
| ------------ | ----------- |
| 1            | Informática |
| 2            | Escritório  |
| 3            | Eletrônicos |
| 4            | Acessórios  |
| 5            | Games       |

## Exercício 2
```pgsql
insert into produto (nome, preco, estoque, id_categoria)
  values
    ('Notebook', 3500.00, 5, 1),
    ('Mouse', 80.00, 20, 1),
    ('Teclado', 150.00, 15, 1),
    ('Monitor', 1200.00, 8, 3),
    ('Impressora', 900.00, 4, 2),
    ('Caderno', 25.00, 50, 2),
    ('Headset', 250.00, 12, 4),
    ('Controle', 300.00, 10, 5);
```

## Exercício 3
```pgsql
insert into produto (nome, preco, id_categoria)
  values
    ('Webcam', 180.00, 1),
    ('Cabo HDMI', 35.00, 4);

select *
from produto;
```

| id_produto | nome       | preco   | estoque | id_categoria |
| ---------- | ---------- | ------- | ------- | ------------ |
| 1          | Notebook   | 3500.00 | 5       | 1            |
| 2          | Mouse      | 80.00   | 20      | 1            |
| 3          | Teclado    | 150.00  | 15      | 1            |
| 4          | Monitor    | 1200.00 | 8       | 3            |
| 5          | Impressora | 900.00  | 4       | 2            |
| 6          | Caderno    | 25.00   | 50      | 2            |
| 7          | Headset    | 250.00  | 12      | 4            |
| 8          | Controle   | 300.00  | 10      | 5            |
| 9          | Webcam     | 180.00  | 0       | 1            |
| 10         | Cabo HDMI  | 35.00   | 0       | 4            |

 - O valor atribuído ao estoque foi 0, pois a coluna `estoque` tem default 0 e como não foi informado na inserção usa o valor padrão

## Exercício 4

### a)
```pgsql
select *
from produto;
```

### b)
```pgsql
select *
from categoria;
```

### c)
```pgsql
select nome, preco
from produto;
```

### d)
```pgsql
select nome, estoque
from produto;
```

## Exercício 5
```pgsql
select
  nome as produto,
  preco as valor_unitario,
  estoque as quantidade_disponivel
from produto;
```

| produto    | valor_unitario | quantidade_disponivel |
| ---------- | -------------- | --------------------- |
| Notebook   | 3500.00        | 5                     |
| Mouse      | 80.00          | 20                    |
| Teclado    | 150.00         | 15                    |
| Monitor    | 1200.00        | 8                     |
| Impressora | 900.00         | 4                     |
| Caderno    | 25.00          | 50                    |
| Headset    | 250.00         | 12                    |
| Controle   | 300.00         | 10                    |
| Webcam     | 180.00         | 0                     |
| Cabo HDMI  | 35.00          | 0                     |

## Exercício 6

### a)
```pgsql
select *
from produto
order by nome;
```

### b)
```pgsql
select *
from produto
order by preco desc;
```

### c)
```pgsql
select *
from produto
order by estoque asc;
```

### d)
```pgsql
select *
from produto
order by id_produto desc;
```

* `ASC` ordena dde forma crescente e `DESC` ordena de forma decrescente.

## Exercício 7

### a)
```pgsql
select *
from produto
order by nome
limit 5;
```

### b)
```pgsql
select *
from produto
order by preco desc
limit 3;
```

### c)
```pgsql
select *
from produto
order by estoque
limit 4;
```

## Exercício 8

### a)
```pgsql
select *
from produto
where preco > 500;
```

### b)
```pgsql
select *
from produto
where preco < 100;
```

### c)
```pgsql
select *
from produto
where estoque = 10;
```

### d)
```pgsql
select *
from produto
where estoque >= 15;
```

### e)
```pgsql
select *
from produto
where preco != 150;
```

## Exercício 9

### a)
```pgsql
select *
from produto
where preco > 100 and estoque > 10;
```

### b)
```pgsql
select *
from produto
where preco < 50 or preco > 1000;
```

### c)
```pgsql
select *
from produto
where estoque >= 5 and estoque <= 15;
```

### d)
```pgsql
select *
from produto
where preco > 200 and estoque < 10;
```

## Exercício 10

### a)
```pgsql
select *
from produto
where nome like 'M%';
```

### b)
```pgsql
select *
from produto
where nome like '%o';
```

### c)
```pgsql
select *
from produto
where nome like '%book%';
```

### d)
```pgsql
select *
from produto
where nome ilike '%a%';
```

* `LIKE` diferencia maiúsculas de minúsculas enquanto o `ILIKE` ignora essa 
diferença.

## Exercício 11

### a)
```pgsql
update produto
set preco = 95.00
where id_produto = 2;

select *
from produto
where id_produto = 2;
```

| id_produto | nome  | preco | estoque | id_categoria |
| ---------- | ----- | ----- | ------- | ------------ |
| 2          | Mouse | 95.00 | 20      | 1            |

### b)
```pgsql
update produto
set estoque = 8
where id_produto = 1;

select *
from produto
where id_produto = 1;
```

| id_produto | nome     | preco   | estoque | id_categoria |
| ---------- | -------- | ------- | ------- | ------------ |
| 1          | Notebook | 3500.00 | 8       | 1            |

### c)
```pgsql
update produto
set preco = 175.00
where id_produto = 3;

select *
from produto
where id_produto = 3;
```

| id_produto | nome    | preco  | estoque | id_categoria |
| ---------- | ------- | ------ | ------- | ------------ |
| 3          | Teclado | 175.00 | 15      | 1            |

### d)
```pgsql
update produto
set nome = 'Controle sem fio'
where id_produto = 8;

select *
from produto
where id_produto = 8;
```

| id_produto | nome             | preco  | estoque | id_categoria |
| ---------- | ---------------- | ------ | ------- | ------------ |
| 8          | Controle sem fio | 300.00 | 10      | 5            |

## Exercício 12
```pgsql
update produto
set preco = 1350.00,
    estoque = 12
where id_produto = 4;

select *
from produto
where id_produto = 4;
```

| id_produto | nome    | preco   | estoque | id_categoria |
| ---------- | ------- | ------- | ------- | ------------ |
| 4          | Monitor | 1350.00 | 12      | 3            |

## Exercício 13
```pgsql
update produto
set preco = preco * 1.10
where id_categoria = 1;

select *
from produto
where id_categoria = 1;
```

| id_produto | nome     | preco   | estoque | id_categoria |
| ---------- | -------- | ------- | ------- | ------------ |
| 9          | Webcam   | 198.00  | 0       | 1            |
| 2          | Mouse    | 104.50  | 20      | 1            |
| 1          | Notebook | 3850.00 | 8       | 1            |
| 3          | Teclado  | 192.50  | 15      | 1            |

## Exercício 14
```pgsql
update produto
set estoque = estoque + 5
where estoque < 10;

select *
from produto
order by id_produto;
```

| id_produto | nome             | preco   | estoque | id_categoria |
| ---------- | ---------------- | ------- | ------- | ------------ |
| 1          | Notebook         | 3850.00 | 13      | 1            |
| 2          | Mouse            | 104.50  | 20      | 1            |
| 3          | Teclado          | 192.50  | 15      | 1            |
| 4          | Monitor          | 1350.00 | 12      | 3            |
| 5          | Impressora       | 900.00  | 9       | 2            |
| 6          | Caderno          | 25.00   | 50      | 2            |
| 7          | Headset          | 250.00  | 12      | 4            |
| 8          | Controle sem fio | 300.00  | 10      | 5            |
| 9          | Webcam           | 198.00  | 5       | 1            |
| 10         | Cabo HDMI        | 35.00   | 5       | 4            |

## Exercício 15

### a)
```pgsql
delete from produto
where id_produto = 9;
```

### b)
```pgsql
delete from produto
where id_produto = 10;
```

### c)
```pgsql
select *
from produto;
```

| id_produto | nome             | preco   | estoque | id_categoria |
| ---------- | ---------------- | ------- | ------- | ------------ |
| 1          | Notebook         | 3850.00 | 13      | 1            |
| 2          | Mouse            | 104.50  | 20      | 1            |
| 3          | Teclado          | 192.50  | 15      | 1            |
| 4          | Monitor          | 1350.00 | 12      | 3            |
| 5          | Impressora       | 900.00  | 9       | 2            |
| 6          | Caderno          | 25.00   | 50      | 2            |
| 7          | Headset          | 250.00  | 12      | 4            |
| 8          | Controle sem fio | 300.00  | 10      | 5            |

* delete from produto sem where excluiria todos os registros da tabela
produto, ainda teria uma tabela, mas ela estaria vazia.

## Exercício 16
```pgsql
insert into produto (nome, preco, estoque, id_categoria)
  values
    ('Pen Drive', 40.00, 0, 1),
    ('Mouse pad', 20.00, 0, 4);

select *
from produto
where estoque = 0;
```

| id_produto | nome      | preco | estoque | id_categoria |
| ---------- | --------- | ----- | ------- | ------------ |
| 11         | Pen Drive | 40.00 | 0       | 1            |
| 12         | Mouse pad | 20.00 | 0       | 4            |

```pgsql
delete from produto
where estoque = 0;

select *
from produto;
```

| id_produto | nome             | preco   | estoque | id_categoria |
| ---------- | ---------------- | ------- | ------- | ------------ |
| 1          | Notebook         | 3850.00 | 13      | 1            |
| 2          | Mouse            | 104.50  | 20      | 1            |
| 3          | Teclado          | 192.50  | 15      | 1            |
| 4          | Monitor          | 1350.00 | 12      | 3            |
| 5          | Impressora       | 900.00  | 9       | 2            |
| 6          | Caderno          | 25.00   | 50      | 2            |
| 7          | Headset          | 250.00  | 12      | 4            |
| 8          | Controle sem fio | 300.00  | 10      | 5            |

## Exercício 17
```pgsql
delete from categoria
where id_categoria = 1;
```

* a) Não permitiu a exclusão (erro de violação de chave estrangeira).
* b) `fk_produto_categoria`.
* c) Ainda existem produtos que referenciam a categoria, se ela fosse excluida teria produtos apontando para uma categoria inexistente.
* d) Excluindo ou movendo os produtos da categoria outra, e só depois excluir a categoria.

## Exercício 18

1. 
```pgsql
update produto
set estoque = estoque + 10
where id_produto = 1;
```

2. 
```pgsql
update produto
set estoque = estoque - 3
where id_produto = 2;
```

3. 
```pgsql
update produto
set preco = preco * 1.05
where id_produto = 5;
```

4. 
```pgsql
delete from produto
where id_produto = 6;
```

5. 
```pgsql
select *
from produto
where estoque < 10;
```

## Exercício 19
```pgsql
select nome, preco, estoque
from produto
where preco between 100 and 1000
  and estoque > 5
order by preco desc
limit 5;
```
