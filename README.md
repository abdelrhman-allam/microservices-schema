# microservices-schema
Project describe the folder structure for a micro-services based

# Overview
This project is a microservices-based architecture for building web applications using Ruby on Rails and Docker. The project includes a folder schema that can be easily added to any repository, making it easy to create and manage microservices on a large scale.

# Getting Started
To get started with this project, follow the steps below:

1. Clone the repository to your local machine.
2. Install Docker and Docker Compose if not already installed.
3. In the root directory of the project, run `docker-compose up -d` to start the containers.
4. Access the services by navigating to `localhost` on your web browser.

# Folder Structure
```
Project Root
├── docker
│   ├── common
│   │   ├── database
│   │   ├── rabbitmq
│   │   ├── redis
│   │   └── rails
│   ├── gateway
│   │   ├── config
│   │   │   ├── routes.rb
│   │   │   └── settings.yml
│   │   └── Dockerfile
│   ├── nginx
│   │   ├── config
│   │   │   └── nginx.conf
│   │   └── Dockerfile
│   ├── docker-compose.yml
│   ├── docker-compose.override.yml
│   ├── docker-compose.common.yml
│   └── deploy.sh
└── shopping
    ├── catalog_service
    │   ├── docker
    │   │   └── Dockerfile
    │   ├── docker-compose.yml
    │   ├── docker-compose-common.yml
    │   ├── docker-compose.production.yml
    │   ├── docker-compose.override.yml
    │   └── script
    │       ├── .git
    │       │   └── hooks
    │       │       ├── pre-commit
    │       │       └── pre-push
    │       ├── setup.sh
    │       └── deploy.sh
    ├── customer_service
    │   └── ... same as catalog_service
    └── order_service
        └── ... same as catalog_service
```

The folder structure is organized as follows:

The `docker` folder contains the Dockerfiles and configuration files for the various services.

- The `common` folder contains shared configuration files for services that need them.
- The `gateway` folder contains the gateway service for the project, and its subfolder `config` contains the routes and settings files.
- The `nginx` folder contains the web server for the project, and its subfolder `config` contains the nginx configuration file.

The `docker-compose.yml` file is the main Docker Compose configuration file for the project. The `docker-compose.override.yml` file is used for overriding settings in the main configuration file. The `docker-compose.common.yml` file contains shared settings that can be included in other configuration files.

The `shopping` folder contains the microservices for the shopping application. Each service has its own folder with its own Docker Compose configuration files and any other necessary files.

The `catalog_service`, `customer_service`, `order_service` folder contains the microservice for the order functionality, and its `docker` folder contains the Dockerfile for building the container.

The `.git` folder within the `script` folder contains Git hooks that ensure code committed to the repository meets certain standards and runs correctly. 

- The `pre-commit` hook checks for syntax errors and style issues, and 
- The `pre-push` hook runs tests to ensure the code runs correctly before pushing to the remote repository. 

By using these Git hooks, the repository can ensure high-quality code and save time in the long run.

# Build and Test
To build and test the project, follow the steps below:

1. In the root directory of the project, run `docker-compose build` to build the containers.
2. In the root directory of each service, run `docker-compose -f docker-compose.test.yml run app bundle exec rake test` to run the tests using the `docker-compose.test.yml` file.

# Contribute
We welcome contributions to this project. To contribute, follow the steps below:

1. Fork the repository and clone it to your local machine.
2. Make your changes and create a pull request.
3. Ensure that your code passes all tests and follows the project's coding standards.
4. A maintainer of the project will review your changes and merge them if they meet the project's requirements.

Thank you for your interest in contributing to this project!
