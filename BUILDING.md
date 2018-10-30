Requirements
------------
- [docker](https://www.docker.com/get-started)
- [docker compose](https://docs.docker.com/compose/install/)
--------------------------------------------------------------------------------

Install docker and docker-compose for your OS

There are two folders:
- docker_react_cli is for the react_cli container to create react app scalfolding.
- docker_react_dev is for development of the generated app in docker container. It consists of two containers dev and prod

All OS
--------
Build react-cli docker image

```
# Clone the repo
git clone https://github.com/irazaq/react-docker-tools.git
cd react-docker-tools/docker_react_cli

# Build the container
docker build . -t react-cli

# This will take a few minutes.
```

Linux/Mac
-----
You can create an alias to the docker tools
Add this to your bashrc 

```
alias react-docker='docker run -v ${PWD}:/app -u `id -u`:`id -g` react-cli'
alias npm='docker run -v ${PWD}:/app -u `id -u`:`id -g` react-cli npm'
alias yarn='docker run -v ${PWD}:/app -u `id -u`:`id -g` react-cli yarn'
```
logout and login again OR type `source .bashrc`

--------------------------------------------------------------------------------

##  react-cli usage to generate app scaffolding

Linux/Mac
---------
```
cd project_directory
docker run -v ${PWD}:/app -u `id -u`:`id -g` react-cli create-react-app myapp
```
or using alias

```
react-docker create-react-app myapp
```

--------------------------------------------------------------------------------

Windows 
--------
```
docker run -v %cd%:/app react-cli create-react-app myapp
```
