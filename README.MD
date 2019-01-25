
# Genearate SSL selfsigned sertificate

```
openssl req -x509 \
 -nodes -days 3650 -newkey rsa:4096 \
 -keyout example.com.pem \
 -out example.com.x509.crt \
 -subj "/C=US/ST=WA/L=Seattle/CN=example.com/emailAddress=some@mail.com"
```