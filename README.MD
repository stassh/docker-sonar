
# Genearate SSL selfsigned sertificate

``` bash
openssl req -x509 \
 -nodes -days 3650 -newkey rsa:4096 \
 -keyout example.com.pem \
 -out example.com.x509.crt \
 -subj "/C=US/ST=WA/L=Seattle/CN=example.com/emailAddress=some@mail.com"
```

``` bash

openssl s_client -showcerts -connect sonarqube-at.remote.server.com:443

openssl s_client -connect sonarqube-at.remote.server:443 | openssl x509 -out sonar_ssl.cert

sudo keytool -import -alias sonar_certificate -file sonar_ssl.cert -keystore  /Library/Java/JavaVirtualMachines/jdk1.8.0_171.jdk/Contents/Home/jre/lib/security/cacerts
```

password: changeit

list content of folder on runned container

``` bash
docker exec -it nginx-alpine ls /etc/nginx/conf.d

```

remove deafult configuration file

```sh
docker exec -it nginx-alpine rm /etc/nginx/nginx.conf.default
```
