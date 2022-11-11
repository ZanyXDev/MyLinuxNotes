- Run socks5 tunnel over ssh

`ssh -D 1080 -fN  username@server_with_internet_access_ip`

- Set socks5 proxy for apt

`echo "Acquire::https::proxy \"socks5h://127.0.0.1:1080\";" >>/etc/apt/apt.conf.d/50proxy.conf`

`echo "Acquire::http::proxy \"socks5h://127.0.0.1:1080\";" >>/etc/apt/apt.conf.d/50proxy.conf`

- Config git to use SOCKS5

    For https:// and http://(e.g. http://github.com, https://github.com), run the following script.

git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'

    For git://(e.g. git://github.com), run git config --global core.gitproxy 'socks5://127.0.0.1:1080'
    For ssh(e.g. git@github.com,ssh://git@github.com), add ProxyCommand nc -x localhost:1080 %h %p to ~/.ssh/config file.

    git config --global is stored in ~/.gitconfig while local config settings is in ./.git/config. To remove a configuration, e.g. run git config --global --unset core.gitproxy.
