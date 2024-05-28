# SMB

**SMBclient - Connecting to the Share**

```bash
smbclient -N -L //IP
```

### Nmap

```bash
sudo nmap IP -sV -sC -p139,445
```

### RPCclient

```bash
rpcclient -U "" IP
```

<table data-header-hidden><thead><tr><th width="319"></th><th></th></tr></thead><tbody><tr><td><strong>Query</strong></td><td><strong>Description</strong></td></tr><tr><td><code>srvinfo</code></td><td>Server information.</td></tr><tr><td><code>enumdomains</code></td><td>Enumerate all domains that are deployed in the network.</td></tr><tr><td><code>querydominfo</code></td><td>Provides domain, server, and user information of deployed domains.</td></tr><tr><td><code>netshareenumall</code></td><td>Enumerates all available shares.</td></tr><tr><td><code>netsharegetinfo &#x3C;share></code></td><td>Provides information about a specific share.</td></tr><tr><td><code>enumdomusers</code></td><td>Enumerates all domain users.</td></tr><tr><td><code>queryuser &#x3C;RID></code></td><td>Provides information about a specific user.</td></tr></tbody></table>

**Brute Forcing User RIDs**

```bash
for i in $(seq 500 1100);do rpcclient -N -U "" IP -c "queryuser 0x$(printf '%x\n' $i)" | grep "User Name\|user_rid\|group_rid" && echo "";done
```

An alternative to this would be a Python script from [Impacket](https://github.com/SecureAuthCorp/impacket) called [samrdump.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/samrdump.py).

### SMBmap

```bash
smbmap -H IP
```

### CrackMapExec

```bash
crackmapexec smb IP --shares -u '' -p ''
```

### Enum4Linux-ng

```bash
git clone https://github.com/cddmp/enum4linux-ng.git
cd enum4linux-ng
pip3 install -r requirements.txt
./enum4linux-ng.py IP -A
```

