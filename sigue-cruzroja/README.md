# siguecruzroja

Laravel web application for student onboarding, course delivery, and related administrative workflows.

## Overview

This repository is a Laravel 6 application with server-rendered Blade views, a Vue/Laravel Mix frontend pipeline, and a large REST-style API surface.
Checked-in routes, controllers, and generated docs show modules for enrollment requests, course packages, topics, videos, resources, assignments, chats, exams, documents, and payment-related flows.
The repository also includes LaRecipe-based API documentation and PHPUnit test scaffolding.

## Key Features

- Student panel with package-based progress, notifications, rankings, and video progress tracking.
- Admin-facing CRUD flows for subjects/weeks, topics, questions, classes, schedules, videos, resources, documents, and student records.
- Enrollment/request workflows plus document collection and upload handling.
- Real-time chat built with Laravel broadcasting, Echo, Pusher, and Vue components.
- Documented API endpoints for students, packages, schedules, videos, tasks, chats, resources, charges, and related entities.

## Tech Stack

- Languages: PHP, JavaScript, SCSS, Blade, Markdown
- Frontend: Vue 2, Bootstrap 4, Axios, jQuery, Laravel Echo, Laravel Mix
- Backend: Laravel 6, Laravel Passport, Laravel Socialite, Yajra DataTables, Maatwebsite Excel, LaRecipe
- Datastores: MySQL (default), Redis
- Testing: PHPUnit
- Tooling: Composer, npm, Webpack, StyleCI, EditorConfig

## Architecture

- `routes/web.php` defines the server-rendered application flows and admin/student screens.
- `routes/api.php` exposes a large set of REST-style endpoints for the same domain model.
- `app/Http/Controllers` contains the feature logic, third-party integrations, and request handlers.
- `resources/views` contains Blade templates, while `resources/js` bootstraps Vue chat components and Echo/Pusher listeners.
- `database/migrations` and `database/seeds` describe schema evolution and seed data.
- `resources/docs/1.0` plus `config/larecipe.php` provide generated API documentation under `/docs`.

## Getting Started

### Prerequisites

- PHP 7.2+
- Composer
- Node.js and npm
- A configured database connection; Laravel defaults to `mysql` in `config/database.php`

### Local Setup

```bash
composer install
npm install
php artisan key:generate
npm run dev
```

This repository does not include a one-command local setup or a checked-in `.env.example`.
Use `composer.json`, `package.json`, and the files under `config/` as the source of truth, create your own Laravel environment file locally, and serve the application with your preferred PHP/Laravel web-server setup.

## Configuration

The checked-in config files reference standard Laravel application and infrastructure settings, including:

- `APP_NAME`, `APP_ENV`, `APP_DEBUG`, `APP_URL`, `APP_KEY`
- `DB_CONNECTION`, `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`
- `DB_DATABASE_MOR`, `DB_DATABASE_GUE`
- `MAIL_DRIVER`, `MAIL_HOST`, `MAIL_PORT`, `MAIL_USERNAME`, `MAIL_PASSWORD`, `MAIL_FROM_ADDRESS`, `MAIL_FROM_NAME`
- `VIMEO_CLIENT`, `VIMEO_SECRET`, `VIMEO_ACCESS`, `VIMEO_ALT_CLIENT`, `VIMEO_ALT_SECRET`, `VIMEO_ALT_ACCESS`

Audit committed service configuration carefully before publishing or deploying this project.

## Testing

The repository includes PHPUnit configuration plus sample unit and feature tests.
No npm test script is declared in `package.json`.

```bash
vendor/bin/phpunit
```

## CI/CD

No CI pipeline, Dockerfile, or docker-compose file was found in the repository.

## Notes

- No top-level setup guide or `.env.example` template is included.
- Some third-party configuration is committed in source files instead of being fully environment-driven.

## Contact

Portfolio contact: repository owner or maintainer.

