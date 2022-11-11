#Run socks5 tunnel over ssh
`ssh -D 1080 -fN  username@server_with_internet_access_ip`
#Set socks5 proxy for apt
`cat /etc/apt/apt.conf.d/50proxy.conf
echo "Acquire::https::proxy \"socks5h://127.0.0.1:1080\";" >>/etc/apt/apt.conf.d/50proxy.conf
echo "Acquire::http::proxy \"socks5h://127.0.0.1:1080\";" >>/etc/apt/apt.conf.d/50proxy.conf`
