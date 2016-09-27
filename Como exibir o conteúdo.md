Após autenticar, utilize o token gerado e o código "embed_token" da playlist para exibir o conteúdo na sua plataforma.


## Código de integração

```Javascript
(function(e,a,n,t,r){e[r]=e[r]||function(){(e[r].data=e[r].data||[]).push(arguments)};
 var s=a.createElement(n),c=a.getElementsByTagName(n)[0];s.async=1,
 s.src=t,c.parentNode.insertBefore(s,c)
 })(window,document,'script','//api.replay4.me/in.js','r4me');

r4me('domain',window.document.domain || window.location.href );

r4me('params',{
    'token':'o token de autenticação', // TOKEN Gerado via autenticação
    'embed':'código embed_token da playlist (ou trilha)' // Embed Token da playlist que será exibida
});


r4me('action','embed');

// Onde você gostaria de exibir o conteúdo ?
// Utilize seletores jQuery
r4me('options',{
    'target': '#conteudo',
    'share_notes':true, // Exibe ou não as opções para compartilhar notas
    'title': true, // exibe ou não o 
    'show_list': true, // exibe ou não a lista de vídeos
    'show_buttons': false, // exibe ou não botões para o anterior/próximo vídeo da lista
    'dinamic_size': true, //Permitir ou não modificar dinamicamente o tamanho do iframe que exibe o conteúdo 
    'auto_play': true, //Permite que o vídeo inicie automaticamente 
    'container': {'height':'400px','loading_height':'200px'} // define a altura e tela de carregando do player 
});

// Eventos
r4me('events.onload',function(playlistInfo){
    console.log(playlistInfo);
});

//Código que permite a alteração do tamanho do player, 
//se o dinamic_size for utilizado, este código deve ficar na página, 
//para receber a informação enviada pela plataforma 
var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
var eventer = window[eventMethod];
var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";

eventer(messageEvent, function(e) {
  if (isNaN(e.data)) return;
  document.getElementsByTagName('iframe')[0].style.height = e.data + 'px';
}, false);
```


## Exemplo (HTML)

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Minha página</title>
</head>
<body>

    <div class="wrap">
        <div class="content">
            <!-- conteúdo será exibido aqui -->
        </div>
    </div>

    <script>
        (function(e,a,n,t,r){e[r]=e[r]||function(){(e[r].data=e[r].data||[]).push(arguments)};
         var s=a.createElement(n),c=a.getElementsByTagName(n)[0];s.async=1,
         s.src=t,c.parentNode.insertBefore(s,c)
         })(window,document,'script','//api.replay4.me/in.js','r4me');

        r4me('domain',window.document.domain || window.location.href );

        r4me('params',{
            'token':'o token de autenticação', // TOKEN Gerado via autenticação
            'embed':'código embed_token da playlist (ou trilha)' // Embed Token da playlist que será exibida
        });


        r4me('action','embed');

        // Onde você gostaria de exibir o conteúdo ?
        // Utilize seletores jQuery
        r4me('options',{
            'target': '.content',
            'share_notes':true, // Exibe ou não as opções para compartilhar notas
            'title': true, // exibe ou não o título 
            'show_list': true, // exibe ou não a lista de vídeos
            'show_buttons': false, // exibe ou não botões para o anterior/próximo vídeo da lista
            'dinamic_size': true, //Permitir ou não modificar dinamicamente o tamanho do iframe que exibe o conteúdo 
            'auto_play': true, //Permite que o vídeo inicie automaticamente 
            'container': {'height':'400px','loading_height':'200px'} // define a altura e tela de carregando do player 

        });

        // Eventos
        r4me('events.onload',function(playlistInfo){
            console.log(playlistInfo);
        });

        //Código que permite a alteração do tamanho do player, 
        //se o dinamic_size for utilizado, este código deve ficar na página, 
        //para receber a informação enviada pela plataforma 
        var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
        var eventer = window[eventMethod];
        var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";

        eventer(messageEvent, function(e) {
          if (isNaN(e.data)) return;
          document.getElementsByTagName('iframe')[0].style.height = e.data + 'px';
        }, false);
    </script>

</body>
</html>
```