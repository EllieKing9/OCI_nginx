# nginx

https://nginx.org/en/linux_packages.html#Ubuntu

- $sudo apt update
- $sudo apt install nginx
- $nginx -v
- $sudo nginx
- $curl localhost:80 or $curl localhost:8080
- $sudo nginx -s quit / $nginx -s reload / $nginx -s reopen / $nginx -s stop

https://nginx.org/en/docs/beginners_guide.html
```
nginx consists of modules which are controlled by directives specified in the configuration file(nginx.conf)
Directives are divided into simple directives and block directives
block directive can have other directives inside braces, it is called a context (examples: events, http, server, and location).

simple directives / block directives / context
```

web server
```

```

Oracle Cloud (https://www.oracle.com/kr/cloud/)
```
Inboud 규칙 추가: 0.0.0.0/0 TCP 8080

//Ubuntu on Oracle Cloud
$sudo iptables -I INPUT 1 -p tcp --dport 8080 -j ACCEPT
```
