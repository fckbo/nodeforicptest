# Node.js Hello World Sample App to test Helm Charts and deployment on icp

This application demonstrates a simple, reusable Node.js web application based on the Express framework.

## Run the app locally

1. [Install Node.js][]
+ cd into this project's root directory
+ Run `npm install` to install the app's dependencies
+ Run `npm start` to start the app
+ Access the running app in a browser at <http://localhost:6002>

[Install Node.js]: https://nodejs.org/en/download/

## Run the app locally using docker

1. [Install docker][]
+ cd into this project's root directory
+ Run `docker build -t <imagename> .` to create a docker image 
+ Run `docker run -p 7000:6002 -d <imagename>` to start the app

+ alternatively you can directly run 'docker run -p 7000:6002 -d frck/nodeforicptest'

+ Access the running app in a browser at <http://localhost:7000>

[Install docker]: https://docs.docker.com/engine/installation/
