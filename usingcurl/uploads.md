## Uploads/Carregamentos

Upload (carregamento) é um termo para enviar dados a um servidor remoto. O upload é feito de maneira diferente para cada protocolo, e vários protocolos podem até permitir maneiras diferentes de fazer upload de dados.

### Protocolos que permitem upload

Você pode fazer upload de dados usando um destes protocolos: FILE, FTP, FTPS, HTTP, HTTPS, IMAP, IMAPS, SCP, SFTP, SMB, SMBS, SMTP, SMTPS e TFTP.

### HTTP oferece vários "uploads"

O HTTP (e seu irmão mais velho, o HTTPS) fornece várias maneiras diferentes de fazer upload de dados para um servidor e o curl oferece opções de linha de comando fáceis para fazer isso das três maneiras mais comuns, descritas abaixo.

Um detalhe interessante com HTTP também é que um upload também pode ser um download, na mesma operação e de fato muitos downloads são iniciados com um HTTP POST.

#### POST (PUBLICAR)

POST é o método HTTP que foi inventado para enviar dados a um aplicativo da Web de recebimento e, por exemplo, é como funcionam os formulários HTML mais comuns na Web. Geralmente, envia um bloco de quantidades relativamente pequenas de dados ao receptor.

O tipo de upload geralmente é feito com as opções `-d` ou `--data`, mas existem algumas alterações adicionais.

Leia a descrição detalhada sobre como fazer isso com curl no capítulo [HTTP POST com curl](http-post.md).

#### Postagem de formulários de várias partes (*multipart formpost*)

A postagem de formulários com várias partes também são usados ​​em formulários HTML em sites; normalmente quando há um upload de arquivo envolvido. Este tipo de upload também é um HTTP POST, mas envia os dados formatados de acordo com algumas regras especiais, que é o que significa o nome "multipart".

Como ele envia os dados formatados de maneira completamente diferente, você não pode selecionar qual tipo de POST usar por sua própria vontade, mas depende inteiramente do que o servidor receptor espera e pode lidar.

Formulários HTTP multipartes são feitos com `-F`. Veja a descrição detalhada no capítulo [HTTP multipart formposts](http-multipart.md).

#### PUT (POR)

HTTP PUT é o método de upload projetado para enviar um recurso completo para ser colocado como está no site remoto ou até mesmo substituir um recurso existente lá. Dito isso, este também é o método de upload menos usado para HTTP na web hoje e muitos, senão a maioria, dos servidores web nem mesmo têm o PUT habilitado.

Você envia um upload HTTP usando a opção -T com o arquivo a ser enviado:

    curl -T carregue-isso http://example.com/

### uploads de FTP

Trabalhando com FTP, você consegue ver o sistema de arquivos remoto que estará acessando. Você informa ao servidor exatamente em qual diretório deseja que o upload seja colocado e qual nome de arquivo usar. Se você especificar o URL de upload com uma barra final, curl acrescentará o nome do arquivo usado localmente à URL e esse será o nome do arquivo usado quando armazenado remotamente:

    curl -T carregue-isso ftp://example.com/esse/diretorio/

Portanto, se você preferir selecionar um nome de arquivo diferente no lado remoto do que o usado localmente, especifique-o no URL:

    curl -T carregue-isso ftp://example.com/esse/diretorio/nome-remoto

Aprenda mais sobre FTP com curl na seção [Using curl/FTP](usingcurl-ftp.md).

### uploads SMTP

Você pode não considerar o envio de um e-mail para "fazer upload", mas para curl é. Você carrega o corpo da mensagem para o servidor SMTP. Com o SMTP, você também precisa incluir todos os cabeçalhos de e-mail de que precisa (Para:, De:, Data:, etc.) no corpo do e-mail, pois o curl não adicionará nenhum.

    curl -T mail smtp: //mail.example.com/ --mail-from user@example.com

Saiba mais sobre como usar SMTP com curl na seção [Usando curl/SMTP](usingcurl-smtp.md).

### Medidor de progresso para uploads

The general progress meter curl provides

O medidor de progresso genérico que o curl disponibiliza  (consulte a seção [Medidor de progresso](cmdline-progressmeter.md)) também funciona bem para uploads. O que precisa ser lembrado é que o medidor de progresso é desabilitado automaticamente quando você está enviando a saída para stdout, e a maioria dos protocolos de suporte a curl pode gerar algo até mesmo para um upload.

Portanto, você pode precisar redirecionar explicitamente os dados baixados para um arquivo (usando o redirecionamento de shell `>`, `-o` ou similar) para obter o medidor de progresso exibido para upload.

### Limitação de taxa de transferência

A limitação de taxa de transferência funciona exatamente da mesma forma para uploads e downloads e curl; na verdade, só tem um único limite que limitará a velocidade em ambas as direções.

Veja mais detalhes na [seção de limitação da taxa de transferẽncia](downloads.md#limitacao-de-taxa-de-transferencia).
