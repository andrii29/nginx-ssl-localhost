#### Install [mkcert](https://github.com/FiloSottile/mkcert#installation "mkcert")
    curl -JLO "https://dl.filippo.io/mkcert/latest?for=linux/amd64"
    chmod +x mkcert-v*-linux-amd64
    sudo cp mkcert-v*-linux-amd64 /usr/local/bin/mkcert
	
    sudo apt-get update
    sudo apt-get install libnss3-tools
    mkcert --install

#### Generate ssl certificates
    mkcert -cert-file ./ssl/local.crt -key-file ./ssl/local.key  localhost "*.com.local" 127.0.0.1 ::1

#### Add hostnames to /etc/hosts
    echo '127.0.0.1 example1.com.local' | sudo tee -a /etc/hosts
    echo '127.0.0.1 example2.com.local' | sudo tee -a /etc/hosts

#### Start nginx
    docker-compose up

#### Check ssl
Open [site1](https://example1.com.local "site1") and [site2](https://example2.com.local "site2") in browser
