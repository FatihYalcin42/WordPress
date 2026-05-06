# WordPress Course Project

This repository contains a Docker-based WordPress setup with a MySQL database for the course project.
It provides a simple way to run WordPress on a server, keep database data persistent, and preserve uploaded media files across restarts.

## Table of Contents

- [Repository Description](#repository-description)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Quickstart](#quickstart)
- [Usage](#usage)
- [Configuration](#configuration)
- [Persistence](#persistence)
- [Security Notes](#security-notes)
- [Contributing](#contributing)

## Repository Description

The purpose of this repository is to provide a reproducible WordPress environment for development and deployment with Docker Compose.
The setup includes:

- a `wordpress` service for the web application
- a `db` service for MySQL
- persistent storage for database data
- persistent storage for WordPress files and uploads

## Project Structure

- `docker-compose.yaml`: Defines the WordPress and MySQL services, networks, restart behavior, and volumes
- `.env.example`: Example configuration file with the environment variables used by Docker Compose

## Requirements

- Docker
- Docker Compose
- A server or local machine with port `8080` available

## Quickstart

1. Clone the repository:

   ```bash
   git clone git@github.com:FatihYalcin42/WordPress.git
   cd WordPress
   ```

2. Create a local environment file:

   ```bash
   cp .env.example .env
   ```

> [!IMPORTANT]
> Adjust the values in `.env` before starting the project, especially the passwords.

3. Start the project:

   ```bash
   docker compose up -d
   ```

4. Open WordPress in the browser:

   ```text
   http://<SERVER-IP>:8080
   ```

## Usage

The project is managed with Docker Compose.

Start the containers:

```bash
docker compose up -d
```

Stop and remove the running containers:

```bash
docker compose down
```

Check the container status:

```bash
docker compose ps
```

Validate the Docker Compose configuration before starting:

```bash
docker compose config
```

After the containers are running, complete the WordPress installation in the browser by creating the admin account and initial site configuration.

## Configuration

The project uses environment variables defined in `.env`.
The following variables are available in `.env.example`:

- `WORDPRESS_TAG`: WordPress image tag
- `MYSQL_TAG`: MySQL image tag
- `WORDPRESS_CONTAINER_NAME`: Container name for the WordPress service
- `DB_CONTAINER_NAME`: Container name for the database service
- `WORDPRESS_PORT`: Published host port for WordPress
- `WORDPRESS_DB_HOST`: Database host and port used by WordPress
- `WORDPRESS_DB_NAME`: MySQL database name
- `WORDPRESS_DB_USER`: MySQL user for WordPress
- `WORDPRESS_DB_PASSWORD`: MySQL password for the WordPress user
- `MYSQL_ROOT_PASSWORD`: MySQL root password

## Persistence

The project uses Docker volumes to keep important data across restarts:

- `db_data`: Persists MySQL database content
- `wordpress_data`: Persists WordPress files, including uploads and media

This allows the project to survive `docker compose down` and `docker compose up -d` without losing the installed site and uploaded files.

## Security Notes

- Do not commit the local `.env` file
- Do not store real passwords, tokens, SSH keys, or sensitive IP-based credentials in the repository
- Use strong passwords for `WORDPRESS_DB_PASSWORD` and `MYSQL_ROOT_PASSWORD`
- Keep administrative WordPress credentials outside the repository

## Contributing

1. Create a feature branch:

   ```bash
   git checkout -b feature/your-change
   ```

2. Commit your changes:

   ```bash
   git commit -m "Describe your change"
   ```

3. Push the branch:

   ```bash
   git push -u origin feature/your-change
   ```

4. Open a pull request against `main`.
