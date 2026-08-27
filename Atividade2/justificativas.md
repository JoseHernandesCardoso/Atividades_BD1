1. Decidiu-se criar uma generalização dos funcionários, para haver a possibilidade
    de representar outros tipos e aumentar a escalabilidade na necessidade se especificar
    novos tipos de funcionário no sistema.

2. Optou-se por criar uma entidade excluisiva para os serviços, visto que cada serviço realizado
    possui suas próprias caracteristicas, como preço, descrição e tipo. Sendo assim, o serviço
    representado não é um realizado, mas um modelo de um serviço que pode ser requirido por uma
    ordem de serviço.

3. A associação entre mecânico, serviço e ordem de serviço foi feita usando um relacionamento  
    ternário, pois uma ordem de serviço diversos serviços e requer mecânicos para realizar os
    serviços solicitados.

4. A peça foi modelada em forma de uma entidade, pois cada peça possui dados próprios intrincicos,
    como descrição, fabricante e valor de referência, entretanto peças similares possui as mesmas
    caracteristicas, por isso há um código único que agrupa essas peças similares que podem ser
    utilizadas em diversas ordens de serviço

5.  - Cada cliente possui um ou mais veículos, mas cada veículo só pode estar relacionado a um ou
    nenhum cliente
    - Cada veículo pode estar relacionado a várias ordens de serviço, mas uma ordem de serviço só
    pode estar relacionada a um veículo
    - Cada ordem de serviço pode requerer vários serviços e mecânicos, cada mecânico pode estar
    envolvida em várias ordem se serviço e tipos de serviço, cada serviço pode ser requisitado por
    várias ordens de serviço e feito por vários mecânicos
    - Cada ordem de serviço pode usar ou não uma ou várias peças, e cada peça pode ter sido usada
    ou não em um ou vários serviços 