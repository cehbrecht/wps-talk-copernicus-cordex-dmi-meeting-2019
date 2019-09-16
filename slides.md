# WPS deployment
Copernicus CORDEX General Assembly at DMI, Copenhagen, 24-25 September 2019
---
## Intro
Create a new WPS project starting with a template and deploy it on a host and with Docker container.
---
## Motivation
---
### Using WPS
![WPS use case](media/wps_adamsteer.png)
---
### OGC Standard
![OGC wps](media/ogc-wps.png)
---
### PyWPS - Server
![OGC pywps](media/ogc-pywps.png)
---
### OWSLib - Client
![OGC owslib](media/ogc-owslib.png)
---
## WPS for Climate Data Store
---
### CP4CDS
![cp4cds](media/cp4cds.png)
---
### CP4CDS Interfaces
![cp4cds interfaces](media/cp4cds-interfaces.png)
---
### Uptime 99%
![ghc](media/ghc.png)
---
### Can't do it alone
![cp4cds federated](media/cp4cds-federated.jpg)
---
### Security
![security](media/cp4cds-access-control.jpg)
---
## Using WPS Template
---
### Create your WPS from a Template
Use the cookiecutter template and create a new WPS project.

https://cookiecutter-birdhouse.readthedocs.io/en/latest/
---
### Example
```
$ conda install -c conda-forge cookiecutter
$ cookiecutter https://github.com/bird-house/cookiecutter-birdhouse.git

full_name [Full Name]: Daphne du Maurier
github_username [bird-house]: bird-house
project_name [Babybird]: Babybird
project_slug [babybird]: babybird
project_short_description [Short description]: A Web Processing Service for Climate Data Analysis.
version [0.1.0]: 0.1.0
http_port [5000]: 5000
```
---
### Babybird
![babybird](media/babybird.png)

https://github.com/bird-house/babybird
---
## Start the new WPS for development
---
### Install the WPS
```
$ git clone https://github.com/bird-house/babybird.git
$ cd babybird
$ conda env create -f environment.yml
$ source activate babybird
$ pip install -e .[dev]
OR
$ make develop
```
https://babybird.readthedocs.io/en/latest/installation.html#install-from-github
---
### Run the tests
```
$ make test
$ make test-all
$ make lint
```
https://babybird.readthedocs.io/en/latest/dev_guide.html#running-tests---
---
### Start the Service
```
$ make start
$ make status
$ tail -f pywps.log
$ make stop
```
https://babybird.readthedocs.io/en/latest/installation.html#start-babybird-pywps-service
---
## Execute processes of your WPS
---
### Use the WPS with URL requests
* http://localhost:5000/wps?service=WPS&version=1.0.0&request=GetCapabilities
* http://localhost:5000/wps?service=WPS&version=1.0.0&request=DescribeProcess&identifier=hello
* http://localhost:5000/wps?service=WPS&version=1.0.0&request=execute&identifier=hello&DataInputs=name=Stranger
---
### Use the WPS via Birdy command line:
```
$ export WPS_SERVICE=http://localhost:5000/wps
$ birdy -h
$ birdy hello -h
$ birdy hello --name Stranger
'Hello Stranger'
```
https://birdy.readthedocs.io/en/latest/api.html#module-birdy.cli
---
### Use the WPS via Birdy in a Jupyter Notebook:
```
from birdy import WPSClient
client = WPSClient(url='http://localhost:5000/wps')
client.hello(name='Stranger')
```
https://birdy.readthedocs.io/en/latest/notebooks/examples/emu-example.html
---
## Modify your WPS
---
### Add a new Process
* Add a new PyWPS process class.
* Define the input and output parameters.
* Implement a *handler* method with the process code.
---
### Example
![pywps process example](media/pywps-process-example.png)

https://birdhouse-workshop.readthedocs.io/en/latest/pywps/process.html#create-your-first-process
---
## WPS Deployment
---
### CP4CDS Toolbox (SDDS)
![sdds](media/cp4cds-toolbox.jpg)
---
### Deploy as docker container
```
$ docker build -t bird-house/babybird .
$ docker run -p 5000:5000 bird-house/babybird
http://localhost:5000/wps?request=GetCapabilities&service=WPS
```
https://github.com/bird-house/babybird/blob/master/Dockerfile
---
### PyWPS with Nginx etc
![pywps with nginx](media/cp4cds-wps.jpg)
---
### Deploy with Ansible
```
$ git clone https://github.com/bird-house/ansible-wps-playbook.git
$ cd ansible-wps-playbook
$ vim custom.yml
$ ansible-playbook -c local playbook.yml
```
https://ansible-wps-playbook.readthedocs.io/en/latest/deploy.html
---
## Summary
* Use Cookiecutter template to create a new WPS project.
* New WPS is ready to use without additional installation steps.
* Dockerfile for deployment is prepared.
* Ansible can be used for production deployment with Nginx and Postgres.
---
## Thank You
* Website: http://bird-house.github.io/
* Development: https://github.com/bird-house
* CP4CDS: https://cp4cds.github.io/
* Presentation: https://github.com/cehbrecht/cp4cds-presentation-at-knmi-feb-2018/blob/master/cp4cds-for-magic.pdf
* Poster: https://github.com/cehbrecht/copernicus-poster-egu-2018/blob/master/copernicus-poster-egu-2018.pdf
