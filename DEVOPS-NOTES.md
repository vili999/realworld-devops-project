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


## Step 5 — Docker Image Validation in CI

Extended the GitHub Actions CI pipeline to validate Docker image builds for both backend and frontend services.

Added automated Docker build steps:
- Backend Docker image build
- Frontend Docker image build

Verified that container images can be successfully built in a clean CI environment during every push and pull request.

## Step 6 — Docker Build Optimization

Created a `.dockerignore` file to optimize Docker build context and reduce unnecessary files during image creation.

Excluded:
- node_modules
- Git metadata
- logs
- local environment files
- IDE settings
- coverage and build artifacts

Improved Docker build efficiency and reduced container build context size.

## Step 7 — Multi-stage Frontend Docker Build

Improved the frontend Dockerfile by using a multi-stage build.

Implemented:
- Node.js build stage for compiling the React/Vite application
- Nginx runtime stage for serving static production files
- Smaller and cleaner frontend container image
- Production-style container serving on port 80

Updated Docker Compose port mapping from `3000:3000` to `3000:80`.

Verified that the frontend is accessible at http://localhost:3000.

## Step 8 — Multi-stage Backend Docker Build

Improved the backend Dockerfile using a multi-stage build approach.

Implemented:
- Separate dependency installation stage
- Cleaner final runtime image
- Improved Docker layer caching
- Reduced unnecessary build complexity

Debugged workspace dependency behavior where npm installed dependencies in `/app/node_modules` instead of `/app/backend/node_modules`.

Verified that the backend container runs successfully and the API is reachable at http://localhost:3001.

## Step 9 — Backend Container Healthcheck

Added a backend container healthcheck to Docker Compose.

Implemented:
- Automated HTTP availability check for the backend API
- Health monitoring using Docker Compose healthcheck configuration
- Retry and timeout configuration for service validation

Verified that:
- PostgreSQL container reports healthy status
- Backend container reports healthy status
- Frontend container runs successfully

Confirmed successful multi-container orchestration with health monitoring.

## Step 10 — Container Restart Policies

Configured restart policies for frontend, backend, and PostgreSQL containers using:

restart: unless-stopped

Implemented automatic container recovery behavior to improve service reliability and resilience in case of crashes or Docker daemon restarts.

Verified that:
- Backend container is running and healthy
- PostgreSQL container is running and healthy
- Frontend container is running successfully

## Step 11 — Container Resource Limits

Configured CPU and memory limits for frontend, backend, and PostgreSQL containers.

Implemented:
- Memory limits using `mem_limit`
- CPU allocation using `cpus`

Verified runtime resource usage with Docker statistics monitoring.

Improved container resource management and production-style environment configuration.

## Step 12 — Environment Variable Templates

Created environment variable template files for configuration management.

Implemented:
- `.env.example` template files
- Separation of configuration templates from real secrets
- Improved project onboarding and deployment preparation
- `.gitignore` protection for sensitive environment files

Configured environment templates for:
- Backend application settings
- Database connection settings
- Development, testing, and production environments

Applied DevOps best practices for secret and configuration management.

## Step 13 — Monitoring Stack with Prometheus and Grafana

Added monitoring and observability services using Prometheus and Grafana.

Implemented:
- Prometheus metrics collection service
- Grafana visualization platform
- Docker Compose integration for monitoring stack
- Prometheus scrape configuration
- Grafana Prometheus datasource configuration

Created initial monitoring dashboard:
- Prometheus target status visualization
- Basic service availability monitoring using Prometheus `up` metric

Verified:
- Prometheus accessible on port 9090
- Grafana accessible on port 4000
- Successful communication between Grafana and Prometheus

Introduced DevOps monitoring and observability concepts into the project infrastructure.

## Step 14 — Docker Container Metrics Monitoring

Extended the monitoring stack with cAdvisor container metrics collection.

Implemented:
- cAdvisor service for Docker container monitoring
- Prometheus integration with cAdvisor metrics endpoint
- Container-level observability for Docker services

Configured Prometheus scrape targets for:
- Prometheus metrics
- cAdvisor container metrics

Verified:
- cAdvisor accessible on port 8080
- Prometheus targets reporting UP status
- Successful container metrics collection

Introduced container resource monitoring concepts including:
- CPU usage monitoring
- Memory usage monitoring
- Network metrics
- Filesystem metrics