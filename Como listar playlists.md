## Como listar playlists

Exibe todas as playlsits de um determinado módulo cadastrados na empresa. 

```
https://api.replay4.me/api/playlists
```

## Informações

<table>
    <tbody>
        <tr>
            <td>Tipo</td>
            <td>GET</td>
        </tr>
        <tr>
            <td>Formato da resposta</td>
            <td>JSON</td>
        </tr>
        <tr>
            <td>Requer autenticação</td>
            <td>Sim</td>
        </tr>
        <tr>
            <td>Limite de requisições</td>
            <td>Não</td>
        </tr>
        <tr>
            <td valign="top">Respostas</td>
            <td>
                <table>
                    <thead>
                        <tr>
                            <th>Código</th>
                            <th></th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>200</td>
                            <td>OK</td>
                        </tr>
                        <tr>
                            <td>405</td>
                            <td>Método não permitido</td>
                        </tr>
                        <tr>
                            <td>403</td>
                            <td>Acesso negado</td>
                        </tr>
                        <tr>
                            <td>404</td>
                            <td>Não encontrado</td>
                        </tr>
                    </tbody>
                </table>
            </td>
        </tr>
    </tbody>
</table>

## Parâmetros

<table>
    <tbody>
        <tr>
            <td valign="top"><strong>client_id</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>ID do cliente</td>
                    </tr>
                    <tr>
                        <td>Obrigatório</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td valign="top"><strong>client_secret</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>Token para autenticar usuário</td>
                    </tr>
                    <tr>
                        <td>Obrigatório</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td valign="top"><strong>access_token</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>Token de autenticação gerado para o usuário</td>
                    </tr>
                    <tr>
                        <td>Obrigatório</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td valign="top"><strong>module_id</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>ID do módulo</td>
                    </tr>
                    <tr>
                        <td>Obrigatório</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td valign="top"><strong>status</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>Por padrão, todas as playlists são retornadas (rascunhos e publicadas). Para retornar apenas as playlists publicadas, utilize a palavra chave "published". Ou "draft" para playlists não publicadas.</td>
                    </tr>
                    <tr>
                        <td>Opcional</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
    </tbody>
</table>

## Resposta

```json
{
    "meta": {
        "code": 200,
        "msg": "OK"
    },
    "data": {
        "playlists": [
            {
                "embed_token": "550fdsfad739c2536yw2S0dsZ4gb8RZlBDtoDPTewF61QmWRpgfuJnY5f",
                "thumbnail": "//static.replay4me.dev/images/replay4me/Osf591zspxCuGRjXZRoBJ5481d21331d7f.jpg",
                "title": "Consectetur adipsi",
                "description": "Lorem ipsum dolor sit amet, consectetur adipisicing elit.",
                "status":"published",
                "done": "70"
            },
            {
                "embed_token": "550xd7316930eH6sdsdsxvC8odV7j6PexiLXp0UMnopaNDYo21kFHpfv",
                "thumbnail": "//static.replay4me.dev/images/replay4me/AexSnIDp2kH2MtCBbdF0z54b412dbadedf.jpeg",
                "title": "Lorem Ipsum",
                "description": " Natus maxime, mollitia maiores tenetur eaque, ad voluptates saepe, ratione dolorem aperiam architecto dolorum neque soluta quisquam alias minima doloribus esse. Aliquid?",
                "status": "draft",
                "done": "0"
            }
        ]
    }
}
```


## Exemplo de código (PHP)

```php
<?php
$ch = curl_init('https://api.replay4.me/embed/playlists?client_id=1235&client_secret=seu_client_secret&access_token=seu_access_token&module_id=123');
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER => false
]);

$response = curl_exec($ch);

curl_close($ch);

$playlists = json_decode($response);
```