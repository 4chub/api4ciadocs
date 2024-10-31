# Documentação da API - Email

Esta documentação detalha os endpoints da API relacionados a login e envio de campanhas de e-mail. Todas as informações foram extraídas do documento fornecido.

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
