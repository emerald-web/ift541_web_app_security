# Student Registration Web Application, Security Assessment

IFT 542, Web Application Security, Practical Assignment
Okenwa Emmanuel Ikechukwu, 2022/2/85805CF

## Important Notice, Fictitious Data Only

This project runs entirely on fictitious, self generated test data. No real student records, no real credentials, and no real personal information are used anywhere in this repository. The single seeded test account (student1@local.edu) is a made up example created solely for demonstrating and testing the security controls below. All testing was carried out against this self built, isolated prototype only, in accordance with the ethical and legal requirements described in docs/ethics_statement.md.

## What This Is

A prototype Student Registration Web Application built to demonstrate, for each of Task 1, Task 2, and Task 3 of the assignment, a working vulnerability and a working, tested fix, grounded in the IFT 542 course handout. The application supports student login, profile updates, course registration, document upload, and administrative management of courses and enrolments.

## Main Report

See docs/IFT542_Assignment_Report.docx for the full written report, covering all three tasks with explanations, code, and evidence screenshots.

## Requirements

PHP 8.1 or later, with the pdo_sqlite extension enabled. No external libraries or Composer packages are required. See docs/SBOM.md for full dependency details.

## Setup Instructions

Run these commands once, in order, from the project root, before running any tests or starting the server.

```
php setup_db.php
php add_attempts_table.php
php add_logs_table.php
php rehash_passwords.php
```

This creates database/student_registration.sqlite with one seeded, fictitious test student.

```
Username: student1@local.edu
Password: StudentPass123!
```

## Running the Application Locally

```
php -S 127.0.0.1:8877 -t .
```

Then visit, for example, http://127.0.0.1:8877/src/profile/profile_secure.php in a browser or with curl. All requests should be made only against this local instance.

## Running the Tests

Each file in tests/ can be run directly, for example:

```
php tests/task2_auth_test.php
```

This runs the consolidated Task 2 automated test suite, covering valid login, invalid credential rejection, SQL injection neutralisation, and secure password storage, all in one pass.

For tests involving sessions, pass a session save path.

```
php -d session.save_path=/tmp tests/test_lockout.php
```

## Project Structure

- src/auth/, login logic, vulnerable and secure versions
- src/profile/, profile display and update, vulnerable and secure versions
- src/urlpreview/, SSRF demonstration, vulnerable and secure versions
- src/config/, database connection and environment configuration
- src/utils/security.php, shared functions for escaping, CSRF, security headers, and logging
- tests/, all exploit demonstrations and secure version proofs
- docs/, the full report, the data flow diagram, evidence images, request and response captures, and supporting documents

## Supporting Documents

- docs/SBOM.md, software bill of materials
- docs/ethics_statement.md, signed ethics statement
- docs/incident_response_runbook.md, one page incident response runbook
- docs/task1_dfd.mmd, Mermaid source for the data flow diagram
- docs/request_response_capture/, real HTTP request and response captures for key endpoints

## Ethics Note

All testing described in this project was carried out exclusively against this self built, isolated prototype, using entirely fictitious data. No real system, real credentials, or real personal data were used at any point. See docs/ethics_statement.md for the full statement.
