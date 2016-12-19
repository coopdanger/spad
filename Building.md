
The website and specification can be build using a Docker image. If you do not have Docker installed, it can be downloaded from [https://www.docker.com/].

# Building a docker image with the tools

Create a docker image with
```sh
docker build -t spad .
```

# Using docker to build the website

Build specification  with
```sh
docker run -v `pwd`:/work spad
```

another useful command to get a shell in the docker image is
```sh
docker run -it -v `pwd`:/work spad /usr/bin/tcsh
```
For repeated builds you will want to
```sh
make clean
```
before building the specification again.

Continuous integration with Travis is forthcoming.
