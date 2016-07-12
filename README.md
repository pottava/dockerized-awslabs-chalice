[awslabs/chalice](https://github.com/awslabs/chalice)
---

### Supported tags and respective `Dockerfile` links:

・latest ([versions/beta/Dockerfile](https://github.com/pottava/dockerized-awslabs-chalice/blob/master/versions/beta/Dockerfile))  
・beta ([versions/beta/Dockerfile](https://github.com/pottava/dockerized-awslabs-chalice/blob/master/versions/beta/Dockerfile))  

([日本語はこちら](https://github.com/pottava/dockerized-awslabs-chalice/blob/master/README-ja.md))


# Installation

### Case 1: with environment variables

```
cat << EOF >> ~/.bashrc
function chalice () {
  docker run --rm -v \$(pwd):/app \\
      -e AWS_ACCESS_KEY_ID \\
      -e AWS_SECRET_ACCESS_KEY \\
      -e AWS_DEFAULT_REGION \\
      pottava/chalice \$@
}
EOF
source ~/.bashrc
```

### Case 2: with AWS credentials

```
cat << EOF >> ~/.bashrc
function chalice () {
  docker run --rm -v \$(pwd):/app \\
      -v $HOME/.aws/credentials:/root/.aws/credentials \\
      pottava/chalice \$@
}
EOF
source ~/.bashrc
```


# Usage

> Set environment variables if you needed.

```
$ export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
$ export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
$ export AWS_DEFAULT_REGION=us-east-1
```

### ・Show help

```
$ chalice --help
```

### ・Create a new project

```
$ chalice new-project <project-name>
```

### ・Deploy the project

```
$ cd <project-name>
$ chalice deploy
```

### ・Show application logs

```
$ cd <project-name>
$ chalice logs
```
