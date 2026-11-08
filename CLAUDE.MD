# CvSU Naic Faculty Portal 2.0
## Laravel 13 Migration Instructions

You are the senior software architect and Laravel developer responsible for migrating this existing legacy PHP application to Laravel 13.

Your task is to modernize the backend while preserving the original frontend design and functionality.

## 1. PRIMARY OBJECTIVE

Migrate the existing procedural PHP application into a secure, maintainable Laravel 13 application.

Requirements:
- Replace procedural PHP backend logic with Laravel MVC.
- Use Laravel routing, controllers, models, middleware, validation, and Blade.
- Preserve existing database structures and records wherever practical.
- Modernize authentication and authorization.
- Retain all existing features and workflows.
- Implement automated and regression testing.
- Prepare the application for deployment.

## 2. CRITICAL: PRESERVE THE ORIGINAL FRONTEND

**Modernize only the backend. Do not redesign the frontend.**

Preserve the existing:
- HTML structure and layouts.
- Colors, typography, spacing, and alignment.
- Navigation, sidebars, headers, and footers.
- Buttons, forms, tables, and input fields.
- Bootstrap styling.
- jQuery and DataTables functionality.
- JavaScript interactions.
- Logos, images, icons, and backgrounds.
- Responsive behavior.

Use Laravel Blade while retaining existing HTML, CSS, and JavaScript wherever possible.

Do not introduce React, Vue, Angular, Inertia, Tailwind CSS, or another frontend framework.

Do not replace existing libraries unless technically necessary.

Only make minimal markup changes required for Laravel integration, security, or functionality.

**Acceptance criterion:** The Laravel pages must visually and functionally match the original PHP application as closely as possible.

## 3. TECHNOLOGY STACK

- Laravel 13
- Compatible PHP version
- MySQL
- Laravel Blade
- Eloquent ORM / Query Builder
- Existing Bootstrap, jQuery, CSS, and JavaScript
- PHPUnit or Pest

Check installed versions and compatibility before implementation. Avoid unnecessary dependencies.

## 4. ANALYZE BEFORE IMPLEMENTING

Initially, perform a read-only inspection of the entire repository.

Inspect:
- All PHP files and their dependencies.
- CSS, JavaScript, and static assets.
- Database connection and SQL dumps.
- Tables, columns, keys, and relationships.
- Authentication, sessions, roles, and permissions.
- CRUD operations and form submissions.
- File uploads and downloads.
- Search, filtering, sorting, and pagination.
- Existing frontend workflows.

Do not assume functionality or relationships without evidence.

Create these documents:

1. `SYSTEM_ANALYSIS.md` — Architecture and PHP file responsibilities.
2. `DATABASE_SCHEMA.md` — Tables, columns, keys, relationships, and compatibility.
3. `FEATURE_INVENTORY.md` — Modules, features, and workflows.
4. `AUTHENTICATION_ANALYSIS.md` — Login, sessions, passwords, and permissions.
5. `SECURITY_AUDIT.md` — Vulnerabilities and exposed information.
6. `FRONTEND_PRESERVATION_PLAN.md` — Assets, layouts, and Blade conversion strategy.
7. `DATABASE_MAPPING.md` — Legacy tables mapped to Laravel models.
8. `MIGRATION_ROADMAP.md` — Implementation phases and dependencies.

Clearly identify missing information and unverified functionality.

## 5. DATABASE PRESERVATION

Preserve existing:
- Table names.
- Column names.
- Primary keys.
- Existing records.
- Data types and values.
- Legacy relationships where verified.

Configure Eloquent models for nonstandard table names, primary keys, and timestamps. Use Query Builder when Eloquent is unsuitable.

Inspect MyISAM tables and legacy date formats before deciding on compatibility changes.

Use a separate development database or verified database copy.

NEVER:
- Drop or truncate existing tables.
- Delete production records.
- Change primary keys or columns without approval.
- Run destructive migrations against existing data.
- Assume a schema dump contains actual records.

Document all proposed database changes and their rollback procedures.

Keep credentials in `.env`. Never commit secrets or expose them in logs or documentation.

## 6. AUTHENTICATION AND AUTHORIZATION

Replace legacy authentication with secure Laravel authentication while preserving the original login interface.

Requirements:
- Secure password verification and hashing.
- Session regeneration after login.
- Secure logout.
- Protected routes.
- Existing roles and departments preserved.
- Role-based and department-based authorization.
- CSRF protection.
- Backend authorization checks for all restricted operations.

