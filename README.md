# relationship

## Overview
A Spring Boot application demonstrating simple entity relationships and REST APIs:
- Java, Spring Boot, Maven
- Entities: `User`, `Profile`, `Post`
- Typical relationships:
  - `User` 1 — 1 `Profile` (one-to-one)
  - `User` 1 — * `Post` (one-to-many)

## Entities & Relationship Explanation
- `User`
  - Primary aggregate. Holds basic user info and references to `Profile` and a list of `Post`.
- `Profile`
  - One-to-one with `User`. Stores extended user details (bio, phone, address, etc.).
- `Post`
  - Many posts can belong to a single `User`. Stores content, title, timestamps.

These relationships are typically implemented with JPA annotations:
- `@OneToOne` (User ↔ Profile) with cascade as appropriate.
- `@OneToMany` (User → Post) with `mappedBy` and cascade/ orphan removal as needed.

## Implemented APIs (examples from `UserController`)
Base URL: `http://localhost:8081/api/users`

- `POST /api/users`
  - Create a new user 
  - Example body:
    ```json
    {
      "name": "alice"
    }
    ```

- `GET /api/users`
  - Get list of users.

- `Put /api/users/{id}/profile`
- Update Uses with Profile
  ```json
    {
      "email": "alice@gmail.com",
      "phone": "1234567890"
    }
- `POST /api/users/{id}/posts`
  ```json
    {
      "title": "First Post"
    }
  ```
```

- Check Get All Again