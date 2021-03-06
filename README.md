# Let's Encrypt HAProxy

A [Let's Encrypt](https://github.com/letsencrypt/letsencrypt) wrapper that generates an extra `haproxy.pem` file compatible with [HAProxy](https://serversforhackers.com/using-ssl-certificates-with-haproxy) crt configuration option.

## Usage

You can use it just like the official Docker image.

```
sudo docker run -it --rm -p 443:443 -p 80:80 --name letsencrypt \
  -v "/etc/letsencrypt:/etc/letsencrypt" \
  -v "/var/lib/letsencrypt:/var/lib/letsencrypt" \
  sheerun/letsencrypt:latest auth
```

## References

- http://letsencrypt.readthedocs.org/en/latest/using.html#running-with-docker
- https://blog.brixit.nl/automating-letsencrypt-and-haproxy
- http://blog.defsdoor.org/using-letsencrypt-ssl-certificates/
- https://github.com/Levino/letsencrypt-cert-service

## How it works

When wrapped `letsencrypt` command successfully exits, this script looks for all `fullchain.pem` in `/etc/letsencrypt/` and concatenates them with corresponding `privkey.pem` producing extra `fullchain.pem`.

## License

Dual-licensed MIT and Apache-2.0.
