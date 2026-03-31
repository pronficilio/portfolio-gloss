# sigmacadit

Legacy PHP/MySQL medical operations web application with electronic clinical record workflows.

## Overview

`sigmacadit` is a monolithic server-rendered PHP application focused on day-to-day clinical and administrative operations. The repository includes authentication, permission-aware navigation, scheduling, patient intake, consultations, hospitalization, imaging, laboratory, rehabilitation, pharmacy, cash operations, user administration, branches, agreements, and partner-facing areas. It also commits SQL artifacts and several module-specific Dockerized upload handlers for documents and images.

## Key Features

- Role-based login and menu routing for reception, consultations, hospital, imaging, laboratory, rehabilitation, pharmacy, administration, cash, and partner areas.
- Scheduling flows for agenda management and order handling, including documented checks for doctor availability and overlapping appointments.
- Separate modules for patients, consultations, hospitalization, nursing, imaging, laboratory, social work, and pharmacy workflows.
- Administrative areas for users, branches, agreements, cash reporting, productivity dashboards, and partner operations.
- Document, photo, signature, logo, and clinical image upload handlers, with module-local Dockerfiles and Compose files for several upload services.

## Tech Stack

- Languages: PHP, JavaScript, HTML, CSS, SQL
- Frontend: Bootstrap, jQuery, jQuery UI, DataTables, Font Awesome, Bootstrap Validator
- Backend and data access: PHP, PDO, legacy `mysql_*`
- Database: MySQL
- Infrastructure: Docker, Docker Compose, Apache-based PHP containers
- Testing: No repository-level automated test configuration detected

## Architecture

- Top-level entry pages such as `login.php`, `index.php`, and `menu.php` drive authentication and role-aware navigation.
- Shared code is concentrated in `Connections/` (database access), `recursos/` (session and utility helpers), `partes/` (shared auth and header logic), `funciones/`, `htmls/`, and `remote_files/`.
- Domain modules live in directories such as `agenda/`, `consultas/`, `hospital/`, `imagen/`, `laboratorio/`, `trabajo_social/`, `farmacia/`, `usuarios/`, `caja/`, `seguros/`, `sucursales/`, and `asociados/`.
- Many modules repeat a consistent structure with `datatable-serverside/`, `files-serverside/`, `genera/`, and `htmls/` subfolders for AJAX endpoints, reports, generators, and UI partials.
- Database artifacts are committed in `nuevo-sigma (1).sql`, `todo.sql`, and `agenda/SQL/`, while upload and image subsystems include module-specific Docker assets.

## Getting Started

This repository does not include a one-command local setup. The closest source-of-truth files for local setup are `Connections/database.php`, `nuevo-sigma (1).sql`, `todo.sql`, `agenda/insertar_en_tabla_documentacion.txt`, and the module-specific Docker Compose files under `usuarios/`, `pacientes/`, `seguros/`, `sucursales/`, and `imagen/`.

Prerequisites:

- PHP with a web server capable of serving this repository as a web root
- MySQL
- Docker (optional, only for module-specific upload, image, and document handlers)

Suggested local setup based on repository evidence:

1. Provision a MySQL database using the committed SQL artifacts that apply to your environment.
2. Configure database connection settings in the PHP connection files under `Connections/`.
3. Serve the repository from a PHP-capable web root and open `login.php`.
4. If you need the module-local upload handlers, use the relevant `Dockerfile` and `docker-compose.yml` pairs inside those feature folders.

## Configuration

No `.env.example` or other environment template was detected. Configuration appears to be file-based:

- Database connectivity is wired through `Connections/database.php` and related files in `Connections/`.
- Module-local upload and image handlers use dedicated Docker assets such as `usuarios/documentos/Dockerfile` and `usuarios/documentos/docker-compose.yml`.

Do not publish credentials or hard-coded environment-specific settings from local copies of these files.

## Testing

No repository-level automated test suite or test command was detected.

## CI/CD

No repository-level CI/CD workflow configuration was detected.

## Notes / Trade-offs

- The repository commits a large amount of vendored frontend code directly into the project tree.
- Database access mixes PDO and legacy `mysql_*` usage, which suggests a long-lived codebase with incremental changes.
- Only selected upload, image, and document subsystems are containerized; the main application does not expose a single documented build or run command.

## Contact

Add a public portfolio, LinkedIn profile, or other public contact channel before publishing this README.
