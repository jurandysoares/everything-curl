# Os protocolos que curl suporta

curl suporta cerca de 22 protocolos. Dizemos "cerca de" porque depende de como você conta e do que considera serem protocolos claramente diferentes.

## DICT

DICT é um protocolo de rede de dicionário, que permite aos clientes perguntar aos servidores de dicionário sobre o significado ou explicação das palavras. Consulte a [RFC 2229](https://tools.ietf.org/html/rfc2229). Os servidores e clientes Dict usam a porta 2628 do TCP.

## FILE

FILE não é realmente um protocolo de "rede".s É um esquema de URL que permite que você diga ao curl para obter um arquivo do sistema de arquivos local em vez de obtê-lo pela rede de um servidor remoto. Consulte a [RFC 1738](https://tools.ietf.org/html/rfc1738).

## FTP

FTP significa Protocolo para Transferência de Arquivo (*File Transfer Protocol* em inglês) e é uma forma antiga (originada no início dos anos 1970) de transferir arquivos para lá e para cá entre um cliente e um servidor. Consulte a [RFC 959](https://tools.ietf.org/html/rfc959). Ela foi bastante ampliada ao longo dos anos. Os servidores e clientes FTP usam a porta 21 do TCP e mais uma porta, embora a segunda seja geralmente estabelecida dinamicamente durante a comunicação.

Veja a página externa [FTP vs HTTP](https://daniel.haxx.se/docs/ftp-vs-http.html) para saber como ele difere do HTTP.

## FTPS

FTPS significa Protocolo de Transferência de Arquivo Seguro (*Secure File Transfer Protocol* em inglês). Ele segue a tradição de adicionar um 'S' ao nome do protocolo para significar que o protocolo é feito como o FTP normal, mas com uma camada de segurança SSL/TLS adicionada. Consulte a [RFC 4217](https://tools.ietf.org/html/rfc4217).

Este protocolo é problemático para uso em firewalls e outros equipamentos de rede.

## GOPHER

Projetado para "distribuir, pesquisar e recuperar documentos pela Internet", Gopher é um pouco o avô do HTTP, já que o HTTP assumiu completamente o controle dos mesmos casos de uso. Consulte a [RFC 1436](https://tools.ietf.org/html/rfc1436). Os servidores e clientes Gopher usam a porta TCP 70.

## GOPHERS

É Gopher sobre TLS. Uma extensão recente do protocolo muito antigo.

## HTTP

O protocolo de transferência de hipertexto, HTTP, é o protocolo mais amplamente usado para transferência de dados na web e na Internet. Consulte a [RFC 7230](https://tools.ietf.org/html/rfc7230) para HTTP/1.1 e [RFC 7540](https://tools.ietf.org/html/rfc7540) para [HTTP/2](http-http2.md). Os servidores e clientes HTTP usam a porta 80 do TCP.

## HTTPS

O HTTP seguro é HTTP feito por meio de uma conexão SSL/TLS. Veja [RFC 2818](https://tools.ietf.org/html/rfc2818). Servidores e clientes HTTPS usam a porta 443 do TCP, a menos que falem [HTTP/3](http-http3.md) que então usa QUIC e é feito sobre UDP ...

## IMAP

O Protocolo de Acesso a Mensagens da Internet (*Internet Message Access Protocol* em inglês), IMAP, é um protocolo para acessar, controlar e "ler" e-mail. Consulte a [RFC 3501](https://tools.ietf.org/html/rfc3501). Os servidores e clientes IMAP usam a porta 143 do TCP. Enquanto as conexões com o servidor começam como texto não criptografado, a comunicação SSL/TLS pode ser suportada pelo cliente solicitando explicitamente a atualização da conexão usando o comando `STARTTLS`. Consulte a [RFC 2595](https://tools.ietf.org/html/rfc2595).

## IMAPS

IMAP seguro é IMAP feito por meio de uma conexão SSL/TLS. Essas conexões começam implicitamente usando SSL/TLS e, dessa forma, servidores e clientes usam a porta 993 do TCP para se comunicarem entre si. Consulte a [RFC 8314](https://tools.ietf.org/html/rfc8314).

## LDAP

O Protocolo Leve para Acesso a Diretório (*Lightweight Directory Access Protocol* em inglês), LDAP, é um protocolo para acessar e manter informações de diretório distribuídas. Basicamente, uma pesquisa de banco de dados. Consulte a [RFC 4511](https://tools.ietf.org/html/rfc4511). Os servidores e clientes LDAP usam a porta 389 do TCP.

## LDAPS

O LDAP seguro é o LDAP feito por meio de uma conexão SSL/TLS.

## MQTT

O Transporte de Telemetria de Enfileiramento de Mensagens (*Message Queuing Telemetry Transport* em inglês), MQTT é um protocolo comumente usado em sistemas de Internet das Coisas (*IoT* em inglês) para troca de dados envolvendo principalmente dispositivos menores. É um protocolo denominado de "publicação-assinatura".

## POP3

O Protocolo Postal (*Post Office Protocol* em inglês) versão 3 (POP3) é um protocolo para recuperar e-mail de um servidor. Veja [RFC 1939](https://tools.ietf.org/html/rfc1939). Os servidores e clientes POP3 usam a porta 110 do TCP. Embora as conexões com o servidor comecem como texto não criptografado, a comunicação SSL/TLS pode ser suportada pelo cliente solicitando explicitamente a atualização da conexão usando o comando `STLS`. Consulte a [RFC 2595](https://tools.ietf.org/html/rfc2595).

## POP3S

O POP3 seguro é feito POP3 em uma conexão SSL/TLS.Essas conexões são implicitamente iniciadas usando SSL/TLs e, como tal servidores e clientes usam a porta 995 do TCP para se comunicar entre si. Veja [RFC 8314](https://tools.ietf.org/html/rfc8314).

## RTMP

O Protocolo de Mensagens em Tempo Real (*Real-Time Messaging Protocol* em inglês) (RTMP) é um protocolo usado para transmitir áudio, vídeo e dados. Servidores e clientes RTMP usam a porta 1935 do TCP.

## RTSP

O Protocolo de Transmissão em Tempo Real (*Real Time Streaming Protocol*) (RTSP) é um protocolo de controle de rede para controlar servidores de *streaming* (fluxo) de mídia. Consulte a [RFC 2326](https://tools.ietf.org/html/rfc2326). Os servidores e clientes RTSP usam a porta 554 do TCP e do UDP.

## SCP

O protocolo de cópia segura (*Secure Copy Protocolo* em inglês) (SCP) é projetado para copiar arquivos de e para um servidor SSH remoto. Servidores e clientes SCP usam a porta 22 do TCP.

## SFTP

O Protocolo de Transferência de Arquivos via SSH (*SSH File Transfer Protocol* em inglês) (SFTP), que fornece acesso e gerenciamento de arquivos em um fluxo de dados confiável. Os servidores e clientes SFTP usam a porta 22 do TCP.

## SMB

O Protocolo Bloco de Mensagens do Servidor (*Server Message Block* em inglês) (SMB) também é conhecido como CIFS. É um protocolo de rede de camada de aplicação usado principalmente para fornecer acesso compartilhado a arquivos, impressoras e portas seriais e comunicações diversas entre nós em uma rede. Os servidores e clientes SMB usam a porta 445 TCP.

## SMTP

O Protocolo Simples de Transferência de Correio (*Simple Mail Transfer Protocol* em inglês) (SMTP) é um protocolo para transmissão de e-mail. Veja [RFC 5321](https://tools.ietf.org/html/rfc5321). Os servidores e clientes SMTP usam a porta 25 do TCP. Embora as conexões com o servidor comecem como texto não criptografado, a comunicação SSL/TLS pode ser suportada pelo cliente solicitando explicitamente a atualização da conexão usando o comando `STARTTLS`. Consulte a [RFC 3207](https://tools.ietf.org/html/rfc3207).

## SMTPS

O SMTP seguro, às vezes chamado de SSMTP, é o SMTP feito por meio de uma conexão SSL/TLS. Essas conexões começam implicitamente usando SSL/TLS e, dessa forma, servidores e clientes usam a porta 465 do TCP para se comunicarem entre si. Consulte a [RFC 8314](https://tools.ietf.org/html/rfc8314).

## TELNET

TELNET é um protocolo de camada de aplicação usado em redes para fornecer um recurso de comunicação orientado a texto interativo bidirecional usando uma conexão de terminal virtual. Consulte a [RFC 854](https://tools.ietf.org/html/rfc854). Os servidores e clientes TELNET usam a porta 23 do TCP.

## TFTP

O Protocolo Trivial de Transferência de Arquivos (*Trivial File Transfer Protocol* em inglês) (TFTP) é um protocolo para fazer transferências de arquivos simples sobre UDP para obter ou colocar um arquivo em um host remoto. Os servidores e clientes TFTP usam a porta 69 do UDP.
