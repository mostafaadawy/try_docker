# Docker Tutorial Windows 
- for running docker desktop we need to [install](https://learn.microsoft.com/en-us/windows/wsl/install) wsl from microsoft to allow virtual environments
- [install](https://www.docker.com/) docker desktop contains all its dependencies 
- we should have account on docker just like github
- we use docker hub that contains our published repos
- [docker hub](https://www.docker.com/products/docker-hub/) is the world’s leading service for finding and sharing container images with your team and the Docker community 
- for testing we created new project folder and create main.py python file
- `docker images` shows current installed images 
- `docker ps` displays  running containers 
# Create Docker image from this docker project
- `docker build -t hello-docker` build docker image from docker file `-t` stands for `tag` that give the image tag name so it followed by the image name `hello-docker` and then `.` refers to this folder
- at that moment we get that error `failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount228675408/Dockerfile: no such file or directory` that is because we didnot create the docker file yet.
- the steps begins by creating `docker file` which is `blueprint for building docker image` then creating `docker image` which is `a template based that docker file read only for running the container` then the `docker container` which is an `application running process`.
- so to solve this issue we create `DockerFile`
- it doesn't matter to name it dockerfile or even Dockerfile
- write inside the dockerfile `FROM python:3` that means the from docker images use the images for language python and we note that after we write it we will find that it will be clickable and if we click ctrl anf click on python it will redirect to all images on docker site that we can use
- check the code
```sh
FROM python:3
RUN mkdir /usr/src/app/
WORKDIR /usr/src/app/
COPY . /usr/src/app/
CMD ["python", "main.py"]
```
# Explanation of the file
- first from defines the image where we use image with python installed
- `RUN` after it we write terminal command 
- `WORKDIR` defines the application path we can think it where we will find the application in linux os that will be created
- `COPY` will copy the code inside our project folder `.` to the path of the application wich will be the created folder in the previous line of the docerfile code
- `CMD []` will make this file executable
- Note that the left hand side command in capital and vscode will allow autocomplete and some of this command clickable to help complete it
- test by check the docker images `docker images`
# run
- as our docker image is called `hello-docker`
- we can run the dockerimage  by `docker run hello-docker`
- then we get hello-docker from our container
- the container here is our application 
- we can run our container also from the docker desktop
- `docker ps -a`  well show all containers running and not running
- from  docker images we can see that every image has name and id if we want to deal with any image we can deal with its name or id
- delete the image using `docker image rm a0264f5a256e`
- because the image is running so it must be forced to delete `docker image rm a0264f5a256e -f`
# Using more than one image just that one for db and other for the backed needs docker compose this will be completed in the [second project](https://github.com/mostafaadawy/composejangodock)