# Maven, aws-cli, docker in docker

Containerized maven, aws-cli, docker on alpine to avoid requiring them to be installed on CI machines.

## Build

```
docker build -t yaoliinyk/mvn-aws-cli .
```

Automated build on Docker Hub

[![DockerHub Badge](http://dockeri.co/image/yaoliinyk/mvn-aws-cli)](https://hub.docker.com/r/yaoliinyk/mvn-aws-cli/)

## Usage

If you need to run docker commands inside container pass -v option to docker run command:

```
docker run -v "/var/run/docker.sock:/var/run/docker.sock:rw" --rm -it --entrypoint /bin/sh yaoliinyk/mvn-aws-cli

```


In order to configure aws cli pass credentials during run command:

```
docker run -v "/var/run/docker.sock:/var/run/docker.sock:rw" -e "AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}" -e "AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}" -e "AWS_DEFAULT_REGION=${AWS_DEFAULT_REGION}" --rm -it --entrypoint /bin/sh yaoliinyk/mvn-aws-cli

```

## Jenkinsfile

Jenkinsfile example:


```
 agent {
        docker {
            image "yaoliinyk/mvn-aws-cli"
            args "-v $HOME/.m2:/root/.m2 -v /var/run/docker.sock:/var/run/docker.sock:rw -e \"AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID}\" -e \"AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}\" -e \"AWS_DEFAULT_REGION=${AWS_DEFAULT_REGION}\" "
        }
    }

```
