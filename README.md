# Laravel API - Secure & Best Practices

A production-ready Laravel API boilerplate implementing modern best practices for security and structure.

## Features

- **Authentication**: Secure Token-Based Authentication using [Laravel Sanctum](https://laravel.com/docs/sanctum).
- **API Versioning**: Scalable `v1` namespace structure.
- **Standardized Responses**: Consistent JSON response format using `ApiResponse` trait.
- **Security**:
  - Rate Limiting
  - Input Validation
  - Password Hashing (Bcrypt)
  - CSRF Protection (where applicable)

## Installation

1.  **Clone the repository**
    ```bash
    git clone <repo-url>
    cd laravel-api-creation-secure
    ```

2.  **Install Dependencies**
    ```bash
    composer install
    ```

3.  **Environment Setup**
    ```bash
    cp .env.example .env
    php artisan key:generate
    ```

4.  **Database Setup**
    Configure your database in `.env`. For SQLite (default):
    ```bash
    touch database/database.sqlite
    php artisan migrate
    ```

5.  **Serve Application**
    ```bash
    php artisan serve
    ```

## API Documentation

The API uses standard HTTP verbs and status codes.

### Authentication

#### Register
- **Endpoint**: `POST /api/v1/register`
- **Body**:
  ```json
  {
      "name": "John Doe",
      "email": "john@example.com",
      "password": "password",
      "password_confirmation": "password"
  }
  ```
- **Response**: `201 Created` with Auth Token.

#### Login
- **Endpoint**: `POST /api/v1/login`
- **Body**:
  ```json
  {
      "email": "john@example.com",
      "password": "password"
  }
  ```

#### Get User Profile
- **Endpoint**: `GET /api/v1/user`
- **Headers**: `Authorization: Bearer <token>`

#### Logout
- **Endpoint**: `POST /api/v1/logout`
- **Headers**: `Authorization: Bearer <token>`

## Project Structure

- `app/Http/Controllers/Api/V1`: API Controllers (e.g., `AuthController`).
- `app/Traits/ApiResponse.php`: Standardized response helper.
- `routes/api.php`: API Routes definition.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
