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
Certbot은 우분투 20.04를 설치 후 letsencrypt을 설치했다면 그 안에 포함
- https://eff-certbot.readthedocs.io/en/stable/using.html
```
//$sudo apt-get install letsencrypt
$sudo apt-get install certbot
$sudo apt-get install python3-certbot-nginx
```
- nginx 자동 연계 세팅
- https://hoing.io/archives/4491#Lets_Encrypt
- https://blog.projectdh.link/99
- !! https://bbul-jit.tistory.com/77
```
//$sudo certbot --nginx -d zhem66.ml --email 7baetae@hanmail.net --agree-tos
$sudo certbot --nginx -d zhem66.ml -m 7baetae@hanmail.net --agree-tos --no-eff-email
//-d --domain, -m --email, --agree-tos 항목체크, --no-eff-email lets encrypt 메일 받지않음 

Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing, once your first certificate is successfully issued, to
share your email address with the Electronic Frontier Foundation, a founding
partner of the Let's Encrypt project and the non-profit organization that
develops Certbot? We'd like to send you email about our work encrypting the web,
EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: n
Account registered.
Requesting a certificate for zhem66.ml

Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/domain/..
Key is saved at:         /etc/letsencrypt/live/domain/..
This certificate expires on 2023-02-05.
These files will be updated when the certificate renews.
Certbot has set up a scheduled task to automatically renew this certificate in the background.

Deploying certificate
Successfully deployed certificate for zhem66.ml to /etc/nginx/sites-enabled/default
Congratulations! You have successfully enabled HTTPS on https://zhem66.ml

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
If you like Certbot, please consider supporting our work by:
 * Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
 * Donating to EFF:                    https://eff.org/donate-le
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

```
- nginx 수동 세팅 및 정리(webroot/standalone/DNS/manual)
- https://blog.hyunsub.kim/Server/HTTPS/
- https://happist.com/573990/%EC%B5%9C%EC%8B%A0-lets-encrypt-ssl-%EC%9D%B8%EC%A6%9D%EC%84%9C-%EB%B0%9C%EA%B8%89-%EB%B0%A9%EB%B2%95-3%EA%B0%80%EC%A7%80-%EC%A0%95%EB%A6%AC
```

```

reverse proxy server
```

```

web server
```

```

