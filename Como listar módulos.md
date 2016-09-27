Exibe todos os módulos cadastrados na empresa

```
https://api.replay4.me/embed/modules
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
    "modules": [
      {
        "id": 21,
        "title": "Planejamento 2015",
        "status": "published",
        "slug": "planejamento-2015",
        "icon": "fa-book",
        "menu_order": 1,
        "type": "curso",
        "company_id": 11,
        "updated_at": "2015-09-03 14:24:44",
        "created_at": "2014-12-05 18:37:46",
        "parent": []
      },
      {
        "id": 496,
        "title": "Teste Bruna",
        "status": "draft",
        "slug": "teste-bruna",
        "icon": "fa-folder-open",
        "menu_order": 6,
        "type": "curso",
        "company_id": 11,
        "updated_at": "2015-09-03 14:36:03",
        "created_at": "2015-09-03 13:31:14",
        "parent": []
      }
    ]
  }
}
```



## Exemplo de código (PHP)

```php
<?php
$ch = curl_init('https://api.replay4.me/embed/modules?client_id=1235&client_secret=seu_client_secret');
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER => false
]);

$response = curl_exec($ch);

curl_close($ch);

$modules = json_decode($response);
```