# Documentação da API - 4Cia

Esta documentação detalha os endpoints da API relacionados a login e envio de campanhas de e-mail.

---

### **URL de requisição:** `https://api.4ciweb.com`

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
| `customId`          | Id Customizado para identificação      | Sim           |
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

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Relatório de Campanha de E-mail

### **GET** `/api/Email/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de e-mail.

### Parâmetros

| **Nome**            | **Descrição**                                           | **Tipo**      | **Local**  |
|---------------------|---------------------------------------------------------|---------------|------------|
| `page`              | Página buscada                                          | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados (Opcional, padrão: 1000) | `integer`     | (query)    |
| `campaigncustomId`  | customid da campanha (Opcional)                         | `string`      | (query)    |
| `msgcustomId`       | customid da mensagem (Opcional)                         | `string`      | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)                             | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)                        | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)                          | `string`      | (query)    |

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Envio de SMS

### **POST** `/api/SMS/Send`

**Descrição:** Envia uma campanha de SMS.

**Autenticação:** A autenticação é feita por Bearer token. Para obtê-lo, é necessário efetuar login através do endpoint `/api/Login`.

### Propriedades da Campanha

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Sim           |
| `nome`              | Nome da Campanha                       | Sim           |
| `mensagens`         | Lista de Mensagens a serem enviadas    | Sim           |

### Propriedades das Mensagens

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Não           |
| `corpo`             | Mensagem a ser enviada                 | Sim           |
| `contatoDestino`    | Telefone do Destinatário               | Sim           |

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

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Relatório de Campanha de SMS

### **GET** `/api/SMS/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de SMS.

### Parâmetros

| **Nome**            | **Descrição**                                           | **Tipo**      | **Local**  |
|---------------------|---------------------------------------------------------|---------------|------------|
| `page`              | Página buscada                                          | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados (Opcional, padrão: 1000) | `integer`     | (query)    |
| `campaigncustomId`  | customid da campanha (Opcional)                         | `string`      | (query)    |
| `msgcustomId`       | customid da mensagem (Opcional)                         | `string`      | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)                             | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)                        | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)                          | `string`      | (query)    |

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Envio de WhatsApp

### **POST** `/api/Whatsapp/Send`

**Descrição:** Envia uma campanha via WhatsApp.

**Autenticação:** A autenticação é feita por Bearer token. Para obtê-lo, é necessário efetuar login através do endpoint `/api/Login`.

### Propriedades da Campanha

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Sim           |
| `nome`              | Nome da Campanha                       | Sim           |
| `templateId`        | Template da mensagem enviada           | Sim           |
| `mensagens`         | Lista de Mensagens a serem enviadas    | Sim           |

### Propriedades das Mensagens

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Não           |
| `corpo`             | Resumo da mensagem                     | Sim           |
| `contatoDestino`    | Telefone do Destinatário               | Sim           |
| `variaveis`         | Variáveis do template se houver        | Sim           |

### Propriedades das Variáveis

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `key`               | Nome da variável                       | Sim           |
| `value`             | Valor da variável                      | Sim           |

### De-Para de variáveis

| **Variável**           | **Informação**                      |
|------------------------|-------------------------------------|
| `-var1-`               | Nome                                |
| `-var2-`               | Código de Barras                    |
| `-var3-`               | Vencimento                          |
| `-var4-`               | Valor                               |
| `-var5-`               | Extra                               |

### Exemplo de Corpo da Requisição

Formato `application/json`:

```json
{
  "customId": "string",
  "templateId": "string",
  "nome": "string",
  "mensagens": [
    {
      "customId": "string",
      "corpo": "string",
      "contatoDestino": "string",
      "variaveis": [
        {
          "key": "-var1-",
          "value": "string"
        },
        {
          "key": "-var2-",
          "value": "string"
        }
      ]
    }
  ]
}

```

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.
---
## Endpoint de Consulta de Template Whatsapp

### **GET** `/api/templatesid`

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

---

## Endpoint de Relatório de Campanha de WhatsApp

### **GET** `/api/Whatsapp/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de WhatsApp.

### Parâmetros

| **Nome**            | **Descrição**                                           | **Tipo**      | **Local**  |
|---------------------|---------------------------------------------------------|---------------|------------|
| `page`              | Página buscada                                          | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados (Opcional, padrão: 1000) | `integer`     | (query)    |
| `campaigncustomId`  | customid da campanha (Opcional)                         | `string`      | (query)    |
| `msgcustomId`       | customid da mensagem (Opcional)                         | `string`      | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)                             | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)                        | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)                          | `string`      | (query)    ||

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Envio de URA

