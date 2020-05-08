# codepeer_docker_demo

This demo uses docker-compose to build a Linux image with CodePeer installed,
create a container from that image to analyze a project, then serve the results
via the CodePeer Web Server and CodePeer IDE Server.

NGINX is used as a reverse proxy in front of the CodePeer servers.

## Getting Started

Make sure you have docker and docker-compose installed on your machine.

Before you can build the CodePeer image, you must download a recent copy of
CodePeer from your GNATtracker account and place it in the codepeer folder. Do
not untar the file, Docker will handle that for us.

Now you can run:
```
$ docker-compose up
```

This will build the images, and spin up the containers described in the
docker-compose.yaml file. Once the images are built, the containers are spun up
and CodePeer finishes analyzing the sdc tutorial project, you will be able to
access the results of the analysis by pointing your browser to `localhost` or
the IP address of the machine running the docker-compose.

BEWARE!!! By default, this will serve the results to 0.0.0.0 on your host
machine, which means that any machine on your network will be able to access
the results if they know your IP address.

Please take the necessary security precautions!!
For example: Either modifying the docker-compose.yaml file to only serve to the
host machine's localhost or ensure you are on a closed network. Contact your
local IT administrator for advice/permissions before attempting to deploy this
example.
