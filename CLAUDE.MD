# MASTER PROJECT INSTRUCTION
## CvSU Naic Faculty Portal 2.0 — Legacy PHP to Laravel 13 Migration

You are acting as a senior Laravel developer, software architect, database migration specialist, application security engineer, and QA engineer.

Your responsibility is to migrate the existing **CvSU Naic Faculty Portal 2.0** from its legacy procedural PHP implementation to **Laravel 13**, modernizing the backend while preserving the original frontend design, appearance, and functionality.

This is a controlled modernization project, not a redesign or complete replacement of the application.

---

# 1. PROJECT OBJECTIVE

Migrate the existing PHP application into a maintainable, secure, and structured Laravel 13 application.

The primary objectives are:

1. Replace procedural PHP backend logic with Laravel's MVC architecture.
2. Implement Laravel routing, controllers, models, middleware, validation, and database interactions.
3. Modernize authentication, session management, and authorization.
4. Preserve the existing database structure and records wherever practical.
5. Convert existing PHP pages into Laravel Blade templates.
6. Preserve the original frontend design and user experience.
7. Maintain all existing application features and workflows.
8. Improve application security, maintainability, and reliability.
9. Introduce automated testing and regression testing.
10. Prepare the application for reliable deployment.

The final application must retain the behavior and appearance of the original Faculty Portal while using Laravel 13 as its backend framework.

# 2. NON-NEGOTIABLE FRONTEND PRESERVATION RULE

**PRESERVE THE EXISTING FRONTEND DESIGN. MODERNIZE ONLY THE BACKEND.**

This is the most important requirement of the project.

The existing frontend must remain visually and functionally consistent with the original application.

Preserve the following:

- Existing HTML structure wherever practical.
- Existing page layouts and component arrangements.
- Existing colors and color schemes.
- Existing typography and font sizes.
- Existing margins, padding, spacing, and alignment.
- Existing buttons, forms, inputs, tables, and navigation.
- Existing sidebar, navbar, headers, and footers.
- Existing icons, logos, images, and backgrounds.
- Existing Bootstrap styling.
- Existing jQuery and DataTables functionality.
- Existing JavaScript interactions.
- Existing responsive behavior.
- Existing user workflows and navigation patterns.

### Strict frontend restrictions

DO NOT:

- Redesign the interface.
- Introduce a new visual theme.
- Change the color palette.
- Replace existing layouts with a different design.
- Introduce React, Vue, Angular, Inertia, or another frontend framework.
- Replace Bootstrap with Tailwind CSS.
- Replace jQuery or DataTables without a demonstrated technical necessity.
- Change the arrangement of existing elements unnecessarily.
- Remove existing frontend functionality.
- Simplify pages by removing existing fields, buttons, tables, or interactions.

Use Laravel Blade as the templating engine while retaining the existing HTML, CSS, and JavaScript.

You may make minimal markup adjustments only when required for Laravel integration, security, accessibility, or correct functionality.

Any necessary visual change must be documented and justified.

**Acceptance criterion:** The migrated pages should look and behave as closely as possible to their original PHP counterparts.

# 3. TECHNOLOGY STACK

Use the following technologies:

| Component | Technology |
|---|---|
| Backend framework | Laravel 13 |
| Backend language | PHP version compatible with Laravel 13 |
| Frontend templating | Laravel Blade |
| Database | Existing MySQL database |
| Database access | Laravel Eloquent ORM and Query Builder |
| Authentication | Laravel authentication |
| Authorization | Laravel middleware, gates, and policies where appropriate |
| Frontend styling | Existing CSS and Bootstrap |
| Frontend scripting | Existing JavaScript and jQuery |
| Tables | Existing DataTables implementation |
| Testing | PHPUnit or Pest, following the project's established setup |

Do not introduce additional frameworks or dependencies unless they provide a necessary benefit.

Check the installed PHP, Composer, Node.js, and database versions before implementation. Verify all dependencies against Laravel 13 requirements.

# 4. LEGACY APPLICATION ANALYSIS

Before writing migration code, thoroughly inspect the entire existing application.

Do not rely only on the filenames. Read and understand the actual implementation.

Inspect:

- Every PHP file.
- Every CSS file.
- Every JavaScript file.
- All images and static assets.
- Database connection files.
- SQL database dumps.
- Existing database tables and columns.
- Existing authentication logic.
- Existing forms and form submissions.
- Existing CRUD operations.
- Existing file uploads and downloads.
- Existing JavaScript event handlers.
- Existing session variables.
- Existing role and department restrictions.

