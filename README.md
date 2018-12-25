# dopkg

> Build and run node apps in small container using docker and [zeit/pkg](https://github.com/zeit/pkg)

> dopkg is heavy inspired by [dockerpkg](https://github.com/dockerpkg/dockerpkg)


# Introduction

[zeit/pkg](https://github.com/zeit/pkg) is a tool to package a NodeJS project into an executable. The resulting
packages can be used on a system without having to install NodeJS, npm or the project dependencies. 

When used together with a small system like Alpine Linux this can result in simple and minimal Docker images.

This project aims for a very simple workflow to create these small images. It does so by separating the process of
building and running the container and it provides a simple helper command to run the build. 

# Components

## dopkg/builder

The builder image is based on `node:lts-alpine` and it runs the `pkg` command with some params in the mounted directory.

The result is a generated binary called `app.bin` in the mounted directory (generally this is the dir of you project).

## dopkg/runner

The runner images is based on `alpine:latest` and it is made to run the generated `app.bin` from the `/app` directory.

## dopkg cli tool

The `dopkg` is a simple script that executes the `docker` command with the right parameters to created a build.
 
It pulls the `dopkg/runner` images and makes sure that the working dir is mounted correctly.

# How to use 

Please refer to [dopkg-example-app](https://github.com/dopkg/dopkg-example-app) for a working example.

# Credits

- [ZEIT](https://zeit.co) for creating awesome software like [zeit/pkg](https://github.com/zeit/pkg)

# LICENSE

MIT
