## About

Mitm experiment with real time decryption in wireshark.

## Used components

mitmproxy
chromium
firefox
wireshark

## Usage

### start the containers.
```bash
create --driver host int_net
docker-compose up -d
docker-compose logs
```

### copy your pub key to the volume
```bash
docker ps | grep chromium
docker cp ~/.ssh/id_rsa.pub mitmproxy_chromium_1:/root/.ssh/authorized_keys
```

### start chromium
You can start the apps now in your local X with ssh
```bash
ssh -C -X -i id_rsa -p 1111 root@<dockerhost>
export all_proxy=proxy:8080
chromium-browser --no-sandbox --disable-gpu
```
Wait a while and chromium pops up in your X server.
If it all went well the browser has a certificate problem.
Go to chromium settings, then to the bottom and click
'Show advanced setting'. Go to HTTPS/SSL click 'Manage Certificates'.
Choose Authorities tab and click 'import'. Choose /root/mitmproxy/mitmproxy-ca.cert.
Trust the certificate and your ready to go.



### add ca certificate
Import the mitmproxy mitmproxy-ca.pem into chromium
