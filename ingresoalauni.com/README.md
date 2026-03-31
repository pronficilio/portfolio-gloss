# Ingreso a la Uni / SAINS

Legacy PHP web application for marketing, enrolling, and supporting university entrance-exam preparation programs.

## Overview

This repository combines a public-facing website, course and guide registration microsites, and an authenticated SAINS learning portal. The codebase centers on PHP entry points, MySQL-backed persistence, and bundled front-end assets committed directly in the repository. Beyond marketing pages, the repo includes student login flows, study content delivery, admin screens, and specialized upload modules for photographs and payment receipts.

## Key Features

- Public landing pages for entrance-exam preparation programs, plans, and contact flows.
- Email, Google, and Facebook-based user onboarding and login paths.
- Authenticated SAINS portal with videos, simulators, results, and study history views.
- Separate admin area for operational workflows such as users, payments, exams, questions, and coupons.
- UAEM-focused microsites for course registration and guide download flows.
- File upload endpoints for student photographs and payment receipts.
- Payment-related flows including Conekta/OXXO cash order generation and course payment instructions.

## Tech Stack

### Languages

- PHP
- JavaScript
- HTML
- CSS
- SQL

### Frontend

- Bootstrap
- jQuery
- SweetAlert
- DataTables
- Chosen

### Backend and Integrations

- PHPMailer
- Google API Client
- Vimeo API
- Conekta PHP SDK

### Datastore

- MySQL

### Infrastructure

- Apache-compatible PHP hosting
- Docker
- Docker Compose

## Architecture

- `index.php` is the public landing page and the main signup/login entry point.
- `php/` contains server-side handlers for registration, contact forms, mail delivery, and database helpers.
- `sains/` contains the authenticated student experience, the admin login, the admin module, upload services, and learning-content modules.
- `curso/` and `guiaUAEM/` are campaign-style microsites for course registration and guide-download flows.
- `assets/`, `images/`, and `img/` contain the static assets used by the public pages.
- `ingresoa_ingreso.sql` is the database dump included in the repository.

## Getting Started

This repository does not include a one-command local setup. The closest setup sources included in the repo are:

- `composer.json`
- `ingresoa_ingreso.sql`
- `php/database.php`
- `sains/Connections/sains.php`

Based on those files, a local environment needs:

- PHP with an Apache-compatible web server
- MySQL
- Composer

Module-level Docker definitions are available under `sains/fotografias/` and `sains/comprobantes/`, but the repository does not document a full monolith bootstrap command.

## Configuration

The repository does not provide a sanitized `.env.example`. Configuration is file-based and split across PHP include files under `php/`, `sains/Connections/`, and module-specific folders. Review those files locally before attempting to run the application, and do not publish any embedded credentials.

## Testing

No repository-level automated test, lint, or build commands were detected.

## CI/CD

No repository-level CI/CD configuration was found.

## Notes

- The codebase mixes public site code, application modules, and committed third-party front-end libraries inside the same repository.
- Upload-related Dockerfiles target specific modules rather than the full application.

## Contact

Add your public portfolio or contact details here.
