### Use ssl in local development via nginx and self-signed certificate

> **Warning** Tested in:
>
> Linux: Chrome, Firefox
>
> Windows: Chrome

## Linux
#### Install [mkcert](https://github.com/FiloSottile/mkcert#installation "mkcert")
    curl -JLO "https://dl.filippo.io/mkcert/latest?for=linux/amd64"
    chmod +x mkcert-v*-linux-amd64
    sudo cp mkcert-v*-linux-amd64 /usr/local/bin/mkcert
	
    sudo apt-get update
    sudo apt-get install libnss3-tools
    mkcert --install

#### Generate ssl certificates
    cd nginx-ssl-localhost   # replace whth repo folder
    mkcert -cert-file ./ssl/local.crt -key-file ./ssl/local.key  localhost "*.com.local" 127.0.0.1 ::1

#### Add hostnames to /etc/hosts
    echo '127.0.0.1 example1.com.local' | sudo tee -a /etc/hosts
    echo '127.0.0.1 example2.com.local' | sudo tee -a /etc/hosts

#### Start nginx
    docker-compose up

#### Check ssl
Open [site1](https://example1.com.local "site1") and [site2](https://example2.com.local "site2") in browser

## Windows
#### Download [mkcert](https://dl.filippo.io/mkcert/v1.4.4?for=windows/amd64 "mkcert") binary or check [release](https://github.com/FiloSottile/mkcert/releases "release") page
#### Generate ssl certificates
    Win+R -> cmd -> Enter
    C:\Users\User\Downloads\mkcert-v1.4.4-windows-amd64.exe -install
    cd nginx-ssl-localhost   # replace whth repo folder
    C:\Users\User\Downloads\mkcert-v1.4.4-windows-amd64.exe -cert-file ./ssl/local.crt -key-file ./ssl/local.key  localhost "*.com.local" 127.0.0.1 ::1

#### Edit file C:\Windows\System32\drivers\etc\hosts
    127.0.0.1 example.com.local
    127.0.0.1 example2.com.local

#### Start nginx
    docker-compose up

#### Check ssl
Open [site1](https://example1.com.local "site1") and [site2](https://example2.com.local "site2") in browser
