# Teste de API - Microserviço de Controle e Gestão de Clientes

Este documento descreve os testes realizados na API de um microserviço de controle e gestão de clientes utilizando o Postman.

## Descrição da API

A API foi desenvolvida em Kotlin e Spring Boot e fornece endpoints para manipulação de dados de clientes. Ela pode ser executada localmente ou acessada via Heroku.

### Endereços de acesso:

- **Local:** `http://localhost:8080/`
- **Heroku:** `https://tester-global-cliente-api.herokuapp.com/`
- **Swagger Local:** `http://localhost:8080/swagger-ui.html`
- **Swagger Heroku:** `https://tester-global-cliente-api.herokuapp.com/swagger-ui.html#/`

### Endpoints disponíveis:

- `GET /clientes` - Retorna todos os clientes.
- `GET /cliente/{ID}` - Retorna um cliente pelo ID.
- `POST /cliente` - Cadastra um novo cliente.
- `PUT /cliente` - Atualiza um cliente existente.
- `DELETE /cliente/{ID}` - Remove um cliente pelo ID.
- `GET /risco/{id}` - Retorna o risco do cliente (requisição autenticada via Basic Authentication).

---

## Configuração do Postman

Para realizar os testes, foi criada uma coleção no Postman contendo as requisições para cada endpoint. Os testes incluem:

### 1. **Teste de Consulta de Clientes** (`GET /clientes`)

- Verifica se a API retorna corretamente a lista de clientes cadastrados.
- Valida o código de resposta `200 OK`.
- Confirma que o corpo da resposta contém um array de clientes.

### 2. **Teste de Consulta de Cliente por ID** (`GET /cliente/{ID}`)

- Verifica se a API retorna corretamente os dados de um cliente específico.
- Valida o código de resposta `200 OK` quando o cliente existe.
- Verifica se retorna `404 Not Found` quando o cliente não existe.

### 3. **Teste de Cadastro de Cliente** (`POST /cliente`)

- Envia um JSON com os dados do novo cliente:
  ```json
  {
    "nome": "Teste Cliente",
    "idade": 25,
    "id": "987654321"
  }
  ```
- Valida o código de resposta `201 Created`.
- Confirma se os dados do cliente foram cadastrados corretamente.

### 4. **Teste de Atualização de Cliente** (`PUT /cliente`)

- Envia um JSON com os novos dados do cliente:
  ```json
  {
    "nome": "Cliente Atualizado",
    "idade": 30,
    "id": "987654321"
  }
  ```
- Valida o código de resposta `200 OK`.
- Confirma se os dados do cliente foram atualizados corretamente.

### 5. **Teste de Remoção de Cliente** (`DELETE /cliente/{ID}`)

- Envia uma requisição de exclusão para um ID existente.
- Valida o código de resposta `204 No Content`.
- Confirma que o cliente não existe mais ao fazer uma nova consulta.

### 6. **Teste de Consulta de Risco de Cliente** (`GET /risco/{id}`)

- Envia uma requisição autenticada com usuário e senha.
- Valida o código de resposta `200 OK`.
- Confirma que a resposta contém as informações de risco do cliente.

---

## Execução dos Testes

1. **Importe a coleção no Postman**
   - No Postman, clique em **Import** e carregue o arquivo da coleção de testes.
2. **Configure o ambiente**
   - Defina a variável `base_url` com o endereço da API (`http://localhost:8080` ou `https://tester-global-cliente-api.herokuapp.com`).
3. **Execute os testes**
   - Utilize a opção **Runner** do Postman para executar todos os testes de uma vez e validar as respostas.

---

## Conclusão

Os testes realizados validam a funcionalidade da API de clientes, garantindo que os endpoints estão funcionando conforme esperado. Para uma análise detalhada, consulte os logs do Postman e a documentação do Swagger.



