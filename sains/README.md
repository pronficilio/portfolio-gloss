# SAINS

Legacy PHP web application for university admission exam preparation, online course delivery, and practice exams.

## Overview

This repository contains the PHP entry points, MySQL access code, bundled frontend libraries, and content assets for SAINS, a Spanish-language preparation platform focused on university admission exams. The public entry point handles login, registration-related modals, contact, password recovery, and platform requirements. Authenticated pages expose course content, exam entry points, downloadable study guides, and video-based lessons. The tree also includes PHP endpoints for dynamic catalog lookups and a server-side DataTables feed for course videos.

## Key Features

- Public landing page with login, registration, contact, password recovery, and platform requirements UI.
- Session-protected member area for course access and exam-related flows.
- Online course screens with video listings, downloadable guides, podcasts, and mini-simulator views.
- Downloadable PDF study guides and printable exam materials bundled in the repository.
- Payment flows for PayPal checkout and Conekta-generated OXXO cash orders.
- Account verification flow based on a verification code sent by email.
- AJAX endpoints for dependent selectors covering states, municipalities, and preparatory schools.

## Tech Stack

- Languages: PHP, JavaScript, HTML, CSS, SQL
- Frontend: Bootstrap, jQuery, DataTables, jQuery UI, SweetAlert, Chosen, Bootstrap Datepicker, Select2
- Backend: PHP sessions, PDO, legacy `ext/mysql`
- Database: MySQL
- Integrations: PayPal, Conekta, Vimeo, Google Analytics

## Architecture

- `index.php`, `inicio.php`, `sains_online.php`, `admin.php`, `verificar_cuenta.php`: primary web entry points.
- `Connections/`: database bootstrap using both legacy MySQL connection helpers and PDO.
- `genera/`: lightweight PHP endpoints that populate dependent `<select>` inputs from MySQL queries.
- `documentos/`: bundled PDF guides, exam material, and subject-specific study content.
- `sains_online/htmls/`: HTML fragments for course dashboards, instructions, results, mini-simulators, and video dialogs.
- `sains_online/datatable-serverside/videos.php`: server-side JSON endpoint for DataTables-backed class and video listings.
- `bootstrap/`, `DataTables-1.10.13/`, `jquery-ui-1.10.2.custom/`: vendored frontend distributions committed to the repository.

At a high level, browser requests hit PHP entry points, which read session state, query MySQL tables, and render HTML views. Some screens then load additional content through AJAX endpoints for catalog data, video tables, and payment registration.

## Getting Started

### Prerequisites

- A PHP runtime with PDO MySQL and compatibility for legacy `mysql_*` calls
- A MySQL database containing the tables referenced in source code, including `usuarios`, `reactivos`, `tronco`, and `catalogo_preparatorias`
- A web server capable of serving this directory as a PHP application

### Local Run

This repository does not include a documented one-command local setup.

Evidence in the source suggests the following manual setup steps:

1. Review `Connections/sains.php` and `Connections/database.php` and replace the hard-coded database settings with local values.
2. Serve this directory through a PHP-capable web server and use `index.php` as the public entry point.
3. Ensure the required MySQL schema and seed data exist before attempting authenticated flows.

A clean local run cannot be guaranteed from this tree alone because several paths referenced by the PHP pages are not present in this snapshot, including `htmls/`, `files-serverside/`, `remote_files/`, `p_inicio/`, `funciones/`, `js/`, `imagenes/`, `vendor/`, and multiple `examen_*` directories.

## Configuration

- Database settings are stored directly in `Connections/sains.php` as PHP variables named `hostname_sains`, `database_sains`, `username_sains`, and `password_sains`.
- `Connections/database.php` creates a separate PDO connection from the same variables.
- `php.ini` defines local PHP overrides such as `upload_max_filesize = 10M` and `post_max_size = 10M`.
- No `.env.example` or environment-variable based configuration was found in this snapshot.

## Testing

No application-level test suite, lint command, or build script was found in this directory. The only test and lint files detected belong to vendored third-party libraries under `bootstrap/`, not to the SAINS application itself.

## CI/CD

No repository-level CI/CD configuration was found for this application directory. Historical CI files under `bootstrap/` belong to the vendored Bootstrap source tree rather than this project.

## Notes

- The repository appears to be a partial deployment snapshot rather than a fully reproducible development environment.
- Several source files reference dependencies outside this tree or in missing directories, which limits local reproducibility.
- Secrets are hard-coded in source files, so the project should be sanitized before any public release.
- The codebase mixes PDO with deprecated `mysql_*` APIs, which suggests legacy PHP runtime constraints.

## License

No repository-level license file was found.

## Contact

Portfolio contact: add a public email address or LinkedIn URL here.
