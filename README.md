# Social Media Backend Service 

A **production‑ready REST API** that powers a miniature Twitter‑style platform.  
It supports user management, authentication, posting, commenting, and robust error handling—all crafted with clean architecture and test‑driven principles.

---

## ✨ Features

| Domain            | Highlights                                                          |
|-------------------|---------------------------------------------------------------------|
| **Authentication**| JWT‑based sign‑up, login, refresh‑token flow, password hashing      |
| **Users**         | CRUD operations, follower/following counts, profile update endpoints|
| **Posts**         | Create / read / update / delete posts with pagination & reactions   |
| **Comments**      | Threaded comments, soft‑deletion, like/dislike                      |
| **Validation**    | Spring Validation + custom exceptions for graceful 4xx responses    |
| **Docs**          | Live Swagger UI (`/swagger-ui.html`) + versioned Postman collection |
| **Testing**       | Unit + integration tests with Testcontainers & H2                  |
| **CI/CD**         | GitHub Actions build, test & Docker image push                     |

---

## 🏗 Tech Stack

| Layer                | Tech                           |
|----------------------|--------------------------------|
| Language             | **Java 17**                    |
| Framework            | **Spring Boot 3**, Spring Web  |
| Security             | Spring Security, **JWT**       |
| Data Store           | PostgreSQL (prod) / H2 (local) |
| Build Tool           | **Maven (Wrapper)**            |
| Containerization     | **Docker**                     |
| Documentation        | SpringDoc OpenAPI & Swagger UI |
| Tests                | JUnit 5, Mockito, Testcontainers|
| CI/CD                | **GitHub Actions**             |

---

## 🛠 Architecture at a Glance

┌──────────────┐
│ controllers │ ➜ REST endpoints / DTO mapping
└──────────────┘
│
┌──────────────┐
│ services │ ➜ business rules, transactions
└──────────────┘
│
┌──────────────┐
│ repositories │ ➜ Spring Data JPA (Postgres/H2)
└──────────────┘
│
┌──────────────┐
│ models │ ➜ JPA entities
└──────────────┘

Clean, layered design—controllers never talk to JPA directly, and entities never “know” about HTTP.

---

## 🚀 Getting Started

### 1 · Clone & build

```bash
git clone https://github.com/Vaibhav-09-F/social-media-backend-service.git
cd social-media-backend-service
./mvnw clean package
```

### 2 · Run locally (H2)
```bash
./mvnw spring-boot:run
# App live at http://localhost:8080
# Swagger at http://localhost:8080/swagger-ui.html
```
### 3 · Run with Docker (PostgreSQL)
```bash
docker compose up --build
# API → http://localhost:8080
```

📚 API Reference
Method	Endpoint	Description
POST	/api/v1/auth/register	Register new user
POST	/api/v1/auth/login	Login & receive JWT
GET	/api/v1/users/{id}	Fetch profile
POST	/api/v1/posts	Create post
GET	/api/v1/posts?page=0	List posts (paginated)
POST	/api/v1/posts/{id}/comments	Comment on a post
…	More in Swagger	

👉 Import the bundled Postman collection: postman/social-media-backend.postman_collection.json.

🧪 Tests
```bash
./mvnw test
```

* 90%+ line coverage
* Integration tests spin up PostgreSQL via Testcontainers for true‑to‑prod behavior.

