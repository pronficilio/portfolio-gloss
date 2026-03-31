# RIC

Legacy PHP web application for accounting and records management.

## Overview
RIC is a server-rendered PHP application with an authenticated web interface and shared navigation across accounting and admin workflows.
The tracked entry points and menu structure show modules for movements, people, accounts, companies, users, and reports.
AJAX/DataTables endpoints under `datatable-serverside/` and module-specific `files-serverside/` directories back search, CRUD, and reporting flows.
This checkout looks like a legacy snapshot rather than a fully reproducible starter kit.

## Key Features
- Session-based login and access-restricted pages
- Management screens for movements, people, accounts, companies, and users
- Server-side DataTables grids with filtering, pagination, and export actions
- Policy and payment flows backed by MySQL tables such as `polizas`, `pagos`, `cuentas`, and `empresa`
- Document uploads for people and companies, plus PDF/XML attachments for policy records

## Tech Stack
- Languages: PHP, JavaScript, HTML, CSS
- Frontend: Bootstrap, jQuery, DataTables, Bootstrap Datepicker, Chosen, SweetAlert, Font Awesome, Bootstrap Validator
- Backend: PHP, PDO, legacy `mysql_*` APIs
- Database: MySQL
- Testing: No project-level automated test framework was found
- DevOps: No CI/CD or Docker configuration was found

## Architecture
- `Connections/`: database connection scripts used by pages and AJAX endpoints
- Root `*.php` pages: top-level authenticated screens such as `movimientos.php`, `personas.php`, `cuentas.php`, `empresas.php`, `usuarios.php`, and `reporte.php`
- `datatable-serverside/` plus module-level `*/datatable-serverside/`: server-side JSON endpoints for DataTables grids
- `*/files-serverside/`: form processing and CRUD handlers
- `*/takeArchivos/` and `usuarios/imagenes/`: file upload handlers for documents, images, PDF, and XML assets

## Getting Started
This repository does not include a one-command local setup; see `Connections/ric.php`, `Connections/database.php`, `login.php`, and `index.php`.

Based on the tracked code, a local environment would need:
- A PHP runtime that still supports legacy `mysql_*` calls as well as PDO
- A MySQL-compatible database configured through the tracked connection files
- A web server capable of serving the PHP entry points in the repository root

Important limitation:
- Several tracked modules reference additional connection files that are not present in this checkout, including `Connections/sigma.php`, `Connections/horizonte.php`, and `Connections/productores.php`. Because those files are missing, a complete local run cannot be verified from the repository alone.

## Configuration
- No `.env.example` or public configuration template is included
- Database settings are stored directly in `Connections/ric.php`
- Do not publish or reuse tracked credentials from connection files

## Testing
No project-level automated tests or test commands were found in the repository.

## CI/CD
No GitHub Actions, GitLab CI, Jenkins, or other project-level CI/CD configuration was found.

## Notes
- The codebase mixes PDO with legacy `mysql_*` access patterns
- Frontend dependencies are vendored directly into the repository instead of being managed from a root package manifest

## Contact
Replace this section with a public email address, LinkedIn URL, or portfolio contact before publishing.

