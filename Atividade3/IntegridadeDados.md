# 1 - Pesquisa

### O que é Integridade de Dados?

> Integridade de dados é a garantida de que os dados armazenados
sempre serão confiáveis, completos e precisos. Sendo assim, esses
dados devem ser protegidos contra perdas, vazamentos, corrupção
ou mudanças indesejadas no geral.

### O que é Integridade de Entidade?

> É a segurança que entidades de um banco de dados devem possuir
para garantir a não duplicação de dados e o preenchimento correto
de campos de acordo com o dado que eles representam, por meio de
chaves de identificação e e valores exclusivos.

### O que é Integridade Referencial?

> São sistemas de segurança que buscam proteger a consistência das
referências entre tabelas diferentes, ou seja, que garantem que
as referências a dados de outras tabelas sempre indiquem um
conteúdo existente e correto, além de não permitir registros
órfãos desnecessários (caso os registros que dependiam dele sejam
apagados e não há sentido em mante-lo sozinho).

### O que é Integridade de Domínio?

> É o sistema de proteção que garante que os dados de uma coluna
de uma tabela sempre representaram os dados de forma correta
dentro do formato determinado. Ou seja, é a segurança que evita
que dados fora do domínio (conjunto de valores válidos possíveis)
existam nos registros. 

# 2 - Banco Problemático

### Problemas no Banco

| Problema encontrado | Por que é um problema? | Tipo de integridade | Regra que deveria existir |
|----------------------|------------------------|---------------------|---------------------------|
| Cliente não possui nome | Os dados não estão completos | Domínio | O campo Nome em Cliente deve ser obrigatório e não vazio |
| Produto não possui nome | Os dados não estão completos | Domínio | O campo Nome em Produto deve ser obrigatório e não vazio |
| Preço em produto é negativo | Não existe preço negativo | Domínio | O campo Preço em Produto deve ser maior ou igual a zero |
| Estoque em produto é negativo | Contágens não são negativas | Domínio | O campo Estoque em Produto deve ser meior igual a zero |
| Valor em pedido é negativo | Não existe preço negativo | Domínio | O campo Valor em Pedido deve ser maior ou igual a zero |
| idCliente em Pedido referencia um cliente que não existe | O pedido está referenciando um cliente inválido | Referencial | O campo idClente em Pedido só pode referenciar um cliente válido em Cliente |
| Existem dois clientes com o mesmo ID | Referenciais únicos estão duplicados | Entidade | Os IDs em Cliente devem ser únicos |
| Existem dois clientes com o mesmo e-mail | Atributos possivelmente únicos podem estar duplicados | Entidade | E-mails devem der únicos em Cliente |
| Um pedido está sem data | Dado importante de rastreio faltando | Domínio | O campo data em Pedido deve ser obrigatório |

# 3 - Definição de Regras

[ E ] R01 - Todo cliente deve possuir um ID único como chave primária

[ D ] R02 - Os IDs dos clientes devem ser maiores que zero

[ E ] R03 - Todo cliente deve possuir um nome

[ E ] R04 - Todo cliente deve possuir um email único

[ E ] R05 - Todo produto deve possuir um ID único como chave primária

[ D ] R06 - Os IDs dos produtos devem ser maiores que zero

[ E ] R07 - Todo produto deve possuir um nome

[ E ] R08 - Todo produto deve possuir um preço

[ E ] R09 - Todo produto deve possuir sua quantidade em estoque

[ E ] R10 - Todo pedido deve possuir um ID único como chave primária

[ D ] R11 - Os IDs dos pedidos devem ser maiores que zero

[ E ] R12 - Todo pedido deve possuir uma data

[ E ] R13 - Todo pedido deve possuir um valor

[ E ] R14 - Todo pedido deve referenciar um ID de um cliente

[ R ] R15 - Os IDs dos clientes referenciados nos pedidos devem corresponder a um cliente existente

[ D ] R16 - Todos os preços devem ser não negativos

# 4 - Pesquisa 2

` PRIMARY KEY ` - Define um campo como sendo a chave primária de referência dos elementos. Ela é única e não nula. Útil para diferenciarmos registros similares e referenciarmos registros específicos.

` FOREIGN KEK ` - Difine um campo como uma chave estrangeira, ou seja, como uma referência a um registro de uma outra tabela, onde essa referência é uma chave primária do registro referenciado. Útil para conectarmos dados entre tabelas.

` NOT NULL ` - Define um campo como não nulo, obrigando seu preenchimento sempre. Útil para garantir que informações cruciais sempre estejam presentes.

` UNIQUE ` - Define um campo como único, garantindo que nenhum registro tenha esse campo com o mesmo valor. Útil quando dados de um campo não podem se repetir em múltiplos registros.

` CHECK ` - Impõe uma verificação em um campo e só permite que dados sejam registrados nele se seguirem as condições impostas por ele. Útil para garantir que os valores de um campo sempre pertencerão ao domínio esperado.

` DEFAULT ` - Define um valor padrão para um campo caso ele não seja preenchido. Útil para garantir que campos núnca fiquem vazios.

# 5 - Conexões


| Necessidade | Mecanismo que você utilizaria |
|------------|-------------------------------|
| Identificar cada cliente de maneira única | ` PRIMARY KEY ` |
| Impedir um cliente sem nome | ` NOT NULL ` |
| Impedir dois clientes com o mesmo e-mail | ` UNIQUE ` |
| Impedir preço negativo | ` CHECK ` |
| Garantir que um pedido pertença a um cliente existente | ` FOREIGN KEY ` |
| Fazer um produto iniciar com estoque zero quando nenhum valor for informado | ` DEFAULT ` |

> Os mecânismos pesquisados na etapa anterior são ferramentas para garantir a integridade do banco de dados.