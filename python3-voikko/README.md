README
======

A demo CLI App built on top of the [official Debian images](https://hub.docker.com/_/debian/) `debian:stretch` and `debian:sid`. Debian Sid as the development distribution of Debian supports the latest versions of Voikko packages, whereas Debian Stretch as the stable distribution of Debian supports the older versions of Voikko packages. Analysis of Finnish words passed as arguments, using Voikko's analyze-function. Original accompanying [blog post](https://janikarhunen.fi/a-journey-to-dockerize-voikko-and-python-app.html#a-journey-to-dockerize-voikko-and-python-app) by [Jani Karhunen](https://github.com/janikarh).

Working Voikko installation containing:

* debian:stretch
    * [`voikko-fi 2.1-1`](https://packages.debian.org/stretch/text/voikko-fi)
    * [`python-libvoikko 4.1-1`](https://packages.debian.org/stretch/python-libvoikko)
* debian:sid
    * [`voikko-fi 2.2-1.1`](https://packages.debian.org/sid/text/voikko-fi)
    * [`python-libvoikko 4.1.1-1.1`](https://packages.debian.org/sid/python-libvoikko)

[Official Voikko changelog](https://voikko.puimula.org/releases.html)

## Building Docker images

    docker build -f Dockerfile-debian-stretch -t tuomastik/python3-voikko-stretch:1.0 -t tuomastik/python3-voikko-stretch:latest .
    docker build -f Dockerfile-debian-sid -t tuomastik/python3-voikko-sid:1.0 -t tuomastik/python3-voikko-sid:latest .
    
## Usage

Pull the image, and run the container with:

    docker run --rm -ti tuomastik/python3-voikko-stretch:[Tag] [word_to_analyze]
    docker run --rm -ti tuomastik/python3-voikko-sid:[Tag] [word_to_analyze]

Example with the image version 1.0, and 2 words to analyze:

    docker run --rm -ti tuomastik/python3-voikko-stretch:1.0 "rei'ittämättä" kansiossa
    docker run --rm -ti tuomastik/python3-voikko-sid:1.0 "rei'ittämättä" kansiossa

## Publish the images on Docker Hub

    docker login

    docker push tuomastik/python3-voikko-stretch:latest
    docker push tuomastik/python3-voikko-stretch:1.0

    docker push tuomastik/python3-voikko-sid:latest
    docker push tuomastik/python3-voikko-sid:1.0
 