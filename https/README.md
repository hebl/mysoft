## Https Cert

[certbot](https://certbot.eff.org/#centosrhel7-nginx)

1. 使用EPEL安装 `certbot`

```
yum install certbot
```

2. 生成证书

```
certbot certonly --standalone -d example.com -d www.example.com
```

3. 定期更新

```
certbot renew --dry-run 

certbot renew --quiet 
```

4. nginx

```
ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
```