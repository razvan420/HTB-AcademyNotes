# FTP

**Download All Available Files**

{% code fullWidth="true" %}
```bash
 wget -m --no-passive ftp://anonymous:anonymous@IP
```
{% endcode %}



**Nmap FTP Scripts**

```bash
find / -type f -name ftp* 2>/dev/null | grep scripts
```

```bash
sudo nmap -sV -p21 -sC -A <IP>
```

```bash
sudo nmap -sV -p21 -sC -A IP --script-trace
```

### Check the service

```bash
nc -nv IP PORT
```

```bash
telnet IP PORT
```

```bash
openssl s_client -connect IP:PORT -starttls ftp
```
