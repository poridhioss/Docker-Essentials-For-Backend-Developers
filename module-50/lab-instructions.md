# Module 50: Build a JWT-Based Authentication API

This structure follows a logical development lifecycle: **Database Design $\rightarrow$ Registration (Security) $\rightarrow$ Login (Token Generation) $\rightarrow$ Verification (Middleware) $\rightarrow$ Maintenance (Refresh Tokens).**

### **Lab 1: Project Setup & Database Architecture**
**Context:** Before handling authentication, students need a working application skeleton and a place to store user data. This lab focuses on the "Design a relational SQL schema" objective.

*   **Goals:**
    *   Initialize a FastAPI project environment.
    *   Design the Relational SQL Model for the `User` table (including fields for ID, email, hashed password, and is_active status).
    *   Set up the database connection (PostgreSQL) and migration tool (like Alembic).
*   **Deliverables:**
    *   A Python file defining the SQLAlchemy (or SQLModel) User class.
    *   A successfully generated database file (or table) matching the schema.
    *   A basic `GET /health` endpoint to verify the API is running.

---

### **Lab 2: Secure User Registration**
**Context:** Now that the database exists, students need to populate it. This lab covers "Implement secure password hashing with bcrypt."

*   **Goals:**
    *   Create Pydantic schemas for User Registration (handling input validation).
    *   Implement the `bcrypt` hashing algorithm to convert raw passwords into hashes.
    *   Build the `POST /register` endpoint to save the user to the database.
*   **Deliverables:**
    *   A helper function `hash_password(password: str)`.
    *   A working `/register` endpoint.
    *   **Verification:** A database check showing that the password column contains a hash string (e.g., `$2b$12$...`) rather than "plain_text_password".

---

### **Lab 3: Issuing Tokens (The Login Flow)**
**Context:** This lab bridges the gap between the database and the client. It covers "Learn JWT structure" and creating the token.

*   **Goals:**
    *   Implement a password verification function (comparing input against the stored hash).
    *   Construct the JWT payload (Subject, Expiration, Claims).
    *   Sign the JWT using a secret key and an algorithm (HS256).
    *   Build the `POST /login` (or `/token`) endpoint.
*   **Deliverables:**
    *   A helper function `verify_password()`.
    *   A helper function `create_access_token()`.
    *   A working `/login` endpoint that accepts credentials and returns a JSON response: `{"access_token": "ey...", "token_type": "bearer"}`.
    *   **Task:** Students must decode their generated token (using a tool like jwt.io) to inspect the Header, Payload, and Signature structure.

---

### **Lab 4: Protecting Routes & The Request Lifecycle**
**Context:** This is the core of the module. It covers "Understand FastAPI request lifecycle" and "Develop authentication middleware."

*   **Goals:**
    *   Create a dependency function (Middleware) that intercepts requests.
    *   Implement logic to decode the JWT and validate the signature.
    *   Retrieve the user from the database based on the token payload (request injection).
    *   Create a protected route (e.g., `GET /users/me`) that requires a valid token.
*   **Deliverables:**
    *   A `get_current_user` dependency.
    *   A protected endpoint `/me` that returns the current user's profile data.
    *   **Test:** Attempting to access `/me` without a token should return a `401 Unauthorized` error; accessing it with a token returns `200 OK`.

---

### **Lab 5: Token Expiration & Refresh Strategies**
**Context:** Making the system production-ready. This covers "Handle token expiration and implement refresh token strategies."

*   **Goals:**
    *   Modify the token creation logic to set short expiration times for Access Tokens (e.g., 15 minutes) and long expiration for Refresh Tokens (e.g., 7 days).
    *   Update the database schema (or store logic) to handle refresh tokens if utilizing a whitelist/blacklist approach.
    *   Build a `POST /refresh` endpoint.
*   **Deliverables:**
    *   Updated login response containing both `access_token` and `refresh_token`.
    *   A working `/refresh` endpoint that accepts a valid refresh token and returns a *new* access token.
    *   **Scenario Test:** Student must demonstrate that when an access token expires, the client can use the refresh endpoint to regain access without re-entering a password.