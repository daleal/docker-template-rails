# Docker Compose Template for Rails

This repository serves as an educational docker template over which to build a rails app.

## Getting Started

- Create a rails app:

    ```bash
    docker-compose run web rails new . --force --no-deps --database=postgresql
    ```

- Build the Docker image:

    ```bash
    docker-compose build
    ```

- Get ownership of the files (on linux they are owned by root when created):

    ```bash
    sudo chown -R $USER:$USER .
    ```

- Connect the database (replace the content of `config/database.yml` with the following):

    ```yaml
    default: &default
      adapter: postgresql
      encoding: unicode
      host: db
      username: postgres
      password:
      pool: 5

    development:
      <<: *default
      database: ENV["APP_HOME"]_development


    test:
      <<: *default
      database: ENV["APP_HOME"]_test
    ```

- Create the database:

    ```bash
    docker-compose run web rails db:create
    ```

## Useful Commands

- Build the Docker image:

    ```bash
    docker-compose build
    ```

- Start the server:

    ```bash
    docker-compose up
    ```

- Stop the server:

    ```bash
    docker-compose down
    ```

- Run rails `command` (`command` = `rails ...`):

    ```bash
    docker-compose run web `command`
    ```

- Get ownership of files created by rails generate (on linux they are owned by root when created):

    ```bash
    sudo chown -R $USER:$USER .
    ```