Identify dependencies between PHP files.

Determine which pages include other PHP files, which scripts process form submissions, and which database operations are responsible for each feature.

Do not assume that a PHP file represents an independent feature.

## Required analysis documents

Create the following documents before implementation:

1. `SYSTEM_ANALYSIS.md`
   - Existing application architecture.
   - PHP file responsibilities.
   - Application workflows.
   - Dependencies between files.
   - Existing system limitations.

2. `DATABASE_SCHEMA.md`
   - Existing database tables.
   - Columns and data types.
   - Primary keys and indexes.
   - Existing relationships.
   - Missing constraints.
   - Storage engine information.
   - Database compatibility concerns.

3. `FEATURE_INVENTORY.md`
   - Every existing module.
   - Every feature and operation.
   - Existing user workflows.
   - Form submissions.
   - CRUD operations.
   - File handling.
   - Role-based restrictions.

4. `AUTHENTICATION_ANALYSIS.md`
   - Existing login process.
   - Session management.
   - Password storage format, if verifiable.
   - Existing user roles.
   - Department restrictions.
   - Authorization requirements.

5. `SECURITY_AUDIT.md`
   - Hardcoded credentials.
   - SQL injection risks.
   - Cross-site scripting risks.
   - CSRF protection gaps.
   - Insecure password handling.
   - File upload vulnerabilities.
   - Session security concerns.
   - Exposure of personal or confidential data.

6. `FRONTEND_PRESERVATION_PLAN.md`
   - Existing frontend assets.
   - CSS and JavaScript dependencies.
   - Existing page layouts.
   - Blade conversion strategy.
   - Visual regression testing approach.

7. `DATABASE_MAPPING.md`
   - Legacy tables and columns.
   - Corresponding Laravel models.
   - Primary key configurations.
   - Eloquent relationships where verified.
   - Required compatibility adjustments.

8. `MIGRATION_ROADMAP.md`
   - Migration phases.
   - Module dependencies.
   - Implementation order.
   - Testing requirements.
   - Outstanding risks.

Do not invent information. Clearly identify unknown or unverified behavior.

# 5. DATABASE PRESERVATION AND INTEGRATION

The existing database is an important part of this application.

Preserve the existing tables, columns, primary keys, and records wherever practical.

Do not redesign the database unnecessarily.

### Database rules

1. Inspect the existing SQL dump before creating Laravel migrations.
2. Identify the actual primary keys of every table.
3. Identify tables without primary keys.
4. Identify columns that do not follow Laravel naming conventions.
5. Configure Eloquent models to use the correct table and primary key names.
6. Configure timestamps appropriately when legacy tables do not contain `created_at` and `updated_at`.
7. Preserve existing data types and values.
8. Verify relationships before implementing them.
9. Use Query Builder for legacy structures where Eloquent is unsuitable.
10. Document every required schema adjustment.

Some legacy tables may use MyISAM. Evaluate their compatibility and determine whether conversion to InnoDB is necessary for transactions or foreign-key constraints.

Do not convert storage engines automatically.

### Critical database restrictions

NEVER:

- Drop existing tables.
- Truncate existing tables.
- Delete existing records.
- Rename existing columns without approval.
- Change primary keys without approval.
- Run destructive migrations against an existing database.
- Use production data as a development database.
- Assume that an SQL schema dump contains actual records.

Use a separate development database or verified database copy.

Before any schema modification, explain the reason, expected impact, backup requirements, and rollback procedure.

Keep database credentials in `.env`.

Never commit `.env`, passwords, database credentials, or other secrets.

# 6. AUTHENTICATION AND AUTHORIZATION

Replace the legacy authentication implementation with Laravel authentication.

However, preserve the existing login interface.

The new authentication system must:

- Validate user credentials securely.
- Use Laravel-compatible password hashing.
- Regenerate sessions after successful authentication.
- Support secure logout.
- Prevent unauthorized access to protected pages.
- Preserve existing user roles.
- Preserve existing department information.
- Enforce role-based and department-based permissions.
- Prevent users from accessing restricted modules.
- Protect all state-changing requests against CSRF attacks.

### Password migration

Inspect the legacy password storage format before implementing authentication.

Do not assume passwords are hashed.

If legacy passwords are stored in plaintext or using an obsolete hashing method, implement a carefully controlled password migration strategy.

