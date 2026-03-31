# sigue

Laravel 6 education platform for student enrollment, learning content, assessments, messaging, and payment operations.

## Overview

This repository contains a Laravel 6 monolith with both web and API entry points. The codebase combines Blade views, a large REST-like API, generated API documentation, and Vue-based chat components. Its tracked modules cover student records, enrollment requests, content delivery, exams, tasks, notifications, and collections workflows. Student-facing views reference the "Entrenator" brand, while the route layer also shows dependency on an external frontend host through `URL_QUASAR`.

## Key Features

- Student and enrollment workflows, including requests, custom registration fields, package assignment, groups, grades, scholarships, and notifications
- Learning-content modules for topics, videos, documents, resources, glossary entries, and lesson-planning imports
- Assessment flows for question banks, exams, answer submission, grading, attendance, notes, and topic completion
- Real-time chat backed by Laravel broadcasting, Echo/Pusher, and Vue components
- Payment and collection integrations for Mercado Pago, Conekta/PayPal, BBVA, and Santander flows
- Bulk spreadsheet imports for students, groups, users, and planning data
- Generated API reference pages under `resources/docs/1.0`

## Tech Stack

- Languages: PHP, JavaScript, Blade, SCSS
- Frontend: Vue 2, Bootstrap 4, Laravel Echo
- Backend: Laravel 6, Laravel Passport, Laravel Socialite, LaRecipe, LaRecipe Swagger, Laravel Excel
- Data: MySQL is the default connection in `config/database.php`
- External services: Pusher, Vimeo, Mercado Pago, Conekta, PayPal, BBVA, Santander
- Tooling: Composer, npm, Webpack, Laravel Mix, StyleCI, PHPUnit

## Architecture

- `routes/api.php` exposes the main API surface for academic, messaging, finance, and operations workflows.
- `routes/web.php` provides web/admin routes, authentication redirects, and student-facing entry points.
- `app/Http/Controllers` contains API controllers, web controllers, auth flows, and repository-style service classes.
- `database/migrations` defines the relational model for users, content, exams, payments, schedules, notifications, and academic records.
- `resources/views` contains Blade templates for admin pages, emails, and student-facing screens.
- `resources/js` contains the Vue chat client and the Echo/Pusher bootstrap code.
- `resources/docs/1.0` stores generated endpoint documentation.

At a high level, requests enter through Laravel routes, flow into controllers and Eloquent-backed models, and then surface through Blade views, JSON endpoints, or broadcast events consumed by the Vue chat client.

## Getting Started

### Prerequisites

- PHP 7.2+ and Composer
- Node.js and npm
- A database supported by Laravel 6; the default config targets MySQL
- A frontend host configured for `URL_QUASAR` redirects if you need the login or student-panel routes

### Local Setup Notes

This repository does not include a tracked `.env.example` or a one-command local setup.

Detected repository-defined commands:

```bash
npm run dev
npm run watch
npm run hot
npm run prod
php artisan santander:process
php artisan colegiatura:cobrar
php artisan send:access
```

If you need a full local environment, review `composer.json`, `package.json`, `config/database.php`, and `routes/web.php` before wiring PHP dependencies, database settings, and the external frontend URL.

## Configuration

No sanitized `.env.example` is tracked in this snapshot. Environment-driven settings are referenced across Laravel config files such as `config/database.php`, `config/mail.php`, `config/broadcasting.php`, and `config/vimeo.php`, and web routing depends on `URL_QUASAR` in `routes/web.php`.

## Testing

`phpunit.xml` configures PHPUnit `Unit` and `Feature` suites, but the repository does not define a Composer or npm test script. The tracked checkout also does not include `tests/bootstrap.php`, `tests/Unit`, or `tests/Feature`, so there is no repo-verified test command to publish here beyond the PHPUnit configuration itself.

## CI/CD

No CI workflow configuration was detected in the tracked files. There is no `.github/workflows`, `Jenkinsfile`, or `.gitlab-ci.yml` in this checkout.

## Notes / Trade-offs

- The student login and panel routes redirect to `URL_QUASAR`, which suggests this repository is only one part of the deployed application.
- Docker, Docker Compose, and a tracked `.env.example` are not present, so reproducible local setup requires manual environment assembly.

## License

`composer.json` declares the project license as MIT.

## Contact

Replace this section with your preferred portfolio URL, LinkedIn profile, or public contact channel.
