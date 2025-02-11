# Desafio de Programação 

## Introdução
Este projeto consiste na implementação de uma API REST para recebimento de transações e geração de estatísticas. A API foi desenvolvida utilizando **Java** com **Spring Boot**, armazenando os dados em memória sem o uso de banco de dados ou cache.

## Tecnologias Utilizadas
- **Java 17+**
- **Spring Boot 3**
- **Spring Web**
- **Spring Validation**
- **Lombok**
- **JUnit & Mockito** (para testes)
- **Swagger/OpenAPI** (para documentação)

## Como Executar o Projeto
### Requisitos
- **Java 17+**
- **Maven** ou **Gradle**

### Passos
1. Clone o repositório:
   ```sh
   git clone https://github.com/Leticia0587/TransactionAPI-.git
   ```
2. Compile e execute a aplicação:
   ```sh
   ./mvnw spring-boot:run # Para Maven
   ```
   ou
   ```sh
   ./gradlew bootRun # Para Gradle
   ```
3. A API estará disponível em `http://localhost:8080`
4. A documentação interativa pode ser acessada via **Swagger UI**:
   ```
   http://localhost:8080/swagger-ui/index.html
   ```

## Endpoints da API
### 1. Criar Transação
**POST** `/transacao`

#### Request Body:
```json
{
    "valor": 123.45,
    "dataHora": "2020-08-07T12:34:56.789-03:00"
}
```
#### Regras:
- `valor` não pode ser negativo.
- `dataHora` deve estar no passado.
- `dataHora` deve estar no formato **ISO 8601**.

#### Respostas:
- **201 Created**: Transação registrada com sucesso.
- **422 Unprocessable Entity**: Alguma regra de validação falhou.
- **400 Bad Request**: JSON inválido.

---

### 2. Limpar Transações
**DELETE** `/transacao`

#### Descrição:
Remove todas as transações armazenadas em memória.

#### Respostas:
- **200 OK**: Todas as transações foram removidas.

---

### 3. Obter Estatísticas
**GET** `/estatistica`

#### Descrição:
Retorna estatísticas das transações realizadas nos últimos **60 segundos**.

#### Response Body:
```json
{
    "count": 10,
    "sum": 1234.56,
    "avg": 123.456,
    "min": 12.34,
    "max": 123.56
}
```
#### Respostas:
- **200 OK**: Estatísticas retornadas com sucesso.
- Se não houver transações, todos os valores serão **0**.

---

## Testes
Os testes unitários e de integração foram escritos utilizando **JUnit** e **Mockito**.

Para executar os testes, utilize:
```sh
./mvnw test  # Para Maven
```
Ou:
```sh
./gradlew test  # Para Gradle
```

---

## Melhorias Futuras
- Implementação de logs e monitoramento
- Melhor tratamento de erros e mensagens mais detalhadas
- Melhorias na performance do armazenamento em memória

---

## Autor
Desenvolvido por [Letícia Araujo](https://github.com/Leticia0587).

