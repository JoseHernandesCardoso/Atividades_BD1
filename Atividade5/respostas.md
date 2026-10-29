# Parte 1

## Exercício 1:

a) id_curso, nome_curso e coordenador saão armazenados de forma repetida

b) Modificar algum dos dados repetidos exige modificar varias linhas. Não é possível adicionar um curso sem um aluno. Apagar o último aluno de um curso apaga o curso junto.

c) Varias linhas deveriam ser modificas junto.

d) O curso é apagado junto.

e) Não é possível, pois os dados de um curso são completamente dependentes de um aluno para existir.

f) Aluno e curso podem existir de forma separada.

## Exercício 2:

a) Não é possível inserir um departamento sem inserir um funcionário junto

b) Editar o gerente de um departamento exige atualizar várias linhas.

c) Se o último funcionário de um departamento for excluído, o departamento também será excluido.

d) id_funcionário, nome_funcionário, salário

e) id_departamento, nome_departamento, gerente_departamento

f) Separar a tabela de funcionário da tabela de departamento de forma que essa segunda seja independente e a primeira possua uma FK indicando a que departamento o funcionário pertence.

# Parte 2

## Exercicio 3:

a) id_produto

b)

    id_produto -> nome_produto
    id_produto -> preco
    id_categoria -> nome_categoria

c) O identificador do produto não determina o nome da categoria. Quem determina qual o nome da categoria é o identificador da categoria

d) o id da categoria não determina o nome de um produto. O responsável por essa determinação é o id do produto.

e) id_produto -> id_categoria -> nome_categoria

f) O problema de normalização presente na tabela quebra a segunda forma normal. Sendo assim, existem atributos não-primos que dependem apenas de id_categoria ou apenas de id_produto.

## Exercício 4:

a) id_aluno e cpf

b) id_aluno

c) id_aluno e cpf

d) nome e e-mail

e) Ele pode ajudar a identificar uma linha de forma única, seja sozinho ou combinado com outro primo. Entretanto, como a chave primária é única, apenas um primo (e que não dependa de outros para sua função) pode ser eleito como tal.

f)

```sql
ALUNO(
    id_aluno INT PRIMARY KEY,
    cpf VARCHAR(13) KEY,
    nome VARCHAR(80),
    email VARCHAR(50)
)
```

# Parte 3

## Exercício 5: