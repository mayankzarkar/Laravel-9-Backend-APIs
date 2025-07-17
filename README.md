# Laravel 9 Backend APIs

A modular, multi-tenant backend API boilerplate built with Laravel 9, designed to accelerate development of SaaS and multi-tenant applications. This repository includes boilerplate code for managing domains, products, categories, offers, inventory, and more, with robust support for tenant data isolation and AWS S3 integration.

## Getting Started

### Prerequisites

- PHP 8.0+
- Composer
- Laravel 9.x
- MySQL or PostgreSQL or SQLite
- AWS account (for S3 integration)
- Redis (optional, for queues/cache)

### Installation

1. **Clone the repository**
    ```bash
    git clone https://github.com/mayankzarkar/Laravel-9-Backend-APIs.git
    cd Laravel-9-Backend-APIs
    ```

2. **Install dependencies**
    ```bash
    composer install
    ```

3. **Copy `.env` and configure**
    ```bash
    cp .env.example .env
    # Edit .env and set DB, AWS, and tenancy configs
    ```

4. **Generate application key**
    ```bash
    php artisan key:generate
    ```

5. **Run migrations and seeders**
    ```bash
    php artisan migrate --seed
    ```

6. **Serve the application**
    ```bash
    php artisan serve
    ```

## API Overview

- All endpoints are prefixed with `/api`.
- Authentication uses Laravel Sanctum.
- Example endpoints:
  - `POST /api/login`
  - `GET /api/domain`
  - `POST /api/product`
  - `GET /api/inventory`
  - `POST /api/offer`

## Multi-Tenancy & S3 Buckets

- Each tenant gets a dedicated AWS S3 bucket for file storage.
- Tenancy is initialized by request data.
- Tenant-specific config is handled via bootstrappers (`TenancyBootstrappers`).

## Role and Permission Management

- Roles: `superadmin`, `admin`, `staff`
- Permissions defined in `database/seeders/RoleSeeder.php`

## Project Structure

- `app/Services/` - Business logic for main entities
- `app/Models/` - Eloquent models
- `app/Requests/` - Form request validation
- `database/seeders/` - Seeder classes for roles, tenants, posts, etc
- `routes/api.php` - API routes
