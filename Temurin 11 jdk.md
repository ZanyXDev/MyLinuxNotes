## Install Eclipse Temurin 11 jdk Package Debian 12
#1. Ensure the necessary packages are present:

`apt install -y wget apt-transport-https gnupg`
   
   *2.Download the Eclipse Adoptium GPG key:
    
    `sudo wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | apt-key add -`
    
    *3.Fix Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
` apt-key list`
  Find las 8 digits rsa fingerprint
```
-----------------------------------------------
pub   rsa2048 2021-11-16 [SC]
      3B04 D753 C905 0D9A 5D34  3F39 843C 48A5 65F8 F04B
uid         [ неизвестно ] Adoptium GPG Key (DEB/RPM Signing Key) <temurin-dev@eclipse.org>
sub   rsa2048 2021-11-16 [E]
```
`sudo apt-key export 65F8F04B | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/adotiom_temurin.gpg`

`sudo apt-key --keyring /etc/apt/trusted.gpg del 65F8F04B`

4.Configure the Eclipse Adoptium apt repository by replacing the values in angle brackets:

`echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list`

`sudo apt update`

`sudo install temurin-11-jdk`
