## About react-docker-tools
react-docker-tools is a set of react development tools using docker containers.

Development of react projects on local system without worrying about dependencies and breaking the development system. Docker makes it possible without any need to install node, npm, creat-react-app, create-react-native-app, react-native-cli on localhost.

## Setup instruction
To get started:
- [Build instruction](https://github.com/irazaq/react-docker-tools/blob/master/BUILDING.md)

## USAGE
After installing docker, docker-compose and building the docker containers, you can generate react app scalfolding and or develop on local machine. Production build can also be done and test in nginx based container.

## react-cli usage to generate app scaffolding
react-cli is based on the comments on 
https://github.com/facebook/create-react-app/issues/3002 by przbadu and others

## On linux / Mac
Enter the project folder where you want the app to be created using create-react-app
```
cd project_directory
docker run -v ${PWD}:/app react-cli create-react-app myapp
```
Instead of using the long version of the command, you can create a shortcut or alias to the docker tools. To do this, add
these to your .bashrc file
```
alias react-docker='docker run -v ${PWD}:/app react-cli'
alias npm='docker run -v ${PWD}:/app react-cli npm'
alias yarn='docker run -v ${PWD}:/app react-cli yarn'
```
logout and login again OR type `source .bashrc` to load the file and update your shell environment.

using the alias
```
react-docker create-react-app myapp
```

## On windows 
```
docker run -v %cd%:/app react-cli create-react-app myapp
```

## development of your app on localhost using docker_react_dev folder
after creating your app and you want to start development, copy development files from the cloned react-docker-tools folder in the build instruction to the app folder.
Copy the .docker folder, docker-compose.yml, .dockerignore from docker_react_dev folder to the app folder.
.docker/ is used to hide away the docker files out of the root of the app project. The only visible file in the root of the app project is the docker-compose.yml file.

```
cp -R path-to-downloaded-react-docker-tools-folder/docker_react_dev/.docker myapp/

# copy docker-compose.yml and .dockerignore too
cp docker-compose.yml .dockerignore myapp/

```

## Build the docker image and start development
```
docker-compose --build dev
```

## start you development server
```
docker-compose up -d dev
```
you can access the app at http://localhost:3000
Any modification to any files will be hot reloaded and available in the container and displayed in the browser.

## build and start your production server
to build for production and see how it looks like served by a nginx webserver
```
docker-compose up --build prod
```
Can also start the production container using
```
docker-compose up -d prod
```
The only difference between this and the previous command for production is that what you see will the last modifications before the container was build. Any modification after will not be shown.
you can access the production app at http://localhost:8000

OR you can build both containers with

```
docker-compose --build .
```
The build will take a few minutes.

## License
react-docker-tools is released under MIT License:

Copyright (c) 2018 Razaq Ijaduola

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.