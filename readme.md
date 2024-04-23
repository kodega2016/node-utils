We can use docker container to intialize a new project(utlity container) and then use it to create a new project. This is a good way to keep the project clean and avoid installing unnecessary packages on the host machine.

## Steps:

1. Create a new container
2. Install the required packages
3. Create a new project

## Create a new container

```bash
docker image build -t node_utils .
docker container run -it --rm $(pwd):/app utility-container npm init
```

It will ask for the project name, version, description, entry point, test command, git repository, keywords, author, license. You can skip any of these by pressing enter.
And it will create a package.json file.

We can use `ENTRYPOINT` in the Dockerfile to append the command , so that we don't have to type it everytime.

```bash
docker container run -it --rm utility-container -v $(pwd):/app init
docker container run -it --rm utility-container $(pwd):/app install express
```