### **POST** `/api/URA/Send`

**Descrição:** Envia uma campanha de URA.

**Autenticação:** A autenticação é feita por Bearer token. Para obtê-lo, é necessário efetuar login através do endpoint `/api/Login`.

### Propriedades da Campanha

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Sim           |
| `templateId`        | Template utilizado para a campanha     | Sim           |
| `nome`              | Nome da Campanha                       | Sim           |
| `mensagens`         | Lista de Mensagens a serem enviadas    | Sim           |

### Propriedades das Mensagens

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Sim           |
| `contatoDestino`    | Telefone do Destinatário               | Sim           |

### Exemplo de Corpo da Requisição

Formato `application/json`:

```json
{
  "customId": "string",
  "templateId": "string",
  "nome": "string",
  "mensagens": [
    {
      "customId": "string",
      "corpo": "string",
      "contatoDestino": "string",
    }
  ]
}
```

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---


## Endpoint de Relatório de Campanha de URA

### **GET** `/api/URA/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de URA.

### Parâmetros

| **Nome**            | **Descrição**                                           | **Tipo**      | **Local**  |
|---------------------|---------------------------------------------------------|---------------|------------|
| `page`              | Página buscada                                          | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados (Opcional, padrão: 1000) | `integer`     | (query)    |
| `campaigncustomId`  | customid da campanha (Opcional)                         | `string`      | (query)    |
| `msgcustomId`       | customid da mensagem (Opcional)                         | `string`      | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)                             | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)                        | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)                          | `string`      | (query)    |

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---

## Endpoint de Envio de RCS

### **POST** `/api/RCS/Send`

**Descrição:** Envia uma campanha de RCS.

**Autenticação:** A autenticação é feita por Bearer token. Para obtê-lo, é necessário efetuar login através do endpoint `/api/Login`.

### Propriedades da Campanha

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Sim           |
| `templateId`        | Template utilizado para a campanha     | Sim           |
| `nome`              | Nome da Campanha                       | Sim           |
| `mensagens`         | Lista de Mensagens a serem enviadas    | Sim           |
| `fallbacks`         | Fallback a ser enviado                 | Sim           |

### Propriedades das Mensagens

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `customId`          | Id Customizado para identificação      | Sim           |
| `contatoDestino`    | Telefone do Destinatário               | Sim           |
| `variaveis`         | Variáveis utilizados no template       | Não           |

### Propriedades do Fallback

| **Propriedade**     | **Descrição**                          | **Requerido** |
|---------------------|----------------------------------------|---------------|
| `templateId`          | ID do Fallback correspondente        | Sim           |

### Exemplo de Corpo da Requisição

Formato `application/json`:

```json
{
  "customId": "string",
  "templateId": "string",
  "nome": "string",
  "mensagens": [
    {
      "customId": "string",
      "contatoDestino": "string",
      "variaveis": [
        {
          "key": "string",
          "value": "string"
        }
      ]
    }
  ],
  "fallbacks": [
    {
      "templateId": "string"
    }
  ]
}
```

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

---


## Endpoint de Relatório de Campanha de RCS

### **GET** `/api/RCS/Relatorio/Pagina/{page}`

**Descrição:** Obtém o relatório de envio de uma campanha de RCS.

### Parâmetros

| **Nome**            | **Descrição**                                           | **Tipo**      | **Local**  |
|---------------------|---------------------------------------------------------|---------------|------------|
| `page`              | Página buscada                                          | `integer`     | (path)     |
| `pageSize`          | Quantidade de dados retornados (Opcional, padrão: 1000) | `integer`     | (query)    |
| `campaigncustomId`  | customid da campanha (Opcional)                         | `string`      | (query)    |
| `msgcustomId`       | customid da mensagem (Opcional)                         | `string`      | (query)    |
| `nomeCampanha`      | Nome da campanha (Opcional)                             | `string`      | (query)    |
| `dataInicial`       | Data Inicial do Envio (Opcional)                        | `string`      | (query)    |
| `dataFinal`         | Data Final do Envio (Opcional)                          | `string`      | (query)    |

### Respostas

- **200 OK**: Solicitação bem-sucedida.

- **400 Bad Request**: Ocorreu uma falha durante a solicitação.

- **401 Unauthorized**: Não logado ou sem privilégios.

- **403 Forbidden**: Acesso ao recurso é proibido.

