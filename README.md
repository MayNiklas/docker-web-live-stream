# web-live-stream

### Wireguard:
- by only accepting traffic on port 1935 via the wireguard interface, the stream is encrypted as well it's protected

### NGINX reverse proxy:
- use the example config
- authentification is enabled by default! Make sure /config/nginx/.htpasswd is created 

### OBS stream settings
- Service: Custom
- Server: rtmp://IP-Adress/live
- Stream key: watching-shows-together (change it within index.html)
