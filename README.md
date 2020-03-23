# Maven, aws-cli, docker in docker

Containerized maven, aws-cli, docker on alpine to avoid requiring them to be installed on CI machines.

## Build

```
docker build -t yaoliinyk/mvn-aws-cli .
```

Automated build on Docker Hub

[![DockerHub Badge](http://dockeri.co/image/yaoliinyk/mvn-aws-cli)](https://hub.docker.com/r/yaoliinyk/mvn-aws-cli/)
