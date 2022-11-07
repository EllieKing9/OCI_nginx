# nginx

설치: https://nginx.org/en/linux_packages.html#Ubuntu

- $sudo apt update
- $sudo apt install nginx
- $nginx -v
- default port 세팅
```
$cd /etc/nginx/sites-enabled
$sudo nano default
```
- $sudo nginx
- $curl localhost:80 or $curl localhost:8080
- $sudo nginx -s quit / $nginx -s reload / $nginx -s reopen / $nginx -s stop

Oracle Cloud (https://www.oracle.com/kr/cloud/)
```
//Dashboard > Default Security list for VCN on Oracle Cloud 
Inboud 규칙 추가: 0.0.0.0/0 TCP 8080
Inboud 규칙 추가: 0.0.0.0/0 TCP 80
Inboud 규칙 추가: 0.0.0.0/0 TCP 443

//Ubuntu on Oracle Cloud
$sudo iptables -nL
$sudo iptables -I INPUT 6 -p tcp --dport 8080 -j ACCEPT
$sudo iptables -I INPUT 6 -p tcp --dport 80 -j ACCEPT
$sudo iptables -I INPUT 6 -p tcp --dport 443 -j ACCEPT
$sudo iptables -nL
//$sudo iptables -A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
$sudo cp /etc/iptables/rules.v4 /etc/iptables/rules.v4.ori
$sudo su
$iptables-save > /etc/iptables/rules.v4
or
//$service iptables save
or
//sudo netfilter-persistent save
//sudo netfilter-persistent reload
$reboot
```
iptables
- 설정: https://meongj-devlog.tistory.com/127 | https://goni9071.tistory.com/46 | https://jdh5202.tistory.com/492
- 저장(ubuntu): https://blog.elmi.page/406 | https://ndb796.tistory.com/262

구성: https://nginx.org/en/docs/beginners_guide.html
```
nginx consists of modules which are controlled by directives specified in the configuration file(nginx.conf)
Directives are divided into simple directives and block directives
block directive can have other directives inside braces, it is called a context (examples: events, http, server, and location).

simple directives / block directives / context
```
HTTPS 세팅
1. (무료)도메인 취득 //하루(24시간) 정도 후에 사용 가능..
- https://www.freenom.com/en/index.html?lang=en
zhem66.ml
- 하루 지나도 사용이 안되면 sign in > Services > Manage Domain > Manage Freenom DNS > Target에 IP 세팅
2. SSL 인증서 발급 (Let`s Encrypt with Certbot)
- https://blog.hyunsub.kim/Server/HTTPS/
```

```
web server
```

```
reverse proxy server
```

```
