---
title: How to Build Consistent Development Environment through Docker
date: 2019-03-20T02:02:28.828Z
tags: 
    - Docker
    - Tutorial
    - Jupyter Notebok
categories:
  - Data
  - Dev Env
image: https://i.loli.net/2019/04/27/5cc38cc0066e1.jpg
description: Data Analysis is not all about reports or visualization. The correctness and reproducibility are also important for scientific research. A consistent environment is critical for reproducibility. There are several ways to achieve that. However, I find out using Docker at any time can repeat the experiment in the same environment. It is easy to scale up and scale horizontally. 
---


Data Analysis is not all about reports or visualization. The correctness and reproducibility are also important for scientific research. A consistent environment is critical for reproducibility. There are several ways to achieve that. However, I find out using Docker at any time can repeat the experiment in the same environment. It is easy to scale up and scale horizontally. For more information, you can click [here](https://www.docker.com/why-docker).


<!-- more -->


## Docker File
A Dockerfile basically "tells" docker the way an image build. You can edit it to fit your daily usages.

> Please go to my [GitHub Repository](https://github.com/iamjohnnyli/data-analyst-notebook-docker) to check and download latest file.


## Build YOUR OWN DOCKER IMAGE


### INSTALL DOCKER
The Docker community have an explicit tutorial about how to install Docker. Please check [here](https://www.docker.com/community-edition#/download)


### BUILD ONE BASED ON DOCKERFILE

In the terminal, direct to the folder that contains the dockerfile and run the following command:
```sh
docker build -t data-analyst-notebook .
```
Don't forget the "." at the end. data-analyst-notebook is the name of the image. You can change to whatever you prefer.

## START SERVER
I use following code to start server:
```sh
docker run --rm -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v ~/:/home/jovyan/work data-analyst-notebook
```
There is more detailed instruction from [User Guide on ReadTheDocs](https://jupyter-docker-stacks.readthedocs.io/en/latest/)

If you feel like that the command is too long to run. You can add an alias to your .bashrc file like this:
```sh
alias dslab='docker run -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v ~/:/home/jovyan/work data-analyst-notebook'
```
Now you can use ```dslab``` in the terminal as a replacement for typing the long command.
