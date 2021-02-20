# Copiar como curl

Usar curl para realizar uma operação que um usuário acabou de fazer com seu navegador é uma das solicitações e áreas mais comuns sobre as quais as pessoas pedem ajuda.

Como você obtém uma linha de comando curl para obter um recurso, assim como o navegador faria, de forma fácil e agradável? Chrome, Firefox e Safari têm esse recurso.

## Do Firefox

Você obtém o site mostrado com as ferramentas de rede do Firefox. Em seguida, clique com o botão direito do mouse na solicitação específica que deseja repetir na ferramenta "Desenvolvedor da Web-> Rede" ao ver o tráfego HTTP e, no menu que aparece, selecione "Copiar como cURL". Como mostra a imagem abaixo. A operação então gera uma linha de comando curl para sua área de transferência e você pode colá-la na sua janela de shell favorita. Este recurso está disponível por padrão em todas as instalações do Firefox.

![copiar como curl com o Firefox](../firefox-copy-as-curl.png)

## Do Chrome

Quando você abre o pop-up Mais ferramentas-> modo Desenvolvedor no Chrome e seleciona a guia Rede, você vê o tráfego HTTP usado para obter os recursos do site. Na linha do recurso específico de seu interesse, você clica com o botão direito do mouse e seleciona "Copiar como cURL" e isso gerará uma linha de comando para você em sua área de transferência. Cole isso em um shell para obter uma linha de comando curl que faz a transferência. Este recurso está disponível por padrão em todas as instalações do Chrome e Chromium.

![copiar como curl com o Chrome](../chrome-copy-as-curl.png)

## Do Safari

No Safari, o menu "desenvolvimento" não fica visível até que você vá em **preferências-> Avançado** e o habilite. Mas, depois de fazer isso, você pode selecionar **Mostrar inspetor da web** nesse menu de desenvolvimento e ver um novo console pop-up semelhante às ferramentas de desenvolvimento do Firefox e do Chrome.

Selecione a guia de rede, recarregue a página da web e, em seguida, clique com o botão direito nos recursos específicos que deseja buscar com o curl, como se tivesse feito isso com o Safari ..

![copiar como curl com Safari](../safari-copy-as-curl.png)

## No Firefox, sem usar o devtools

Se isso é algo que você gostaria de fazer com mais frequência, provavelmente achará o uso das ferramentas de desenvolvedor um pouco inconveniente e complicado de aparecer apenas para copiar a linha de comando. Então [cliget](https://addons.mozilla.org/en-US/firefox/addon/cliget/) é o complemento perfeito para você, pois oferece uma nova opção no menu do botão direito, para que você pode obter uma linha de comando rápida gerada muito rapidamente, como este exemplo quando clico com o botão direito em uma imagem no Firefox:

![cliget com Firefox](../firefox-cliget.png)

## Imperfeito

Todos esses métodos fornecem uma linha de comando para reproduzir suas transferências HTTP. Você também aprenderá que muitas vezes ainda não são a solução perfeita para seus problemas. Porque? Bem, principalmente porque essas ferramentas são escritas para reexecutar a mesma solicitação * exata * que você copiou, enquanto você geralmente deseja reexecutar a mesma lógica, mas não enviar uma cópia exata dos mesmos cookies e conteúdo de arquivo, etc.

Essas ferramentas fornecerão linhas de comando com conteúdo de cookies estáticos e fixos para enviar na solicitação, porque esse é o conteúdo dos cookies que foram enviados nas solicitações do navegador. Provavelmente, você desejará reescrever a linha de comando para se adaptar dinamicamente a qualquer que seja o conteúdo do cookie que o servidor informou em uma resposta anterior. E assim por diante.

A funcionalidade copiar como curl também é notoriamente ruim no uso de `-F` e, em vez disso, fornecem soluções feitas à mão em` --data-binary`, incluindo strings separadoras de mime etc.