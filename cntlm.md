## Setup Proxy in WSL to enable connectivity

Install cntlm proxy on WSL

```bash
sudo apt-get install cntlm
```

Alternative

```bash
curl http://archive.ubuntu.com/ubuntu/pool/universe/c/cntlm/cntlm_0.92.3-1ubuntu1_amd64.deb -o cntlm_0.92.3-1ubuntu1_amd64.deb
sudo dpkg -i cntlm_0.92.3-1ubuntu1_amd64.deb
```


sudo systemctl restart cntlm



https://askubuntu.com/questions/1121521/how-to-configure-http-proxy-with-authentication-on-ubuntu-wsl-on-windows-10


cntlm -H  for generating new password
/etc/cntlm.conf

https://dev.to/ironfroggy/wsl-tips-starting-linux-background-services-on-windows-login-3o98

Edit /etc/environment

```bash
http_proxy=http://localhost:3128/
https_proxy=http://localhost:3128/
ftp_proxy=http://localhost:3128/
no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
HTTP_PROXY=http://localhost:3128/
HTTPS_PROXY=http://localhost:3128/
FTP_PROXY=http://localhost:3128/
NO_PROXY="localhost,127.0.0.1,localaddress,.localdomain.com"
```

Edit /etc/wgetrc

```bash
http_proxy=http://localhost:3128/
https_proxy=http://localhost:3128/
ftp_proxy=http://localhost:3128/
```

Edit or create /etc/apt/apt.conf.d/95proxy

```bash
Acquire::http::proxy "http://localhost:3128/";
Acquire::ftp::proxy "http://localhost:3128/";
Acquire::https::proxy "http://localhost:3128/";
```

Edit or create in your home ~/.curl.rc

```bash
proxy = localhost:3128
```

PIP

```bash
pip --proxy localhost:3128 install <module>
```

```git
git config --global http.proxy http://localhost:3128
```

/etc/maven/settings.xml

```xml
<proxy>
  <active>true</active>
  <protocol>http</protocol>
  <host>localhost</host>
  <port>3128</port>
</proxy>
```
