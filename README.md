# DevOps course at Innopolis University

> Semester 7, 4th study year

## Contents

- [Overview](#overview)
- [Build](#build)
- [Docker](#docker)
- [Usage](#usage)
- [Contact](#contact)

## Overview

This is a simple web application that shows the Moscow time
each time when you refresh a page.
The application was developed in two programming languages:

- Python with the use of [FastAPI](https://fastapi.tiangolo.com) framework.
  Can be found in [app_python](/app_python/) folder.
- Kotlin with the use of [Spring](https://spring.io) framework.
  Can be found in [app_kotlin](/app_kotlin/) folder.

## Build

### Download

- Open your terminal
- `git clone https://github.com/SMore-Napi/DevOps_Innopolis.git`
- `cd DevOps_Innopolis`
- `git checkout lab1`

### Python build

#### Installation

- All required dependencies are stored in the `requirements.txt` file.
- Open your terminal.
- Go to the **app_python** folder: `cd app_python`
- `pip install -r requirements.txt`

#### Running

- Open your terminal
- Go to the **app_python** folder: `cd app_python`
- Run application: `uvicorn main:app --reload`

### Kotlin build

- Install [JDK](https://www.oracle.com/java/technologies/downloads/)
- Install [Gradle](https://gradle.org/install/)
- Open your terminal
- Go to the **app_kotlin** folder: `cd app_kotlin`
- Run application: `./gradlew bootRun`

## Docker

- You can skip the [Build](#build) part and avoid installing packages.
  Instead, run the docker image. Preliminarily, you should build or pull this image.

### Python image

#### Build Python image

- Open your terminal. Your directory should be the root: `pwd`: **/DevOps_Innopolis**
- Build image: `docker build -t app_python_image app_python`
   - `app_python_image` - image name. You can change it whatever you want.
   - `app_python` - the folder in which the `Dockerfile` is placed.
  > In case you are already in the **/app_python** folder, you can use
  this command `docker build -t app_python_image .`

#### Pull Python image

- In case you don't want to build an image, you can pull the already
  pushed image in the docker
  hub: [app_python](https://hub.docker.com/repository/docker/smorenapi/app_python)
- Run `docker pull smorenapi/app_python:latest`

##### Small instruction on how to push an image

- Assign image name: `docker image tag app_python_image:latest <login>/app_python:latest`
- Push: `docker image push <login>/app_python:latest`

> Use your docker hub login instead of `<login>`

#### Run Python image

- You need a built or pulled image.
- Run image: `docker run --rm -p 8000:8000 --name app_python <app_python_image>`
   - `--rm` automatically remove the container when it exits.
  You can omit this parameter.
   - `-p` expose port 8000.
   - `--name app_python` - container name. You can specify any name you'd like.
   - `<app_python_image>` - image name.
      - Use `app_python_image` if you built your own image.
      - Use `smorenapi/app_python:latest` if you pulled the image from my repository
      - You can also include `-d` to run a container in the background
       (detached mode).

### Kotlin image

#### Build Kotlin image

- Open your terminal. Your directory should be the root: `pwd`: **/DevOps_Innopolis**
- Build image: `docker build -t app_kotlin_image app_kotlin`
   - `app_kotlin_image` - image name. You can change it whatever you want.
   - `app_kotlin` - the folder in which the `Dockerfile` is placed.
     > In case you are already in the **/app_kotlin** folder, you can use this
  command `docker build -t app_kotlin_image .`

#### Pull Kotlin image

- In case you don't want to build an image, you can pull the already
  pushed image in the docker
  hub: [app_kotlin](https://hub.docker.com/repository/docker/smorenapi/app_kotlin)
- Run `docker pull smorenapi/app_kotlin:latest`

#### Run Kotlin image

- You need a built or pulled image.
- Run image: `docker run --rm -p 8080:8080 --name app_kotlin <app_kotlin_image>`
   - `--rm` automatically remove the container when it exits.
  You can omit this parameter.
   - `-p` expose port 8080.
   - `--name app_kotlin` - container name. You can specify any name you'd like.
   - `<app_kotlin_image>` - image name.
      - Use `app_kotlin_image` if you built your own image.
      - Use `smorenapi/app_kotlin:latest` if you pulled the image from my repository
      - You can also include `-d` to run a container in the
       background (detached mode).

## Usage

### Python usage

- Run the application and open this URL in your browser: [http://127.0.0.1:8000](http://127.0.0.1:8000)
- Each time when you refresh a page you will see the actual Moscow time

![Web App](https://user-images.githubusercontent.com/49106163/188318587-e71e43a8-8bdf-46f3-a29f-f2377f4b5e86.png)

### Kotlin usage

- Run the application and open this URL in your browser: [http://127.0.0.1:8080](http://127.0.0.1:8080)
- Each time when you refresh a page you will see the actual Moscow time

![Web App](https://user-images.githubusercontent.com/49106163/188326480-63eefcee-88fc-4692-a234-85f34d5afd65.png)

## Contact

- **Student:** Roman Soldatov
- **Group:** B19-SD-01
- **Email:** r.soldatov@innopolis.university
