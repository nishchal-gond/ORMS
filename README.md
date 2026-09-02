# ORMS — Online Marriage Registration System

A web application for submitting and processing marriage registration applications,
built with PHP and MySQL. Applicants register, submit an application and track its
status; administrators review applications, approve or reject them, and pull
date-range reports.

## Features

**Applicant side** (`user/`)

- Sign up, log in, password reset and profile management
- Submit a marriage registration application
- Track application status and view submitted details
- Search previously submitted applications

**Administrator side** (`admin/`)

- Dashboard with application counts
- Review new, approved and rejected applications
- Full application listing with detail views
- Reports filtered by date range
- Admin profile and password management

## Stack

| Layer | Used |
| --- | --- |
| Backend | PHP with PDO |
| Database | MySQL |
| Frontend | Bootstrap, jQuery, SCSS |
| Charts | Chart.js, Morris, Flot, Sparkline |

## Setup

Requires PHP with the PDO MySQL extension, and a MySQL server. XAMPP, WAMP or
MAMP all work.

1. **Clone into your web root**

   ```bash
   git clone https://github.com/nishchal-gond/ORMS.git
   ```

2. **Create the database and import the schema**

   ```sql
   CREATE DATABASE omrsdb;
   ```

   Then import `SQL File/omrsdb.sql` into it, via phpMyAdmin or:

   ```bash
   mysql -u root -p omrsdb < "SQL File/omrsdb.sql"
   ```

3. **Configure the database connection**

   Credentials are read in two places, and **both** need the same values:

   - `admin/includes/dbconnection.php`
   - `user/includes/dbconnection.php`

4. **Open the app**

   - Applicant portal — `http://localhost/ORMS/`
   - Admin portal — `http://localhost/ORMS/admin/`

## Demo accounts

`Readme.txt` contains sample login details for a freshly imported database. They
exist so the app can be tried immediately after setup.

> **These are demo values for a local install only.** They are published in this
> repository, so anyone can read them. Change both passwords before running this
> anywhere reachable from a network, and do not reuse them elsewhere.

## Project layout

```
admin/            Administrator portal
  includes/       Shared header, footer, sidebar, DB connection
  css/ js/ lib/   Bootstrap theme assets and chart libraries
  scss/           SCSS sources for the admin theme
user/             Applicant portal
  includes/       Shared header, footer, sidebar, DB connection
SQL File/         Database schema and seed data
index.php         Entry point for the applicant portal
```

## Notes

This was built as a learning project. Two things worth knowing before reusing it:

- The database connection details are committed rather than read from the
  environment, and are duplicated across `admin/` and `user/`. Moving them to a
  single file outside the web root would be the first change to make.
- Passwords and session handling follow the original tutorial structure and have
  not been audited. Review them before any real deployment.

## License

MIT — see [LICENSE](LICENSE).
