# Open-Source Library System (OSLS)
**Buzzword Software Solutions Limited — Software Development Department**

---

## Tech Stack
- Java 17, Spring Boot 3.2.5, Maven
- Spring Security + JWT (jjwt 0.11.5)
- Spring Data JPA + Hibernate + MySQL
- Vanilla HTML/CSS/JS frontend (MVC pattern)

---

## Setup

### 1. MySQL Database
Make sure MySQL is running locally. The app auto-creates the `osls_db` database.

Default credentials in `application.properties`:
```
spring.datasource.username=root
spring.datasource.password=root
```
Change these to match your local MySQL setup.

### 2. Run the App
```bash
mvn spring-boot:run
```
App starts at: **http://localhost:8080**

### 3. Create Admin User
After registering normally, open MySQL and run:
```sql
USE osls_db;
UPDATE users SET role='ADMIN' WHERE username='your_username';
```

---

## Project Structure
```
src/main/java/com/buzzword/osls/
├── config/         SecurityConfig.java
├── controller/     AuthController, ResourceController, CommentController, AdminController
├── dto/            Request/Response DTOs
├── model/          User, Resource, Comment entities + enums
├── repository/     JPA Repositories
├── security/       JwtUtil, JwtFilter, CustomUserDetailsService
└── service/        AuthService, ResourceService, CommentService, UserService

src/main/resources/static/
├── index.html      Login / Register
├── dashboard.html  Browse & search resources
├── resource.html   Add/Edit resource + comments
├── admin.html      Admin panel
├── css/style.css
└── js/             auth.js, dashboard.js, resource.js, admin.js
```

---

## API Endpoints

| Method | Path | Auth |
|---|---|---|
| POST | /api/auth/register | Public |
| POST | /api/auth/login | Public |
| GET | /api/resources | USER |
| GET | /api/resources/search?q=&category= | USER |
| POST | /api/resources | USER |
| PUT | /api/resources/{id} | Owner/Admin |
| DELETE | /api/resources/{id} | Owner/Admin |
| GET | /api/resources/{id}/comments | USER |
| POST | /api/resources/{id}/comments | USER |
| PUT | /api/comments/{id} | Owner/Admin |
| DELETE | /api/comments/{id} | Owner/Admin |
| GET | /api/admin/users | ADMIN |
| DELETE | /api/admin/users/{id} | ADMIN |
| DELETE | /api/admin/resources/{id} | ADMIN |
"# OSLS" 
