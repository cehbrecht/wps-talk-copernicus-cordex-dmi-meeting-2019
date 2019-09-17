# What is a WPS and why we chose it

WPS (Web Processing Service) is a standard developed by the Open Geospatial Consortium (OGC). It provides standard rules to invoke geospatial processing services as a web service. This means that it makes it both easy and flexible to share any geographical data, including climate data.

It can also describe any calculation on all of its inputs and outputs.

As an example, it’s possible to use a WPS to send data like average temperature, peak temperature, or any calculated data, for every model.

## What’s the goal behind that

The whole idea behind this specific part of the Copernicus project is to make climate data accessible to not only scientists and engineers, but also to a wide audience. This means that it’s possible to send self-explanatory values based on calculations on the raw data on top of the actual data, which is a big boon for accessibility.

# Creating your own WPS

To the ends of the Copernicus project, we use a PyWPS implementation for the web service. It’s an implementation of the WPS standard written in Python. It enables the use of python programs via the WPS.

To create your own WPS, a set of programs called `birdhouse` was developed. Here are a few of the tools developed :

* Emu is just a demo WPS
* Black Swan provides services to analyze extreme weather
* Finch calculates climate indices

These are all to be deployed on a WPS server, of course.

A template called « cookiecutter » was created. As the name suggests, it’s a cookie-cutter template that allows you to build your own WPS. This lets you create an implementation of PyWPS.

Here is how you do it :

```bash
conda install -c conda-forge cookiecutter
cookiecutter https://github.com/bird-house/cookiecutter-birdhouse.git
```

You will then be prompted a list of questions to build your project :
```bash
full_name [Full Name]: Enter your full name.
email [Email Address]: Enter your email address.
github_username [bird-house]: Accept the default or enter your github username.
project_name [Babybird]: The name of your new bird.
project_slug [babybird]: The name of your bird used as Python package.
project_short_description [Short description]: Enter a short description about your project.
version [0.1.0]: Enter the version number for your application.
http_port [5000]: The HTTP port on which your service will be accessible.
https_port [25000]: The HTTPS port on which your service will be accessible.
output_port [8090]: The HTTP port on which your service outputs will be accessible.
```

This will create a bird (PyWPS server) in your current directory. This bird contains configurable processes, along with some initial test processes.

If you want to add it to birdhouse, you can then do the following :

* Create a repo and put it there.
* Add the repo to your Travis-CI account.
* Add the repo to your ReadTheDocs account + turn on the ReadTheDocs service hook.

# Roadmap and where we are in the project

The stack we use for Copernicus is fully useable and in use already in DKRZ + CEDA. I (Pierre) am working on implementing it in IPSL at the moment.

Two data sets are downloadable :

* A CORDEX data set
* A CMIP5 data set

There is a working user interface as well, accessible from a website.
