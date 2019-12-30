# Node.js End-point in a Container

Open a web browser to https://console.aws.amazon.com

From the services select Cloud9 and open the environment we used before for terraform setup

Open a terminal and clone the repo with end-point source code:
```
git clone https://github.com/vkhazin/courseware-nodejs-container.git
```

To build a docker image execute: `docker build ./ -t node/end-point`

Expected result:
```
...
Successfully tagged node/end-point:latest
```

To run the newly create image we need to create a container from it

Images are immutable, containers can mutate over their lifecycle

To launch a new container execute: `docker run --name node-end-point -d --rm -p 3001:3001 node/end-point`

`--name` gives our container a name

`-p 3001:3001` maps host port 3001 to container port 3003

`-d` start detached to be able to use the terminal

`--rm` delete the container when is stopped

And now you are able to access the endpoint: `curl 'http://localhost:3001?name=John'`

This is how you create a nodejs end-point running in a container

To delete the container: `docker rm node-end-point -f`

To delete the image: `docker rmi node/end-point`