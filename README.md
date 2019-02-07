# kubernetes-traefik

- Create TLS certificate:

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ./tls.key -out ./tls.crt -subj "/CN=*.example.com"
```

This examples uses 2 different certificates to terminate SSL for 2 hostnames.

Deploy the controller by creating the rc in the parent dir
Create tls secret for foo.bar.com
Create rc-ssl.yaml
Next create a SSL certificate for foo.bar.com host:

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /tmp/tls.key -out /tmp/tls.crt -subj "/CN=foo.bar.com"
Now store the SSL certificate in a secret:

kubectl create secret tls foo-secret --key /tmp/tls.key --cert /tmp/tls.crt

- Create a TLS secret:

```
kubectl create secret tls traefik-ui-tls-cert - - key ./tls.key  --cert ./tls.crt
```

- Apply deployment file:

```
kubectl apply -f deployment.yaml
```
