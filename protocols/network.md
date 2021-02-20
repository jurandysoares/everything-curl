## Rede simplificada

Rede significa comunicação entre dois terminais na Internet. A Internet é apenas um monte de máquinas interconectadas (computadores, na verdade), cada uma usando seus próprios endereços privados (chamados [endereços IP](https://pt.wikipedia.org/wiki/Endere%C3%A7o_IP)). Os endereços de cada máquina podem ser de tipos diferentes e as máquinas podem até ter endereços temporários. Esses computadores costumam ser chamados de hosts.

O computador, tablet ou telefone que você está sentado em frente é geralmente chamado de "o cliente" e a máquina em algum lugar com a qual você deseja trocar dados é chamada de "servidor". A principal diferença entre o cliente e o servidor está nas funções que eles desempenham aqui. Não há nada que impeça as funções de serem invertidas em uma operação subsequente.

### Qual máquina

Quando você deseja iniciar uma transferência para uma das máquinas lá fora (um servidor), você geralmente não sabe seus endereços IP, mas em vez disso, geralmente sabe seu nome. O nome da máquina com a qual você vai falar está embutido na URL com a qual você trabalha quando usa o curl.

Você pode usar um URL como "http://example.com/index.html", o que significa que você se conectará e se comunicará com o host chamado example.com.

### Resolução de nome de host

Depois de saber o nome do host, precisamos descobrir quais endereços IP esse host possui para que possamos contatá-lo.

A conversão do nome em um endereço IP costuma ser chamada de 'resolução de nomes'. O nome é "resolvido" para um ou um conjunto de endereços. Isso geralmente é feito por um "servidor DNS", o DNS sendo como uma grande tabela de pesquisa que pode converter nomes em endereços - todos os nomes na Internet, na verdade. Normalmente, seu computador já conhece o endereço de um computador que executa o servidor DNS, pois isso faz parte da configuração da rede.

curl irá, portanto, perguntar ao servidor DNS: "Olá, por favor me dê todos os endereços de example.com", e o servidor responderá com uma lista deles. Ou no caso de você digitar o nome errado, ele pode responder que o nome não existe.

### Estabeleça uma conexão

Com uma lista de endereços IP para o host que o curl deseja contatar, o curl envia uma "solicitação de conexão". A conexão que o curl  deseja estabelecer é chamado de TCP ([Transmission Control Protocol](https://pt.wikipedia.org/wiki/Transmission_Control_Protocol)) e funciona de forma semelhante à conexão de um string invisível entre dois computadores. Uma vez estabelecido, ele pode ser usado para enviar um fluxo de dados em ambas as direções.

Conforme curl obtém uma lista de endereços para o host, ele irá percorrer essa lista de endereços ao se conectar e, no caso de um falhar, tentará se conectar ao próximo até que um funcione ou todos falhem.

### Conecta-se a "números de porta"

Ao se conectar com TCP a um servidor remoto, um cliente seleciona em qual número de porta fazer isso. Um número de porta é apenas um local dedicado para um serviço específico, o que permite que o mesmo servidor ouça outros serviços em outros números de porta ao mesmo tempo.

Os protocolos mais comuns têm números de porta padrão que os clientes e servidores usam. Por exemplo, ao usar o URL "http://example.com/index.html", esse URL especifica um esquema chamado "http" que informa ao cliente que ele deve tentar a porta TCP de número 80 no servidor por padrão. O URL pode opcionalmente fornecer outro número de porta personalizado, mas se nada de especial for especificado, ele usará a porta padrão para o esquema usado no URL.

### TLS

Depois que a conexão TCP for estabelecida, muitas transferências exigirão que ambos os lados negociem um nível de segurança melhor antes de continuar, e isso geralmente é TLS: Segurança da camada de transporte (*Transport Layer Security* em inglês). Se isso for usado, o cliente e o servidor farão um aperto de mãos (*handshake* em inglês) TLS primeiro e só continuarão se tiver êxito.

### Transferir dados

Quando a "string" de conexão que chamamos de TCP é anexada ao computador remoto (e fizemos o possível aperto de mãos adicional do TLS), há uma conexão estabelecida entre as duas máquinas e essa conexão pode então ser usada para trocar dados. Essa comunicação é feita por meio de um "protocolo", conforme discutido no capítulo seguinte.

Tradicionalmente, o que é chamado de *download* (baixar, descarregar) é quando os dados são transferidos de um servidor para um cliente e, inversamente, um *upload* (subir, carregar) é quando os dados são transferidos do cliente para o servidor. O cliente está aqui. O servidor está lá em cima.