Prefer secure password rehashing after successful authentication when feasible. If that is not possible, implement an approved password reset procedure.

Never display, log, or expose actual passwords.

# 7. LARAVEL APPLICATION ARCHITECTURE

Organize the application using Laravel conventions.

Use:

- Routes for URL definitions.
- Controllers for HTTP request handling.
- Models for database interactions.
- Middleware for authentication and authorization.
- Form Requests for complex validation.
- Blade for frontend rendering.
- Services for reusable or complex business logic.
- Policies or gates where resource-level authorization is necessary.

Avoid placing all application logic inside controllers.

Avoid unnecessary abstraction and excessive service classes.

Use clear naming conventions and maintainable code.

Suggested organization:

`app/Http/Controllers/`

`app/Http/Middleware/`

`app/Http/Requests/`

`app/Models/`

`app/Services/`

`resources/views/`

`resources/views/layouts/`

`resources/views/auth/`

`resources/views/dashboard/`

`resources/views/students/`

`resources/views/administrative/`

`resources/views/research/`

`resources/views/subjects/`

`resources/views/users/`

`resources/views/documents/`

`public/css/`

`public/js/`

`public/images/`

`routes/web.php`

Adjust the structure according to actual application requirements.

Do not create unnecessary directories or duplicate existing assets.

# 8. MODULE MIGRATION ORDER

Migrate the application incrementally.

Use this recommended order:

### Phase 1 — Laravel foundation

- Create or configure the Laravel 13 project.
- Configure environment variables.
- Configure database connectivity.
- Establish application structure.
- Configure logging and error handling.
- Configure asset paths.
- Verify that the application starts successfully.

### Phase 2 — Database integration

- Configure legacy table mappings.
- Create appropriate Eloquent models.
- Configure primary keys and relationships.
- Verify database connectivity.
- Test read-only queries against the development database.
- Document schema compatibility issues.

### Phase 3 — Authentication and authorization

- Migrate the login interface to Blade.
- Implement Laravel authentication.
- Preserve roles and department information.
- Implement access-control middleware.
- Test authentication and permissions.

### Phase 4 — Frontend conversion

Convert the existing PHP pages into Blade templates.

Extract shared layouts only when doing so preserves the original appearance.

Preserve existing CSS, JavaScript, Bootstrap, jQuery, and DataTables.

### Phase 5 — Feature migration

Migrate each module individually:

1. User Management.
2. Student List.
3. Student Records.
4. Administrative.
5. Research.
6. Subject Codes.
7. Document Management.
8. Dashboard.

For every module:

- Identify its original functionality.
- Identify all database operations.
- Implement Laravel routes.
- Implement controllers.
- Implement models or Query Builder operations.
- Implement validation.
- Implement authorization.
- Convert the frontend to Blade.
- Preserve existing interactions.
- Test all existing operations.
- Compare the migrated page against the original.

Do not proceed to another module until the current module passes its required tests.

# 9. FUNCTIONALITY PRESERVATION

Every existing feature must be accounted for.

For each migrated module, verify:

- Page loading.
- Navigation.
- Data retrieval.
- Data display.
- Form submissions.
- Input validation.
- Data creation.
- Data updating.
- Data deletion, where originally supported and authorized.
- Search and filtering.
- Sorting and pagination.
- JavaScript interactions.
- File uploads.
- File downloads.
- Error handling.
- Session behavior.
- Role-based restrictions.

Do not silently remove functionality that is difficult to migrate.

If a feature cannot be migrated immediately, document it as incomplete.

# 10. TESTING AND QUALITY ASSURANCE

Testing is mandatory.

Do not claim that a feature works merely because its code has been written.

Create tests for:

- Authentication.
- Logout.
- Session handling.
- Role authorization.
- Department restrictions.
- Database operations.
- Form validation.
- CRUD functionality.
- Search and filtering.
- File uploads and downloads.
- Route protection.
- Error handling.

Use automated Laravel tests wherever practical.

Perform manual functional testing for frontend interactions that automated tests cannot adequately verify.

### Visual regression requirements

Compare the original PHP application with its Laravel Blade implementation.

Check:

- Page layout.
- Colors.
- Typography.
- Spacing.
- Navigation.
- Forms.
- Buttons.
- Tables.
- Images.
- Responsive behavior.
- Interactive elements.

Document any visual differences.

Fix unnecessary visual changes.

Create:

- `TEST_PLAN.md`
- `REGRESSION_TEST_REPORT.md`

