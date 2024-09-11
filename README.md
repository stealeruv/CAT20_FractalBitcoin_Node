# CAT20 MINT

1. **Install Packages:**

```shell
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential pkg-config libssl-dev git wget jq make gcc chrony -y
```

## Node Installation

1. **Download the Fractal Repository:**

```shell
wget https://github.com/fractal-bitcoin/fractald-release/releases/download/v0.2.1/fractald-0.2.1-x86_64-linux-gnu.tar.gz
```

2. **Extract the File:**

```shell
tar -zxvf fractald-0.2.1-x86_64-linux-gnu.tar.gz
```

3. **Create the Data Folder:**

```shell
cd fractald-0.2.1-x86_64-linux-gnu && mkdir data
```

4. **Copy the Configuration File:**

```shell
cp ./bitcoin.conf ./data
```
5. Edit file
```
cd data && nano ./bitcoin.conf
```
6. Paste 
```
port=8333
 txindex=1
server=1
rest=1
 rpcallowip=0.0.0.0/0
rpcbind=0.0.0.0
rpcport=8332
rpcuser=bitcoin
rpcpassword=opcatAwesome
rpcworkqueue=2048
rpcthreads=32
rpcservertimeout=120
zmqpubhashblock=tcp://0.0.0.0:8330 zmqpubrawtx=tcp://0.0.0.0:8331  maxconnections=50
debug=bench
debug=netmsg
```

7. Run Node

```
./bin/bitcoind -datadir=./data/ -maxtipage=504576000
```
8. Install Node js


# installs nvm (Node Version Manager)
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
```
# download and install Node.js (you may need to restart the terminal)
```
nvm install 22
```
# verifies the right Node.js version is in the environment
```
node -v # should print `v22.8.0`
```
# verifies the right npm version is in the environment
```
npm -v # should print `10.8.2`
```
8. CATBOX 

```
git clone https://github.com/CATProtocol/cat-token-box.git
```
```
cd cat-token-box && yarn install && yarn build
```
8. Create Wallet

```
yarn cli wallet create
```

Fund the wallet (right now use coinex to buy and withraw $FB)

```
cd ./packages/tracker/ && docker-compose up
```
Fund the wallet (right now use coinex to buy and withraw $FB)

