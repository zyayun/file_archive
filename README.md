# file_archive

> 存放归档文件

/sbin/tini

```
docker run \
  -u root \
  --name jenkins-test \
  -d \
  -p 8080:8080 \
  -p 50000:50000 \
  -v $PWD:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkinsci/blueocean
```

