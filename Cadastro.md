Captura as credenciais necessárias para cadastrar um usuário.

```
https://api.replay4.me/api/register
```

## Informações

<table>
    <tbody>
        <tr>
            <td>Tipo</td>
            <td>POST</td>
        </tr>
        <tr>
            <td>Formato de resposta</td>
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
                            <td>201</td>
                            <td>Criado com sucesso</td>
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
        <tr>
            <td valign="top"><strong>name</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>Nome do cliente que será autenticado</td>
                    </tr>
                    <tr>
                        <td>Obrigatório</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td valign="top"><strong>email</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>Email do cliente que será autenticado</td>
                    </tr>
                    <tr>
                        <td>Obrigatório</td>
                        <td>Sim</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td valign="top"><strong>password</strong></td>
            <td>
                <table>
                    <tr>
                        <td>Descrição</td>
                        <td>Senha do cliente que será autenticado</td>
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

Caso o email enviado não exista, o usuário será cadastrado na empresa e adicionado como "visualizador" de conteúdo.
O usuário, não poderá criar ou editar conteúdos existentes. Caso queira alterar o perfil do usuário, entre na plataforma `https://app.replay4.me` com
seu usuário (administrador), clique na opção `usuários` e altere o perfil do novo usuário.

## Resposta

```json
{
    "meta": {
        "code": 201,
        "msg": "OK"
    },
    "data": {
        "access_token": "550712d48ca81t11esF7VOFfT1vUVlUaSzg",
        "user": {
            "id": "2147",
            "email": "fulano@fulaninho.com.br",
            "name": "Nome do Fulaninho",
            "enabled": true
        }
    }
}
```



## Exemplo de código (PHP)

```php
<?php
$ch = curl_init('https://api.replay4.me/embed/access_token/request');
curl_setopt_array($ch, [
    CURLOPT_POST => true,
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_HEADER => false,
    CURLOPT_POSTFIELDS => http_build_query([
        'client_id' => 1235, // seu client_id
        'client_secret' => 'asdfgasdfgasdfg', // seu client_secret
        'email' => 'emaildousuariocomacesso@dominio.com.br',
        'name' => 'Nome do Usuário',
        'password' => 'senha do usuário'
    ])
]);

$response = curl_exec($ch);

curl_close($ch);

$credentials = json_decode($response);
```