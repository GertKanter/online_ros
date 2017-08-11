By Working Example
==================

This is a web system where the user can compile, edit and run working Robot Operating System (ROS) example code.

This code is currently in a pre alpha, proof of concept state. Do not use in a production environment.

The tutorials are located in a separate repository described below.

### Install (alpha)

You'll need git.
```
sudo apt-get install git
```
You'll want to clone the code which runs the site and the example code into separate directories.
```
git clone https://github.com/davidmball/by_working_example.git
git clone https://github.com/davidmball/ros_examples.git
```
Docker is required to run the example code. For the Google compute engine I use docker.io.
```
sudo apt-get install docker.io
```

And get the docker container.
```
docker pull davidmball/ros_online:kinetic
```

Also, you will need npm/nodejs. Note that for the Google compute engine I had to use these commands to install it.
```
NODE_VERSION="v4.2.6"
curl -LO http://nodejs.org/dist/$NODE_VERSION/node-$NODE_VERSION-linux-x64.tar.gz
tar xzf node-$NODE_VERSION-linux-x64.tar.gz
sudo cp -rp node-$NODE_VERSION-linux-x64 /usr/local/
sudo ln -s /usr/local/node-$NODE_VERSION-linux-x64 /usr/local/node
nodejs --version
```

Then install the package dependencies.

### Running

Set the correct configuration to either production or development. You should edit the development config file to suit your system.
```
export NODE_ENV=production
```

Then run locally with:
```
nodemon server.js
```
Or on a production system at the moment to get access to port 80.
```
sudo -E bash -c '/usr/local/node/bin/node server.js'
```

The docker container is built automatically when there is a change to the dockerfile on master in github.

### Contributing to the web site

Pull requests are welcome. For consistent style use

[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)

Run with
```
standard --fix
```

### Other

If you want to test building the docker image locally then change to the dockerfile/kinetic directory and type
```
docker build -t ros-online-kinetic .
```

### License

The code is released under the BSD license.
Except where otherwise noted, the web pages and documentation are licensed under Creative Commons Attribution 3.0.