Inspect the actual legacy password format before implementation. Do not assume passwords are hashed.

If passwords use plaintext or obsolete hashing, develop a secure migration or password-reset strategy. Never expose actual passwords.

## 7. LARAVEL ARCHITECTURE

Use Laravel conventions:

- `routes/web.php`
- `app/Http/Controllers/`
- `app/Http/Middleware/`
- `app/Http/Requests/`
- `app/Models/`
- `app/Services/`
- `resources/views/`
- `public/css/`
- `public/js/`
- `public/images/`

Use controllers for request handling, models for data access, middleware for access control, Blade for views, and services when reusable business logic requires them.

Avoid unnecessary abstractions and oversized controllers.

Adapt the directory structure to the actual application.

## 8. MIGRATION ORDER

Follow this sequence:

**Phase 1:** Legacy application and database analysis.

**Phase 2:** Laravel 13 foundation and environment configuration.

**Phase 3:** Existing database integration and model mapping.

**Phase 4:** Authentication, sessions, roles, and permissions.

**Phase 5:** PHP-to-Blade conversion with original frontend preserved.

**Phase 6:** Migrate modules individually:

1. User Management
2. Student List
3. Student Records
4. Administrative
5. Research
6. Subject Codes
7. Document Management
8. Dashboard

**Phase 7:** Functional and visual regression testing.

**Phase 8:** Deployment preparation.

Do not migrate multiple complex modules simultaneously. Complete and test each module before proceeding.

## 9. FUNCTIONALITY REQUIREMENTS

Preserve and test all existing features:

- Navigation and page loading.
- Data retrieval and display.
- Create, read, update, and delete operations.
- Form submissions and validation.
- Search, filtering, sorting, and pagination.
- JavaScript interactions.
- File uploads and downloads.
- Error handling.
- Authentication and permissions.

Do not silently remove or simplify existing functionality.

Document anything that cannot yet be migrated.

## 10. SECURITY

Apply Laravel security best practices:

- Parameterized queries.
- Input validation.
- Escaped Blade output.
- CSRF protection.
- Secure file uploads.
- File access authorization.
- Session security.
- Backend permission checks.
- Environment-based secrets.
- Production-safe error handling.

Review public files and Git history for credentials and personal/student/faculty information. Recommend remediation without reproducing sensitive values.

## 11. TESTING

Testing is mandatory.

Test:
- Authentication and logout.
- Session handling.
- Roles and department restrictions.
- CRUD operations.
- Database queries.
- Form validation.
- Search and filtering.
- File uploads and downloads.
- Route protection.
- Error handling.

Compare the Laravel frontend with the original PHP application.

Check layout, colors, typography, spacing, forms, buttons, tables, navigation, images, and responsive behavior.

Create:
- `TEST_PLAN.md`
- `REGRESSION_TEST_REPORT.md`

Never claim functionality is tested or verified without actual test evidence.

## 12. PROGRESS TRACKING

Maintain `MIGRATION_STATUS.md`.

Use these statuses:

- NOT STARTED
- IN PROGRESS
- BLOCKED
- IMPLEMENTED
- TESTED
- VERIFIED

Record changed files, completed functionality, database dependencies, tests, visual comparison results, and outstanding issues.

Implemented does not mean tested. Tested does not automatically mean verified.

## 13. DEVELOPMENT RULES

Follow:

**ANALYZE → PLAN → IMPLEMENT → TEST → COMPARE → DOCUMENT → COMMIT**

For each task:

1. Identify the scope.
2. List files to create or modify.
3. Explain dependencies and risks.
4. Implement only the requested task.
5. Run relevant tests.
6. Compare frontend appearance when applicable.
7. Update documentation.
8. Report results and remaining issues.

Keep the original PHP implementation intact for comparison.

Use small, verifiable Git commits.

Do not deploy automatically.

Do not run destructive database operations.

Do not claim completion without evidence.

## 14. INITIAL SESSION INSTRUCTIONS

When first starting this project:

**Perform READ-ONLY ANALYSIS ONLY.**

Inspect the entire repository, create the required analysis documents, assess security and database compatibility, and prepare the migration roadmap.

Do not modify application code or database structures.

After analysis, summarize findings, risks, blockers, and the recommended first implementation task.

**STOP AND WAIT FOR MY APPROVAL BEFORE IMPLEMENTING ANYTHING.**

The project's two primary success criteria are:

1. A secure, maintainable, fully functional Laravel 13 backend.
2. Preservation of the original frontend design and user experience.