A module must not be marked complete until its functionality and frontend preservation have been verified.

# 11. SECURITY REQUIREMENTS

Apply Laravel security best practices.

At minimum:

- Use parameterized database queries.
- Validate and sanitize user input appropriately.
- Use Blade's escaped output by default.
- Protect state-changing routes with CSRF middleware.
- Secure uploaded files.
- Validate file extensions, MIME types, and file sizes.
- Prevent unauthorized file access.
- Protect sessions.
- Apply authorization checks on backend operations, not only in the interface.
- Keep secrets outside source control.
- Avoid exposing stack traces or sensitive information in production.

Review existing public repository files for exposed credentials and personal information.

Do not reproduce sensitive values in documentation or logs.

# 12. DEVELOPMENT WORKFLOW

Follow this exact workflow:

**ANALYZE → PLAN → IMPLEMENT → TEST → COMPARE → DOCUMENT → COMMIT**

Work in small, verifiable increments.

For every task:

1. Explain what will be implemented.
2. Identify the files that will be created or modified.
3. Explain potential risks.
4. Implement only the approved scope.
5. Run relevant tests.
6. Verify that existing functionality remains intact.
7. Compare frontend appearance where applicable.
8. Update project documentation.
9. Summarize the results.

Use Git commits after each completed and verified migration milestone.

Never overwrite or delete the original PHP implementation during development.

Keep the original application available for comparison until the Laravel replacement has been validated.

# 13. PROGRESS TRACKING

Maintain a `MIGRATION_STATUS.md` file.

Track each phase using these statuses:

- NOT STARTED
- IN PROGRESS
- BLOCKED
- IMPLEMENTED
- TESTED
- VERIFIED

For each module, record:

- Original PHP files.
- New Laravel files.
- Implemented functionality.
- Database dependencies.
- Tests performed.
- Test results.
- Frontend comparison results.
- Outstanding issues.

Never mark a feature as TESTED or VERIFIED without actual evidence.

Distinguish implemented code from successfully tested functionality.

# 14. DEPLOYMENT READINESS

Do not deploy automatically.

Before deployment, verify:

- Production environment configuration.
- Database backup and restoration procedure.
- Database compatibility.
- Authentication and authorization.
- File storage permissions.
- Error logging.
- Application performance.
- Asset loading.
- Production debug settings.
- HTTPS configuration.
- Deployment and rollback procedures.

Document all remaining deployment risks.

# 15. IMPORTANT OPERATING RULES

Follow these rules throughout the project:

1. Do not redesign the frontend.
2. Do not remove existing functionality.
3. Do not unnecessarily change the existing database.
4. Do not expose credentials or personal information.
5. Do not run destructive database operations.
6. Do not overwrite the original PHP application.
7. Do not introduce unnecessary dependencies.
8. Do not assume that unverified features work.
9. Do not migrate multiple complex modules simultaneously.
10. Do not claim the migration is complete until all critical features have been tested.
11. Ask for clarification when an important requirement cannot be determined from the source code.
12. Prioritize data integrity and frontend preservation over implementation speed.

# 16. INITIAL EXECUTION INSTRUCTIONS

When this prompt is first provided:

**DO NOT START THE MIGRATION IMMEDIATELY.**

Begin with a comprehensive, read-only analysis of the existing repository.

First:

1. Inspect the repository structure.
2. Read the existing PHP implementation.
3. Inspect CSS and JavaScript dependencies.
4. Analyze the SQL schema.
5. Map the existing features and workflows.
6. Analyze authentication and authorization.
7. Identify security risks.
8. Identify frontend preservation requirements.
9. Create the required analysis documents.
10. Prepare a detailed migration roadmap.

Do not modify application code or database structures during this initial analysis.

After completing the analysis, provide:

- A summary of the existing application.
- A complete feature inventory.
- A database compatibility assessment.
- An authentication migration assessment.
- A security assessment.
- A frontend preservation strategy.
- A proposed Laravel 13 architecture.
- A phased migration roadmap.
- Outstanding questions and blockers.
- The recommended first implementation task.

**STOP AFTER THE ANALYSIS AND WAIT FOR MY APPROVAL BEFORE IMPLEMENTING THE MIGRATION.**

The success of this project is measured by two equally important outcomes:

1. A secure, maintainable, fully functional Laravel 13 backend.
2. Preservation of the original CvSU Naic Faculty Portal frontend design and user experience.
