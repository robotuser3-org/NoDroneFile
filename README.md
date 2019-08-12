whoami
======

Simple HTTP docker service that serves a a webapp for testing
## Purpose
This app can be used for testing deployments and container orchestrations like Kubernetes. Once deployed the app exposes information about it's environment. These information can then be accessed and validated by test automation scripts.

## How to run

    $ docker build . -t mywhoami

    $ docker run -d -p 80:80 --name mywhoami mywhoami

  The app will expose on port 80 a website showing:

```
Hostname: 8b5485ce34ff
IP: 127.0.0.1
IP: 172.17.0.2
ENV: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV: HOSTNAME=8b5485ce34ff
ENV: PORT=80
ENV: HOME=/root
GET / HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.87 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9,de;q=0.8
Cache-Control: no-cache
Connection: keep-alive
Pragma: no-cache
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
Upgrade-Insecure-Requests: 1
```

On the route /api the app will expose the same information as a json body.

```
{"hostname":"8b5485ce34ff","ip":["127.0.0.1","172.17.0.2"],"header":{"Accept":["text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3"],"Accept-Encoding":["gzip, deflate, br"],"Accept-Language":["en-US,en;q=0.9,de;q=0.8"],"Connection":["keep-alive"],"Sec-Fetch-Mode":["navigate"],"Sec-Fetch-Site":["none"],"Sec-Fetch-User":["?1"],"Upgrade-Insecure-Requests":["1"],"User-Agent":["Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.87 Safari/537.36"]},"env":["PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin","HOSTNAME=8b5485ce34ff","PORT=80","HOME=/root"]}
```
