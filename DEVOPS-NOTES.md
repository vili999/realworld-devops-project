##### \## Step 1

Cloned an existing RealWorld full-stack application to use as a base for a DevOps portfolio project.
Installed project dependencies, verified Node.js, npm, Docker, and Docker Compose setup, and inspected the backend/frontend project structure and environment configuration.
Prepared local environment files for containerized development.

##### \## Step 2

Dockerized the backend application and created a Docker Compose setup with PostgreSQL.
Added a PostgreSQL healthcheck and configured the backend service to wait until the database is healthy before starting.
Verified the backend API is reachable at http://localhost:3001.



##### \## Step 3 Final Result

Successfully deployed a full-stack RealWorld application in a containerized local environment using Docker Compose.



Services included:

\- Frontend (React/Vite)

\- Backend API (Node.js/Express)

\- PostgreSQL database



Implemented:

\- Multi-container orchestration

\- Container networking

\- Environment variable configuration

\- PostgreSQL healthchecks

\- Dependency ordering with depends\_on



Verified successful communication between all containers and confirmed the application is accessible through the browser.



##### \## Step 4 — GitHub Actions CI/CD



Implemented a GitHub Actions CI pipeline triggered automatically on push and pull request events.



Created workflow file:



.github/workflows/ci.yml



Pipeline stages:

\- Checkout repository

\- Set up Node.js

\- Install dependencies

\- Build frontend application

\- Run automated tests with Vitest



The first pipeline run failed because the CI environment was missing the `jsdom` dependency required by Vitest.



Fixed by installing:



npm install -D jsdom



Committed and pushed the fix.



Verified that the GitHub Actions pipeline completed successfully.



