# Udagram Image Filtering Application

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

The project is split into two parts:
1. Frontend - Angular web application built with Ionic Framework
2. Backend RESTful API - Node-Express application

## Getting Started
> _tip_: it's recommended that you start with getting the backend API running since the frontend web application depends on the API.

### Prerequisite
1. The depends on the Node Package Manager (NPM). You will need to download and install Node from [https://nodejs.com/en/download](https://nodejs.org/en/download/). This will allow you to be able to run `npm` commands.
2. Environment variables will need to be set. These environment variables include database connection details that should not be hard-coded into the application code.

#### Environment Script
A file named `set_env.sh` has been prepared as an optional tool to help you configure these variables on your local development environment.
 
We do _not_ want your credentials to be stored in git. After pulling this `starter` project, run the following command to tell git to stop tracking the script in git but keep it stored locally. This way, you can use the script for your convenience and reduce risk of exposing your credentials.
`git rm --cached set_env.sh`

Afterwards, we can prevent the file from being included in your solution by adding the file to our `.gitignore` file.

### 1. Database
Create a PostgreSQL database either locally or on AWS RDS. The database is used to store the application's metadata.

* We will need to use password authentication for this project. This means that a username and password is needed to authenticate and access the database.
* The port number will need to be set as `5432`. This is the typical port that is used by PostgreSQL so it is usually set to this port by default.

Once your database is set up, set the config values for environment variables prefixed with `POSTGRES_` in `set_env.sh`.
* If you set up a local database, your `POSTGRES_HOST` is most likely `localhost`
* If you set up an RDS database, your `POSTGRES_HOST` is most likely in the following format: `***.****.us-west-1.rds.amazonaws.com`. You can find this value in the AWS console's RDS dashboard.


### 2. S3
Create an AWS S3 bucket. The S3 bucket is used to store images that are displayed in Udagram.

Set the config values for environment variables prefixed with `AWS_` in `set_env.sh`.

### 3. Backend API
Launch the backend API locally. The API is the application's interface to S3 and the database.

* To download all the package dependencies, run the command from the directory `udagram-api/`:
    ```bash
    npm install .
    ```
* To run the application locally, run:
    ```bash
    npm run dev
    ```
* You can visit `http://localhost:8080/api/v0/feed` in your web browser to verify that the application is running. You should see a JSON payload. Feel free to play around with Postman to test the API's.

<img width="826" alt="Screenshot 2022-05-19 at 14 42 38" src="https://user-images.githubusercontent.com/80678596/169296297-32cb6e4c-ae9f-4b53-bd80-0d7849c5b949.png">

### 4. Frontend App
Launch the frontend app locally.

* To download all the package dependencies, run the command from the directory `udagram-frontend/`:
    ```bash
    npm install .
    ```
* Install Ionic Framework's Command Line tools for us to build and run the application:
    ```bash
    npm install -g ionic
    ```
* Prepare your application by compiling them into static files.
    ```bash
    ionic build
    ```
* Run the application locally using files created from the `ionic build` command.
    ```bash
    ionic serve
    ```
* You can visit `http://localhost:8100` in your web browser to verify that the application is running. You should see a web interface.

<img width="730" alt="Screenshot 2022-05-19 at 14 43 05" src="https://user-images.githubusercontent.com/80678596/169296200-ad7a28f6-7f88-45e7-94ef-69551dc56c15.png">


<img width="1167" alt="Screenshot 2022-05-19 at 15 17 23" src="https://user-images.githubusercontent.com/80678596/169302463-804787a2-cc73-4578-bb69-6e57a59c25b8.png">

## Tips
1. Take a look at `udagram-api` -- does it look like we can divide it into two modules to be deployed as separate microservices?
2. The `.dockerignore` file is included for your convenience to not copy `node_modules`. Copying this over into a Docker container might cause issues if your local environment is a different operating system than the Docker image (ex. Windows or MacOS vs. Linux).
3. It's useful to "lint" your code so that changes in the codebase adhere to a coding standard. This helps alleviate issues when developers use different styles of coding. `eslint` has been set up for TypeScript in the codebase for you. To lint your code, run the following:
    ```bash
    npx eslint --ext .js,.ts src/
    ```
    To have your code fixed automatically, run
    ```bash
    npx eslint --ext .js,.ts src/ --fix
    ```
4. `set_env.sh` is really for your backend application. Frontend applications have a different notion of how to store configurations. Configurations for the application endpoints can be configured inside of the `environments/environment.*ts` files.
5. In `set_env.sh`, environment variables are set with `export $VAR=value`. Setting it this way is not permanent; every time you open a new terminal, you will have to run `set_env.sh` to reconfigure your environment variables. To verify if your environment variable is set, you can check the variable with a command like `echo $POSTGRES_USERNAME`.







#### Images of the docker images built

<img width="849" alt="Screenshot 2022-05-19 at 23 41 00" src="https://user-images.githubusercontent.com/80678596/169410434-a10cb221-812b-4e37-a98d-f5904e69a4b3.png">

#### Backend api feed

<img width="1438" alt="Screenshot 2022-05-19 at 23 48 41" src="https://user-images.githubusercontent.com/80678596/169410564-d0741e86-f1d3-4593-805c-9c72ebc3f03f.png">

#### Docker images running 

<img width="1315" alt="Screenshot 2022-05-19 at 23 43 31" src="https://user-images.githubusercontent.com/80678596/169410742-223cbc00-c015-4001-982f-56aa73754d44.png">

#### Local host server running

<img width="1307" alt="Screenshot 2022-05-19 at 23 44 42" src="https://user-images.githubusercontent.com/80678596/169410840-5818924e-3174-47d1-9ace-903ae0a411d4.png">

#### The containerized application running

<img width="1040" alt="Screenshot 2022-05-19 at 23 45 50" src="https://user-images.githubusercontent.com/80678596/169410923-b241c213-f02b-4123-b9bd-9566d9c8fb6d.png">

<img width="1118" alt="Screenshot 2022-05-19 at 23 47 21" src="https://user-images.githubusercontent.com/80678596/169411009-45d87914-c427-4bf0-ac5d-3c2f142d78ce.png">
