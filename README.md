# Documentação da API - Mensagem Avulsa

Esta documentação detalha o uso da API para envio de mensagens avulsas. Todas as informações foram extraídas do documento fornecido.

## Endpoint

**POST** `/api/MensagemAvulsa/Send`

**Descrição:** Este endpoint é utilizado para enviar uma mensagem avulsa com vários parâmetros configuráveis, como remetente, destinatário, canal de comunicação, status, entre outros.

---

## Parâmetros de Requisição

**Nenhum parâmetro de URL**

---

## Corpo da Requisição

O corpo da requisição deve ser enviado no formato `application/json`. A estrutura da mensagem suporta os seguintes campos:

### Exemplo de Estrutura JSON

```json
{
  "mensagemAvulsaId": 0,
  "nomeRemetente": "string",
  "nomeDestinatario": "string",
  "customId": "string",
  "remetente": "string",
  "assunto": "string",
  "canal": "string",
  "tipo": "string",
  "corpo": "string",
  "mensagemAlternativa": "string",
  "dataEnvio": "2024-10-31",
  "horaEnvio": "string",
  "dataUltimoEvento": "2024-10-31",
  "horaUltimoEvento": "string",
  "status": "string",
  "statusMessage": "string",
  "deliverdId": "string",
  "enviadoPor": "string",
  "contatoDestino": "string",
  "campanhaAvulsaId": 0,
  "campanhaAvulsa": {
    "campanhaAvulsaId": 0,
    "deliveryGroupId": "string",
    "customId": "string",
    "nome": "string",
    "canal": "string",
    "tipo": "string",
    "status": "string",
    "dataCriacao": "2024-10-31T14:55:29.440Z",
    "horaCriacao": "string",
    "dataEnvio": "2024-10-31T14:55:29.440Z",
    "horaEnvio": "string",
    "dataFinalizacao": "2024-10-31T14:55:29.440Z",
    "horaFinalizacao": "string",
    "userId": "string",
    "user": {
      "id": "string",
      "userName": "string",
      "normalizedUserName": "string",
      "email": "string",
      "normalizedEmail": "string",
      "emailConfirmed": true,
      "passwordHash": "string",
      "securityStamp": "string",
      "concurrencyStamp": "string",
      "phoneNumber": "string",
      "phoneNumberConfirmed": true,
      "twoFactorEnabled": true,
      "lockoutEnd": "2024-10-31T14:55:29.440Z",
      "lockoutEnabled": true,
      "accessFailedCount": 0,
      "name": "string",
      "balance": 0,
      "avatar": "string",
      "lastPasswordChangedDate": "2024-10-31T14:55:29.440Z",
      "temporaryPassword": true,
      "userEmpresas": [
        {
          "userEmpresaId": 0,
          "empresaId": 0,
          "empresa": {
            "empresaId": 0,
            "nome": "string",
            "razaoSocial": "string",
            "codigoInterno": "string",
            "nomenclatura4C": "string",
            "cnpj": "string",
            "fundacao": "2024-10-31T14:55:29.440Z",
            "descricao": "string",
            "regional": "string",
            "operador": "string",
            "clientesAtivos": 0,
            "paralizada": true,
            "logo": "string",
            "grupoEmpresasId": 0,
            "grupo": {
              "grupoEmpresasId": 0,
              "nome": "string",
              "descricao": "string",
              "logo": "string",
              "paralizada": true,
              "operador": "string",
              "controladoraGrupoEmpresasId": 0,
              "controladora": {
                "controladoraGrupoEmpresasId": 0,
                "nome": "string",
                "descricao": "string",
                "logo": "string",
                "paralizada": true,
                "empresas": [
                  "string"
                ]
              },
              "empresas": [
                "string"
              ]
            }
          },
          "userId": "string",
          "user": "string"
        }
      ]
    },
    "mensagens": [
      "string"
    ]
  },
  "arquivos": [
    {
      "arquivoMensagemAvulsaId": 0,
      "fileName": "string",
      "fileLocation": "string",
      "file": "string",
      "mensagemAvulsaId": 0,
      "mensagemAvulsa": "string"
    }
  ],
  "variaveis": [
    {
      "variaveisMensagemAvulsaId": 0,
      "key": "string",
      "value": "string",
      "mensagemAvulsaId": 0,
      "mensagemAvulsa": "string"
    }
  ]
}
