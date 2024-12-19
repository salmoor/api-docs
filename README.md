# Backend

## Introduction

The Backend serves as the backbone of our platform, providing APIs, data processing, and other essential backend services. This document outlines the setup, development, testing, and deployment processes for the Backend within our monorepo.

## Table of Contents

- [Backend](#backend)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Development Environment Setup](#development-environment-setup)
    - [Available Services](#available-services)
  - [Directory Structure](#directory-structure)
  - [Development](#development)
    - [Conventions](#conventions)
    - [Laravel](#laravel)
    - [API Design](#api-design)
    - [Libraries and Tools](#libraries-and-tools)
    - [S3 Storage](#s3-storage)
  - [Testing](#testing)
    - [Using Bazel (TODO)](#using-bazel-todo)
    - [Using Sail](#using-sail)
  - [Deployment](#deployment)
  - [Contributing](#contributing)
  - [Troubleshooting](#troubleshooting)

## Development Environment Setup

1. Install PHP
2. [Install Composer](https://getcomposer.org/download/)
3. [Install Docker](https://docs.docker.com/get-docker/)
4. [Install DBeaver](https://dbeaver.io/download/)
5. [Install Xdebug](https://xdebug.org/docs/install)
6. [Install Insomnia](https://insomnia.rest/download)
7. [Install Redis Insight](https://redis.com/redis-enterprise/redis-insight/)
8. [Install VSCode](https://code.visualstudio.com/download) (Remember to enable Auto Save in VSCode right away.)
9. Install PHP dependencies
   1. php-redis
10. Install [Bazel](https://bazel.build/install/bazelisk)
11. Clone the monorepo
12. Create a `.env` file in the `applications/backend` directory:

   ```bash
   cp applications/backend/.env.example applications/backend/.env
   ```

  Ask a Backend Developer to Generate an Application Key for you and confirm the correctness of the other environment variables.

12. Start the development environment:

   ```bash
   bazel run //applications/backend
   ```

### Available Services

- **Search Engine (Meilisearch)**: [http://localhost:7700](http://localhost:7700)
- **Storage (Minio)**: [http://localhost:8900](http://localhost:8900)
- **Email Testing Tool (Mailpit)**: [http://localhost:8025](http://localhost:8025)
- **Backend Debug Assistant (Telescope)**: [http://localhost/telescope](http://localhost/telescope)
- **Queue System Monitor (Horizon)**: [http://localhost/horizon](http://localhost/horizon)

## Directory Structure

Backend Direcrory Structure follows the [Laravel Directory Structure](https://laravel.com/docs/10.x/structure) as closely as possible.

## Development

The following resources should aid you in your development process:

### Conventions

- [Bakkal Backend Development Conventions](./conventions/index.md)

### Laravel

- [Laravel Documentation](https://laravel.com/docs/9.x)
- [Laravel Best Practices](https://github.com/alexeymezenin/laravel-best-practices)
- [Additional Laravel Standards](https://github.com/Selectra-Dev/standards/blob/master/programming/LARAVEL.md#migrations)
- [Laracasts: Learn Laravel](https://laracasts.com/me)

### API Design

- [JSON:API Specification](https://jsonapi.org/)
- [JSON:API Atomic Operations](https://jsonapi.org/ext/atomic/)
- [Web API Design](https://hashingit.com/elements/research-resources/2012-web-api-design.pdf)
- [Google API design guide](https://cloud.google.com/apis/design)
- [Zalando RESTful API and Event Guidelines](https://opensource.zalando.com/restful-api-guidelines/#)
- [OpenAPI Specification](https://swagger.io/specification/)

### Libraries and Tools

- [FakerPHP / Faker](https://fakerphp.github.io/)
- [Money. PHP library to make working with money safer, easier, and fun!](https://github.com/moneyphp/money)
- [phpgeo - A Simple Geo Library for PHP](https://github.com/mjaschen/phpgeo)
- [Sentry: Application Performance Monitoring & Error Tracking](https://docs.sentry.io/platforms/php/guides/laravel/)
- [Laravel-backup](https://spatie.be/docs/laravel-backup/)
- [Laravel Settings](https://github.com/spatie/laravel-settings)
- [Stripe API](https://stripe.com/docs/api)
- [Twilio](https://www.twilio.com/docs/libraries/php)
- [YAML: YAML Ain't Markup Language™](https://yaml.org/)
- [PHPUnit Manual](https://phpunit.readthedocs.io/en/9.5/index.html#)
- [PHPStan Documentation](https://phpstan.org/user-guide/getting-started)
- [NEON Format](https://doc.nette.org/en/neon/format)
- [phpDocumentor](https://docs.phpdoc.org/)

### S3 Storage

* [Bucket policy examples](https://docs.aws.amazon.com/AmazonS3/latest/userguide/example-bucket-policies.html)

## Testing

### Using Bazel (TODO)

To run tests:
```bash
bazel test //applications/backend:tests
```

### Using Sail

```bash
cd applications/backend
vendor/bin/sail artisan test --parallel --coverage --min=95.0 --stop-on-failure
```

## Deployment

- In the staging environment, the Backend code is automatically deployed whenever a Pull Request is merged into the `main` branch.

- For the production environment, the Backend code undergoes automatic deployment on a daily basis.

## Contributing

1. Make sure you're familiar with the [General Monorepo Guidelines](../../../README.md).
2. Checkout our [Development Workflow](../../../docs/eng-practices/development/git-branching-model.md)
3. Before opening a Pull Request, make sure to check the [Pull Request Guidelines](../../../docs/eng-practices/review/index.md).

## Troubleshooting

If you are facing any issues with the setup, please reach out to any of the Backend Developers or check our [Team StackOverflow](https://stackoverflowteams.com/c/bakkal/questions).
