# Laravel API for Order Processing

This Laravel project implements a login, register and logout functionalities using JWT Autentication

## Table of Contents

- [Stage 01](#stage-01)
- [Stage 02](#stage-02)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Web Form](#web-form)
- [Queueing API Requests](#queueing-api-requests)
- [License](#license)

## Stage 01

### 1. REST API endpoint for user login

- API endpoint: `/api/login`
- HTTP Method: POST
- Request Body Parameters:
    - User email
    - User Password
- API response includes:
    - User Object
    - Token

### 2. REST API endpoint for user registration

- API endpoint: `/api/register`
- HTTP Method: POST
- Request Body Parameters:
    - User email
    - User name
    - User Password
- API response includes:
    - User Object
    - Token


## Getting Started

These instructions will help you set up and run the project on your local machine.

### Prerequisites

- [PHP 7.3](https://www.php.net/manual/en/install.php)
- [Composer](https://getcomposer.org/download/)
- [Node.js v14.6](https://nodejs.org/)
- [MySQL 8](https://www.mysql.com/)

### Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/Liyanamanasampath/spot-test.git


2. Navigate to the project directory:

   ```sh
   cd your-project

3. Navigate to the project directory:

   ```sh
   unzip


4. Install composer dependencies:

   ```sh
   composer install

5. Install npm dependencies:

   ```sh
   npm install


6. Create a .env file:

   ```sh
   cp .env.example .env


7. Generate an application key:

   ```sh
   php artisan key:generate


8. Install JWT:

   ```sh
   php artisan jwt:secret


9. Configure your database settings in the .env file:

   ```sh
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=your_database_name
    DB_USERNAME=your_database_username
    DB_PASSWORD=your_database_password

10. Artisan commands:

```sh
php artisan config:clear
php artisan config:cache
composer dump-autoload
```


11. Run migrations and seed the database::

```sh
php artisan migrate --seed
```


12. Start the artisan server:

    ```sh
    php artisan serve
    ```

13. Start the npm:

    ```sh
    npm run watch
    ```

### 1. Login to the system using the following login details.
I have use JWT Authentication mechanism for authenticate users and I already added the admin user to database using Laravel Seedr
- Login Details:
    - Email: admin@gmail.com
    - Password: 123456


### 2. Difficulties when implementing this solution

- I have created all the functionalities with Laravel and Vue js (login, register, logout, view profile) and I used the authentication as JWT but after completing the assigment I have faced issue with GitHub authentication when pushing my code base to remote repository.
- Using SSH I have overcome this issue and pushed my code to new branch (develop) and make it as default branch.
