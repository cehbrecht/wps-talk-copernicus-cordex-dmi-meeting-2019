# WPS deployment for Copernicus Climate Data Store

Copernicus CORDEX General Assembly at DMI, Copenhagen, 24-25 September 2019

## Intro

Create a new WPS project starting with a template and deploy it on a host and with Docker container.

## Motivation

### Why?

* https://birdhouse-workshop.readthedocs.io/en/latest/appendix.html#why-using-wps
* https://birdhouse.readthedocs.io/en/latest/overview.html#wps-use-case

### How?

* https://www.wikiwand.com/en/Function_as_a_service
* https://www.opengeospatial.org/standards

### Open Source Components

Server:
* https://www.osgeo.org/projects/pywps/

Client:
* https://www.osgeo.org/projects/owslib/

### Birdhouse

https://birdhouse.readthedocs.io/en/latest/publications.html

### WPS and C3S

* https://presentations.copernicus.org/EGU2018-6491_presentation.pdf
* https://cp4cds.github.io/overview/

## Outline

### Create your WPS from a Template

Use the [cookiecutter](https://cookiecutter-birdhouse.readthedocs.io/en/latest/) template and create a new WPS project.

Follow the instructions:
https://cookiecutter-birdhouse.readthedocs.io/en/latest/#installation


### Start the new WPS for development

Install the WPS:
https://babybird.readthedocs.io/en/latest/installation.html#install-from-github

Check the tests:
https://babybird.readthedocs.io/en/latest/dev_guide.html#running-tests

Start the WPS:
https://babybird.readthedocs.io/en/latest/installation.html#start-babybird-pywps-service

### Execute processes of your WPS

Use the WPS with URL requests:
https://emu.readthedocs.io/en/latest/tutorial/using_docker.html

Use the WPS via Birdy command line:
https://birdy.readthedocs.io/en/latest/api.html#module-birdy.cli

Use the WPS via Birdy in Jupyter Notebook:
https://birdy.readthedocs.io/en/latest/notebooks/examples/emu-example.html

### Modify your WPS

https://birdhouse-workshop.readthedocs.io/en/latest/pywps/process.html#what-is-a-wps-process

### Build and run your WPS as docker container

https://emu.readthedocs.io/en/latest/tutorial/using_docker.html

Run your clients again.

### Deploy your WPS with Ansible

https://ansible-wps-playbook.readthedocs.io/en/latest/deploy.html

Run your clients again.
