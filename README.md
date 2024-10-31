# Documentação da API - Email

Esta documentação detalha os endpoints da API relacionados a login e envio de campanhas de e-mail.

---

## Endpoint de Login

### **POST** `/api/Login`

**Descrição:** Efetua login na API para obter o token necessário para autenticação.

### Exemplo de Requisição

```json
{
  "Username": "NomeDeUsuario",
  "Password": "Senha"
}
```

### Parâmetros

- **Sem parâmetros de URL**

### Corpo da Requisição

Formato `application/json`:

```json
{
  "username": "string",
  "password": "string"
}
```

### Respostas

- **200 OK**: Retorna o token e a validade.
- **400 Bad Request**: Falha na autenticação.

---

## Endpoint de Envio de Email

### **POST** `/api/Email/Send`

**Descrição:** Envia uma campanha de e-mail.

**Autenticação:** A autenticação é feita por Bearer token. Para obtê-lo, use o endpoint `/api/Login` descrito acima.

### Propriedades da Campanha

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `nomeRemetente`     | Nome do Remetente do E-mail            | Sim           |
| `remetente`         | Endereço de E-mail do Remetente        | Sim           |
| `assunto`           | Assunto do E-mail                      | Sim           |
| `customId`          | Id Customizado para identificação      | Não           |
| `nome`              | Nome da Campanha                       | Sim           |
| `mensagens`         | Lista de Mensagens a serem enviadas    | Sim           |

### Propriedades das Mensagens

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Não           |
| `corpo`             | Corpo do E-mail em HTML                | Sim           |
| `contatoDestino`    | Endereço de E-mail do Destinatário     | Sim           |

### Exemplo de Corpo da Requisição

Formato `application/json`:

```json
{
  "nomeRemetente": "string",
  "remetente": "string",
  "assunto": "string",
  "customId": "string",
  "nome": "string",
  "mensagens": [
    {
      "customId": "string",
      "corpo": "string",
      "contatoDestino": "string"
    }
  ]
}
```

### Respostas

- **200 OK**: Solicitação bem-sucedida.
  ```json
  {
    "nomeCampanha": "string",
    "idCampanha": 0,
    "customId": "string",
    "mensagens": [
      "string"
    ]
  }
  ```

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.
```json
  {
    "nomeCampanha": "string",
    "idCampanha": 0,
    "customId": "string",
    "mensagens": [
      "string"
    ]
  }
  ```

- **401 Unauthorized**: Não logado ou sem privilégios.
```json
  {
    "type": "string",
    "title": "string",
    "status": 0,
    "detail": "string",
    "instance": "string",
    "additionalProp1": "string",
    "additionalProp2": "string",
    "additionalProp3": "string"
  }
  ```

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Relatório de Campanha

### **GET** `/api/Email/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de e-mail.

### Parâmetros

| **Nome**            | **Descrição**                          | **Tipo**      | **Local**  |
|---------------------|----------------------------------------|---------------|------------|
| `page`              | Página buscada                        | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados         | `integer`     | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)           | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)      | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)        | `string`      | (query)    |

### Respostas

- **200 OK**: Solicitação bem-sucedida.
```json
  {
    "campanhaId": 0,
    "customId": "string",
    "nomeCampanha": "string",
    "status": "string",
    "dataEnvio": "2024-10-31T19:49:24.641Z",
    "mensagens": [
      {
        "customId": "string",
        "contato": "string",
        "status": "string",
        "direction": "string",
        "mensagem": "string",
        "dataEnvio": "2024-10-31T19:49:24.641Z"
      }
    ]
  }
  ```

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.
```json
  {
    "type": "string",
    "title": "string",
    "status": 0,
    "detail": "string",
    "instance": "string",
    "additionalProp1": "string",
    "additionalProp2": "string",
    "additionalProp3": "string"
  }
```

- **401 Unauthorized**: Não logado ou sem privilégios.
```json
  {
    "type": "string",
    "title": "string",
    "status": 0,
    "detail": "string",
    "instance": "string",
    "additionalProp1": "string",
    "additionalProp2": "string",
    "additionalProp3": "string"
  }
  ```

- **403 Forbidden**: Acesso ao recurso é proibido.


## Endpoint de Envio de SMS

### **POST** `/api/SMS/Send`

**Descrição:** Envia uma campanha de SMS.

**Autenticação:** A autenticação é feita por Bearer token. Para obtê-lo, é necessário efetuar login através do endpoint `/api/Login`.

### Propriedades da Campanha

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Não           |
| `nome`              | Nome da Campanha                       | Sim           |
| `mensagens`         | Lista de Mensagens a serem enviadas    | Sim           |

### Propriedades das Mensagens

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Não           |
| `corpo`             | Mensagem a ser enviada                 | Sim           |
| `contatoDestino`    | Endereço de E-mail do Destinatário     | Sim           |

### Exemplo de Corpo da Requisição

Formato `application/json`:

```json
{
  "customId": "string",
  "nome": "string",
  "mensagens": [
    {
      "customId": "string",
      "corpo": "string",
      "contatoDestino": "string"
    }
  ]
}
```

### Respostas

- **200 OK**: Solicitação bem-sucedida.
  ```json
  {
    "nomeCampanha": "string",
    "idCampanha": 0,
    "customId": "string",
    "mensagens": [
      "string"
    ]
  }
  ```

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.
  ```json
  {
    "nomeCampanha": "string",
    "idCampanha": 0,
    "customId": "string",
    "mensagens": [
      "string"
    ]
  }
  ```

- **401 Unauthorized**: Não logado ou sem privilégios.
  ```json
  {
    "type": "string",
    "title": "string",
    "status": 0,
    "detail": "string",
    "instance": "string",
    "additionalProp1": "string",
    "additionalProp2": "string",
    "additionalProp3": "string"
  }
  ```

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Relatório de Campanha de SMS

### **GET** `/api/SMS/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de SMS.

### Parâmetros

| **Nome**            | **Descrição**                          | **Tipo**      | **Local**  |
|---------------------|----------------------------------------|---------------|------------|
| `page`              | Página buscada                        | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados         | `integer`     | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)           | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)      | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)        | `string`      | (query)    |

### Respostas

- **200 OK**: Solicitação bem-sucedida.
  ```json
  {
    "campanhaId": 0,
    "customId": "string",
    "nomeCampanha": "string",
    "status": "string",
    "dataEnvio": "2024-10-31T20:51:50.981Z",
    "mensagens": [
      {
        "customId": "string",
        "contato": "string",
        "status": "string",
        "direction": "string",
        "mensagem": "string",
        "dataEnvio": "2024-10-31T20:51:50.981Z"
      }
    ]
  }
  ```
- **400 Bad Request**: Ocorreu uma falha durante a solicitação.
  ```json
  {
    "type": "string",
    "title": "string",
    "status": 0,
    "detail": "string",
    "instance": "string",
    "additionalProp1": "string",
    "additionalProp2": "string",
    "additionalProp3": "string"
  }
  ```

- **401 Unauthorized**: Não logado ou sem privilégios.
  ```json
  {
    "type": "string",
    "title": "string",
    "status": 0,
    "detail": "string",
    "instance": "string",
    "additionalProp1": "string",
    "additionalProp2": "string",
    "additionalProp3": "string"
  }
  ```

- **403 Forbidden**: Acesso ao recurso é proibido.
