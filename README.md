
#  Sistema de Votaciones API

API RESTful construida con **Spring Boot 3**, **PostgreSQL**, **JWT**, y **Swagger**, que permite gestionar votantes, candidatos, votos y estadísticas de votación.

---

##  Tecnologías usadas

- Java 21
- Spring Boot 3.5
- Spring Security (con JWT)
- PostgreSQL
- JPA / Hibernate
- Swagger UI (Springdoc OpenAPI)
- Lombok
- Postman
---

##  Requisitos

- JDK 17
- Maven 3.9+
- Postman (pruebas)

---

## Ejecución del proyecto

### 1. Clona el repositorio

    git clone https://github.com/lastrazs/ApiVotaciones.git

    cd ApiVotaciones

### 2. Configura tu application.properties
    spring.datasource.url=jdbc:postgresql://localhost:5432/votaciones
    spring.datasource.username=postgres
    spring.datasource.password=postgres

    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true

    springdoc.api-docs.enabled=true
    springdoc.swagger-ui.path=/swagger-ui.html

### 4. Ejecuta la aplicación
    ./mvnw spring-boot:run

### 5. Accede a Swagger UI
    http://localhost:8080/swagger-ui.html

## Endpoints públicos
- POST /auth/register

- POST /auth/login

## Login y uso del token
- Ejecuta login:
    
      curl -X POST http://localhost:8080/auth/login \
      -H "Content-Type: application/json" \
      -d '{"email":"admin@example.com","password":"admin123"}'

Copia el token recibido:

    { "token": "eyJhbGciOi..." }

Usa el token en Swagger o Postman en el header:

Authorization: Bearer <token>

---

## Endpoints principales

| Método | URL                  | Descripción                        |
|--------|----------------------|------------------------------------|
| POST   | /auth/register       | Registro de usuarios               |
| POST   | /auth/login          | Login y generación de JWT          |
| POST   | /voters              | Crear votante                      |
| GET    | /voters              | Listar votantes                    |
| GET    | /voters/{id}         | Obtener votante por ID             |
| DELETE | /voters/{id}         | Eliminar votante                   |
| POST   | /candidates          | Crear candidato                    |
| GET    | /candidates          | Listar candidatos                  |
| GET    | /candidates/{id}     | Obtener candidato por ID           |
| DELETE | /candidates/{id}     | Eliminar candidato                 |
| POST   | /votes               | Emitir voto                        |
| GET    | /votes               | Obtener lista de votos emitidos    |
| GET    | /votes/statistics    | Ver resultados y estadísticas      |

---

## Ejemplos de uso con curl

### Crear votante
    curl -X POST http://localhost:8080/voters \
    -H "Authorization: Bearer <TOKEN>" \
    -H "Content-Type: application/json" \
    -d '{"name":"Juan Pérez","email":"juan@ejemplo.com"}'

### Crear Cantidato
    curl -X POST http://localhost:8080/candidates \
    -H "Authorization: Bearer <TOKEN>" \
    -H "Content-Type: application/json" \
    -d '{"name":"María López","party":"Partido Futuro"}'

### Emitir Voto
    curl -X POST http://localhost:8080/votes \
    -H "Authorization: Bearer <TOKEN>" \
    -H "Content-Type: application/json" \
    -d '{"voterId":1,"candidateId":1}'

### Estadísticas de votación

    {
    "totalVotersVoted": 1,
    "results": [
    {
        "candidateId": 1,
        "name": "María López",
        "votes": 1,
        "percentage": 100.0
    }
      ]
    }
---

## Test con Postman

1. Importa la colección:

Abre Postman

Haz clic en Import

Selecciona el archivo api-test.postman_collection.json (incluido en este repositorio)

Selecciona el entorno votaciones-local

Ejecuta en orden:

- Register

- Login (guarda JWT)

- Crear Votante

- Crear Candidato

- Emitir Voto

- Ver Estadísticas

  2. Colección incluida
    VotacionesApi.postman_collection.json

Contiene todos los endpoints con tokens dinámicos y pruebas listas para evaluar el funcionamiento completo del sistema.

---
### Completado

✔️ API funcional

✔️ Seguridad con JWT

✔️ Swagger listo para testear

✔️ Postman listo para testear

✔️ Base de datos conectada

---

# Autor
Sebastián Lastra Bernal.

📧 sebaslastra1018@gmail.com

🔗 www.linkedin.com/in/sebastian-lastra-6475ba259


