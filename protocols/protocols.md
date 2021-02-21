## Protocolo

A linguagem usada para solicitar o envio de dados - em qualquer direção - é chamada de **protocolo**. O protocolo descreve exatamente como solicitar dados ao servidor ou informar ao servidor que há dados chegando.

Os protocolos são normalmente definidos pelo IETF ([Internet Engineering Task Force](https://www.ietf.org/)), que hospeda documentos RFC que descrevem exatamente como cada protocolo funciona: como os clientes e servidores devem agir e o que enviar e assim por diante.

## Quais protocolos o curl suporta?

curl suporta protocolos que permitem "transferências de dados" em uma ou ambas as direções. Normalmente também nos restringimos a protocolos que têm um "formato URI" descrito em um RFC ou que é pelo menos amplamente usado, já que curl funciona principalmente com URLs (URIs na verdade) como a chave de entrada que especifica a transferência.

O curl mais recente (no momento desta escrita) oferece suporte a estes protocolos:

DICT, FILE, FTP, FTPS, GOPHER, GOPHERS, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS,
MQTT, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, TELNET, TFTP

Para complicar ainda mais, os protocolos geralmente existem em diferentes versões ou sabores também.

## Que outros protocolos existem?

O mundo está cheio de protocolos, antigos e novos. Protocolos antigos são abandonados e descartados, e novos são introduzidos. Nunca existe um estado de estabilidade, mas a situação muda dia a dia e ano a ano. Você pode ter certeza de que haverá novos protocolos adicionados à lista acima no futuro e que haverá novas versões dos protocolos já listados.

É claro que já existem outros protocolos que curl ainda não suporta. Estamos abertos para oferecer suporte a mais protocolos que atendam aos paradigmas gerais de curl, só precisamos que os desenvolvedores escrevam os ajustes de código necessários para eles.


## Como os protocolos são desenvolvidos?

Ambas as novas versões de protocolos existentes e protocolos inteiramente novos são geralmente desenvolvidos por pessoas ou equipes que acham que os existentes não são bons o suficiente. Algo sobre eles os torna inadequados para um caso de uso específico ou talvez tenha surgido alguma ideia nova que possa ser aplicada para melhorar as coisas.

Claro, nada impede ninguém de desenvolver um protocolo inteiramente por conta própria e prazer em seu quintal, mas os principais protocolos são levados geralmente para o IETF em um estágio bastante inicial, onde são então discutidos, refinados, debatidos e polidos e então, eventualmente, idealmente, se tornam um documento RFC publicado.

Os desenvolvedores de software então leem as especificações RFC e implantam seu código no mundo inteiro com base em suas interpretações das palavras nesses documentos. Às vezes acontece que algumas das especificações estão sujeitas a interpretações muito diferentes ou às vezes os engenheiros são apenas preguiçosos e ignoram os bons conselhos nas especificações e implantam algo que não aderem. Escrever software que interopera com outras implementações das especificações pode, portanto, acabar sendo um trabalho árduo.

## Quanto os protocolos mudam?

Como o software, as especificações do protocolo são atualizadas com frequência e novas versões do protocolo são criadas.

A maioria dos protocolos permite algum nível de extensibilidade que faz com que novas extensões apareçam com o tempo, extensões cujo suporte faz sentido.

A interpretação de um protocolo às vezes muda, mesmo se as especificações permanecerem as mesmas.

Os protocolos mencionados neste capítulo são todos "Protocolos da camada de aplicação", o que significa que são transferidos por meio de protocolos de nível mais baixo, como TCP, UDP e TLS. Eles também são protocolos que mudam com o tempo, obtêm novos recursos e são atacados, de forma que novas formas de lidar com a segurança etc. obrigam o curl a se adaptar e mudar.

## Sobre aderir aos padrões e quem está certo

Geralmente, existem especificações de protocolo que nos dizem como enviar e receber dados para protocolos específicos. As especificações de protocolo que seguimos são RFCs reunidas e publicadas pela IETF.

Alguns protocolos não estão devidamente documentados em uma RFC final, como, por exemplo, o SFTP, para o qual nossa implementação é baseada em um rascunho da Internet que não é o último disponível.

Os protocolos são, no entanto, falados por duas partes e, como em qualquer conversa, existem dois lados de compreensão de algo ou interpretando as instruções dadas em uma especificação. Além disso, muito software de rede é escrito sem os autores prestando muita atenção à especificação, então eles acabam fazendo alguns atalhos, ou talvez eles apenas interpretam o texto de maneira diferente. Às vezes, mesmo erros e bugs fazem software se comportar de maneiras que não são mandadas pela especificação e às vezes até francamente proibidas nas especificações.

No projeto Curl, usamos as especificações publicadas como regras sobre como atuar até aprender qualquer outra coisa. Se as implementações alternativas populares atuam diferentemente do que o que achamos que a especificação diz e esse comportamento alternativo é o que funciona amplamente na grande Internet, então as chances são que vamos mudar e, em vez disso, decidir agir como os outros. Se um servidor se recusar a falar conosco quando achamos que seguimos a especificação, mas funciona bem quando quebramos ligeiramente as regras, provavelmente acabamos quebrando-as exatamente dessa maneira - se ainda pudemos trabalhar com sucesso com outras implementações.

Em última análise, é uma decisão pessoal e passível de discussão em todos os casos em que pensamos que uma especificação e o mundo real não se alinham.

Nos piores casos, introduzimos opções para permitir que os desenvolvedores de aplicativos e os usuários da Curl tenham a palavra final sobre o que o curl deve fazer. Eu digo pior porque muitas vezes é muito difícil pedir aos usuários tomar essas decisões, pois geralmente envolve detalhes complicados e estranheza acontecendo e é muita coisa para pergunta aos usuários. Devemos sempre fazer o nosso melhor para evitar levar tais decisões de protocolo para os usuários.
