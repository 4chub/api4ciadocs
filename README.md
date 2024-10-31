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
