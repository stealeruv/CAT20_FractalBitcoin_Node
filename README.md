# CAT20 Token Minting using Fractal Bitcoin Node

Join TG : https://t.me/cryptoconsol

Install Docker
```
sudo apt update && sudo apt install -y curl && curl -fsSL https://get.docker.com -o get-docker.sh && sudo sh get-docker.sh
Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
Make this executable
```
sudo chmod +x /usr/local/bin/docker-compose
```
Install npm
```
sudo apt-get install npm -y
```
Install n pacakges globally
```
sudo npm i n -g
```
Switch to stable node version
```
sudo n stable
```
Install yarn package globally
```
sudo npm i -g yarn
```
Clone Cat Protocol repo
```
git clone https://github.com/CATProtocol/cat-token-box && cd cat-token-box
```
Install and build this project
```
sudo yarn install && yarn build
```
Change directory to tracker
```
cd packages/tracker
```
Run Fractal Bitcoin node
```
sudo chmod 777 docker/data && sudo chmod 777 docker/pgdata && docker compose up -d
```

If you have firewall
```
ufw allow 3000
ufw allow 5432
ufw allow 8333
ufw allow 8332
```

Build docker image
```
cd ../../ && docker build -t tracker:latest .
```
Run the container
```
docker run -d \
    --name tracker \
    --add-host="host.docker.internal:host-gateway" \
    -e DATABASE_HOST="host.docker.internal" \
    -e RPC_HOST="host.docker.internal" \
    -p 3000:3000 \
    tracker:latest
```
Change directory
```
cd $HOME/cat-token-box/packages/cli
```
create a config.json 
```
nano config.json
```
Paste this
```
{
  "network": "fractal-mainnet",
  "tracker": "http://127.0.0.1:3000",
  "dataDir": ".",
  "maxFeeRate": 30,
  "rpc": {
      "url": "http://127.0.0.1:8332",
      "username": "bitcoin",
      "password": "opcatAwesome"
  }
}
```


CTRL + X then Y and Enter


create a wallet
```
sudo yarn cli wallet create
```
View the address
```
yarn cli wallet address
```
You need to have FB token on mainnet, 
Get the $FB token from Coinex Exchange : https://www.coinex.com/register?refer_code=pkwtn

Check the balance
```
sudo yarn cli wallet balances
```
**Wait untill blocks to sync**
Single Mint Command
```
sudo yarn cli mint -i 45ee725c2c5993b3e4d308842d87e973bf1951f5f7a804b21e4dd964ecd12d6b_0 5 --fee-rate 150
```
or use Multi Mint Automation
```
cd
cd && nano cat-token-box/packages/cli/mint_script.sh
```
Paste this
Edit the fee rate accordingly
```
sudo yarn cli mint -i 45ee725c2c5993b3e4d308842d87e973bf1951f5f7a804b21e4dd964ecd12d6b_0 5 --fee-rate 150
```
CTRL + X then Y and Enter

```
chmod +x mint_script.sh
bash ~/cat-token-box/packages/cli/mint_script.sh
```

Check the fee and change according to the market : https://explorer.unisat.io/fractal-mainnet

