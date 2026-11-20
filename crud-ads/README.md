# API de Funcionários – Spring Boot + Spring Security

| Método | Endpoint                  | Acesso                          |
|--------|---------------------------|---------------------------------|
| GET    | `/api/funcionarios`       | Público                         |
| GET    | `/api/funcionarios/{id}`  | Público                         |
| POST   | `/api/funcionarios`       | Público                         |
| PUT    | `/api/funcionarios/{id}`  | Autenticado (HTTP Basic)        |
| DELETE | `/api/funcionarios/{id}`  | Autenticado (HTTP Basic)        |

Credenciais (definidas em `application.properties`): `admin` / `admin123`

## Executar
```
./mvnw spring-boot:run
```

## Testar com curl
```
# público
curl http://localhost:8080/api/funcionarios
curl -X POST http://localhost:8080/api/funcionarios -H "Content-Type: application/json" \
     -d '{"nome":"Ana","cpf":"12345678900","rua":"Rua A"}'

# sem credenciais -> 401
curl -i -X PUT http://localhost:8080/api/funcionarios/1 -H "Content-Type: application/json" \
     -d '{"nome":"Ana Maria","cpf":"12345678900","rua":"Rua B"}'

# com credenciais -> 200
curl -u admin:admin123 -X PUT http://localhost:8080/api/funcionarios/1 -H "Content-Type: application/json" \
     -d '{"nome":"Ana Maria","cpf":"12345678900","rua":"Rua B"}'
curl -u admin:admin123 -X DELETE http://localhost:8080/api/funcionarios/1
```
