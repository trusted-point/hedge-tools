[<img src='assets\hedge-banner.png' alt='banner' width= '99.9%'>]()

<font size = 7><center><b><u>About Hedge Blockchain</u></b></center></font>

* ### **[Hedge Blockchain](https://www.hedgeblock.io/)** Hedge Blockchain stands out as a state-of-the-art platform aimed at elevating the security, transparency, and efficiency of transactions. 
  
* ### Leveraging advanced M-sig transaction protocols, Hedge pioneers a blockchain network that ensures swifter and more dependable on-chain transactions.

<div align="center">
  <a href="https://www.hedgeblock.io/"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/85aaef48-7ea4-4857-b339-985645c6850c" alt="Hedge Website" width="16%"></a>
  <a href="https://github.com/hedgeblock"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/229ec400-72ff-48ee-ac18-7bdb1f5e221a" alt="Hedge Github" width="16%"></a>
  <a href="https://twitter.com/hedgeblockio"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/3978b7fc-d575-44a6-8d41-327c14c8ba31" alt="Hedge Twitter" width="16%"></a>
  <a href="https://discord.com/invite/fxmUNYTayQ"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/944a0b87-548d-4109-ad0c-def572d307cb" alt="Hedge Discord" width="16%"></a>
  <a href="https://medium.com/@hedgeblockio"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/ac52729b-64d7-44d1-9a66-1e0d159848f6" alt="Hedge Blog" width="16.2%"></a>
</div>

<font size = 7><center><b><u>Navigation</u></b></center></font>
- [Hardware requirements](#hardware-requirements)
- [TrustedPoint Services](#trustedpoint-services)
- [Installation guide](#installation-guide)
  - [1. Install required packages](#1-install-required-packages)
  - [2. Install Go](#2-install-go)
  - [3. Download `hedged` binary](#3-download-hedged-binary)
  - [4. Set up variables](#4-set-up-variables)
  - [5. Initialize the node](#5-initialize-the-node)
  - [6. Download genesis.json](#6-download-genesisjson)
  - [7. Add seeds and peers to the config.toml](#7-add-seeds-and-peers-to-the-configtoml)
  - [8. Change ports (Optional)](#8-change-ports-optional)
  - [9. Configure pruning to save storage (Optional)](#9-configure-pruning-to-save-storage-optional)
  - [10. Set min gas price](#10-set-min-gas-price)
  - [11. Enable indexer (Optional)](#11-enable-indexer-optional)
  - [12. Create a service file](#12-create-a-service-file)
  - [13. Start the node](#13-start-the-node)
  - [14. Create a wallet for your validator](#14-create-a-wallet-for-your-validator)
  - [15. Request tokens from the faucet](#15-request-tokens-from-the-faucet)
  - [16. Check wallet balance](#16-check-wallet-balance)
  - [17. Create a validator](#17-create-a-validator)
- [State sync](#state-sync)
  - [1. Stop the node](#1-stop-the-node)
  - [2. Backup priv\_validator\_state.json](#2-backup-priv_validator_statejson)
  - [3. Reset DB](#3-reset-db)
  - [4. Setup required variables (One command)](#4-setup-required-variables-one-command)
  - [4. Move priv\_validator\_state.json back](#4-move-priv_validator_statejson-back)
  - [5. Start the node](#5-start-the-node)
  - [6. Check the synchronization status](#6-check-the-synchronization-status)
  - [7. Disable state sync](#7-disable-state-sync)
- [Download fresh addrbook.json](#download-fresh-addrbookjson)
  - [1. Stop the node and use `wget` to download the file](#1-stop-the-node-and-use-wget-to-download-the-file)
  - [2. Restart the node](#2-restart-the-node)
  - [3. Check the synchronization status](#3-check-the-synchronization-status)
- [Add fresh persistent peers](#add-fresh-persistent-peers)
  - [1. Extract persistent\_peers from our endpoint](#1-extract-persistent_peers-from-our-endpoint)
  - [2. Restart the node](#2-restart-the-node-1)
  - [3. Check the synchronization status](#3-check-the-synchronization-status-1)
- [Download Snapshot](#download-snapshot)
  - [1. Download latest snapshot from our endpoint](#1-download-latest-snapshot-from-our-endpoint)
  - [2. Stop the node](#2-stop-the-node)
  - [3. Backup priv\_validator\_state.json](#3-backup-priv_validator_statejson)
  - [4. Reset DB](#4-reset-db)
  - [5. Extract files fromt the arvhive](#5-extract-files-fromt-the-arvhive)
  - [6. Move priv\_validator\_state.json back](#6-move-priv_validator_statejson-back)
  - [7. Restart the node](#7-restart-the-node)
  - [8. Check the synchronization status](#8-check-the-synchronization-status)
- [Useful commands](#useful-commands)
  - [Check node status](#check-node-status)
  - [Query your validator](#query-your-validator)
  - [Query missed blocks counter \& jail details of your validator](#query-missed-blocks-counter--jail-details-of-your-validator)
  - [Unjail your validator](#unjail-your-validator)
  - [Delegate tokens to your validator](#delegate-tokens-to-your-validator)
  - [Get your p2p peer address](#get-your-p2p-peer-address)
  - [Edit your validator](#edit-your-validator)
  - [Send tokens between wallets](#send-tokens-between-wallets)
  - [Query your wallet balance](#query-your-wallet-balance)
  - [Monitor server load](#monitor-server-load)
  - [Query active validators](#query-active-validators)
  - [Query inactive validators](#query-inactive-validators)
  - [Check logs of the node](#check-logs-of-the-node)
  - [Restart the node](#restart-the-node)
  - [Stop the node](#stop-the-node)
  - [Upgrade the node](#upgrade-the-node)
  - [Delete the node from the server](#delete-the-node-from-the-server)
  - [Example gRPC usage](#example-grpc-usage)
  - [Example REST API query](#example-rest-api-query)

## Hardware requirements
```py
- Memory: 8 GB RAM
- CPU: 4 cores
- Disk: 200 GB NVME
- Bandwidth: 1 Gbps
- Linux amd64 arm64 (Ubuntu LTS release)
```
## TrustedPoint Services

| Parameter | Value
|-|-
| indexing | kv
| pruning | custom (100/50)
| min-retain-blocks | 0
| snapshot-interval | 2000
| snapshot-keep-recent | 2
| minimum-gas-prices | 0.0025uhedge

---
- RPC: https://rpc-hedge-testnet.trusted-point.com
- REST API: https://api-hedge-testnet.trusted-point.com
- WSS: https://wss-hedge-testnet.trusted-point.com/websocket
- P2P Persistent Peer: cb7cfc03fbfc78fed10b24394041db54ef8658b7@peer-hedge-testnet.trusted-point.com:26995
---
- State sync: [Guide](#state-sync)
- Fresh Snapshot: [URL](https://rpc-hedge-testnet.trusted-point.com/latest_snapshot.tar.lz4) / [Guide](#download-snapshot) **(Being updated every 10 hours)**
- Fresh addrbook: [URL](https://rpc-hedge-testnet.trusted-point.com/addrbook.json) / [Guide](#download-fresh-addrbookjson) **(Being updated every 5 minutes)**
- Live Peers scanner: [URL](https://rpc-hedge-testnet.trusted-point.com/peers.txt) / [Guide](#add-fresh-persistent-peers) **(Being updated every 5 minutes)**

## Installation guide

### 1. Install required packages
```bash
sudo apt update && \
sudo apt install curl git jq build-essential gcc unzip wget lz4 -y
```
### 2. Install Go
```bash
cd $HOME && \
ver="1.21.3" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile && \
go version
```
### 3. Download `hedged` binary
```bash
cd $HOME
wget -O hedged https://github.com/hedgeblock/testnets/releases/download/v0.1.0/hedged_linux_amd64_v0.1.0
sudo chmod +x hedged
mv $HOME/hedged $HOME/go/bin
hedged version
```
### 4. Set up variables
```bash
# Customize if you need
echo 'export MONIKER="My_Node"' >> ~/.bash_profile
echo 'export CHAIN_ID="berberis-1"' >> ~/.bash_profile
echo 'export WALLET_NAME="wallet"' >> ~/.bash_profile
echo 'export RPC_PORT="26657"' >> ~/.bash_profile
source $HOME/.bash_profile
```
### 5. Initialize the node
```bash
cd $HOME
hedged init $MONIKER --chain-id $CHAIN_ID
hedged config chain-id $CHAIN_ID
hedged config node tcp://localhost:$RPC_PORT
hedged config keyring-backend os # You can set it to "test" so you will not be asked for a password
```
### 6. Download genesis.json
```bash
wget https://rpc-hedge-testnet.trusted-point.com/genesis.json -O $HOME/.hedge/config/genesis.json
```
### 7. Add seeds and peers to the config.toml
```bash
PEERS="7f53c0fba561febc278e00334a7d9af8d155c538@109.199.97.149:26656,a848ebed4c4a2e235e838640abd849d58eafd2e3@75.119.154.225:11856,6ca822c4d9fa868767e8a51e8a53d2ab13e8b633@162.55.212.77:26656,0c9fa03479edf7093241305be1f6b5a361039c28@45.85.147.82:11856,e94719f60d03fd1864551ad07746284083dd1bb9@161.97.131.194:26656,0b7dbbbf7ae007daafe3c49c142fce5dcc9a1c55@94.72.125.122:26656,e01e82e12beeb44b7ff3e98b1e62f9b976356e84@206.221.176.90:29656,4524fc7143cb352c89c0fdcd4f63927014cc25e3@45.85.146.138:26656,70f7dc74d3b6afa12b988d61707229e8e191d9a2@213.246.45.16:55656,481fc7a1fffee6cb4075deb6450e00085fe72dc0@65.109.30.35:11856,35b4dc6f1f4d4da6f293cd79b34fd0e21367a08f@37.60.227.6:11856,bbf8ef70a32c3248a30ab10b2bff399e73c6e03c@65.21.198.100:24056,f5d973568fec14272c8b3ced0cb74277ff5866fa@62.171.131.124:26656,0d9d4760a5f2ffb52177dfdd40fb46dfb05aabd9@167.86.98.179:26656,ade303649081d98ab8ab0287530afee607d5b95b@104.248.195.112:26656,cd023377468374e7482dd762db2977c6db44e10f@84.247.166.63:26656,b75d61ead2bdb1c8a1b0d6803b0ae6ed5c288ea2@37.27.35.64:26656,9a05e0f082d39bda195456f409ab1e004a78f03a@164.68.121.28:26656,2e8530ee80c99aea4c883f6a40b01366e8177f3b@64.226.96.33:28656,7879005ab63c009743f4d8d220abd05b64cfee3d@13.202.33.16:26656,54f0c004ee99ee82c6c2c54595ee4f2aa7572b53@116.203.18.135:26656,ad584c786fed7d067bbe582655ff0998cbdba1b9@213.199.33.133:12656,22b3741209f3bf95ccb5c93aa4dbbe2f9b6f6f32@14.161.28.247:26656,182b7f7ec60961b365808aece3837b6f1786a2b3@95.217.13.48:26656,93ca0a11cfeb0af49e3a2e565892216bca1321b1@65.109.164.113:26656,a52d446b9c44fec603b09ba0e4e278076d95dfcd@65.21.141.250:11856,b2a0bfb93d98e62802ec21eac60eaf11f17354d8@89.117.145.86:11856,93165d63303c5632b060a8dcfc8a440fd001c0c8@68.183.183.234:26656,042c20f5acd1274e87336f1686392d94e49af156@66.42.52.13:26656,93b946934c09a75608a4a70ec80aa27000286dd1@62.169.17.70:26656" && sed -i -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" $HOME/.hedge/config/config.toml
```
### 8. Change ports (Optional)
```bash
# Customize if you need
EXTERNAL_IP=$(wget -qO- eth0.me) \
PROXY_APP_PORT=26658 \
P2P_PORT=26656 \
PPROF_PORT=6060 \
API_PORT=1317 \
GRPC_PORT=9090 \
GRPC_WEB_PORT=9091
```
```bash
sed -i \
    -e "s/\(proxy_app = \"tcp:\/\/\)\([^:]*\):\([0-9]*\).*/\1\2:$PROXY_APP_PORT\"/" \
    -e "s/\(laddr = \"tcp:\/\/\)\([^:]*\):\([0-9]*\).*/\1\2:$RPC_PORT\"/" \
    -e "s/\(pprof_laddr = \"\)\([^:]*\):\([0-9]*\).*/\1localhost:$PPROF_PORT\"/" \
    -e "/\[p2p\]/,/^\[/{s/\(laddr = \"tcp:\/\/\)\([^:]*\):\([0-9]*\).*/\1\2:$P2P_PORT\"/}" \
    -e "/\[p2p\]/,/^\[/{s/\(external_address = \"\)\([^:]*\):\([0-9]*\).*/\1${EXTERNAL_IP}:$P2P_PORT\"/; t; s/\(external_address = \"\).*/\1${EXTERNAL_IP}:$P2P_PORT\"/}" \
    $HOME/.hedge/config/config.toml
```
```bash
sed -i \
    -e "/\[api\]/,/^\[/{s/\(address = \"tcp:\/\/\)\([^:]*\):\([0-9]*\)\(\".*\)/\1\2:$API_PORT\4/}" \
    -e "/\[grpc\]/,/^\[/{s/\(address = \"\)\([^:]*\):\([0-9]*\)\(\".*\)/\1\2:$GRPC_PORT\4/}" \
    -e "/\[grpc-web\]/,/^\[/{s/\(address = \"\)\([^:]*\):\([0-9]*\)\(\".*\)/\1\2:$GRPC_WEB_PORT\4/}" \
    $HOME/.hedge/config/app.toml
```
### 9. Configure pruning to save storage (Optional)
```bash
sed -i \
    -e "s/^pruning *=.*/pruning = \"custom\"/" \
    -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"100\"/" \
    -e "s/^pruning-interval *=.*/pruning-interval = \"10\"/" \
    "$HOME/.hedge/config/app.toml"
```
### 10. Set min gas price 
```bash
sed -i "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.0025uhedge\"/" $HOME/.hedge/config/app.toml
```
### 11. Enable indexer (Optional)
```bash
sed -i "s/^indexer *=.*/indexer = \"kv\"/" $HOME/.hedge/config/config.toml
```
### 12. Create a service file
```bash
sudo tee /etc/systemd/system/hedged.service > /dev/null <<EOF
[Unit]
Description=Hedge Node
After=network.target

[Service]
User=$USER
Type=simple
ExecStart=$(which hedged) start --home $HOME/.hedge
Restart=on-failure
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```
### 13. Start the node
```bash
sudo systemctl daemon-reload && \
sudo systemctl enable hedged && \
sudo systemctl restart hedged && \
sudo journalctl -u hedged -f -o cat
```
P.S. Consider [downloading snapshot](#download-snapshot) or using [state-sync](#state-sync) for the quick sync.

### 14. Create a wallet for your validator
```bash
hedged keys add $WALLET_NAME

# DO NOT FORGET TO SAVE THE SEED PHRASE
# You can add --recover flag to restore existing key instead of creating
```
### 15. Request tokens from the faucet

Copy the validator public key generated during the wallet setup process. You can find it by running the following command:
```bash
hedged tendermint show-validator --home $HOME/.hedge
```

Send the copied validator public key in the Discord  `#faucet` channel to get tokens.

-> <a href="https://discord.com/channels/1129302070659383388/1202196541725741127"><font size="4"><b><u>FAUCET</u></b></font></a> <-

### 16. Check wallet balance
Make sure your node is fully synced unless it won't work.
```bash
hedged status | jq .SyncInfo.catching_up
```
```bash
hedged q bank balances $(hedged keys show $WALLET_NAME -a) 
```
### 17. Create a validator
```bash
hedged tx staking create-validator \
  --amount=1000000uhedge \
  --pubkey=$(hedged tendermint show-validator) \
  --moniker=$MONIKER \
  --chain-id=$CHAIN_ID \
  --commission-rate=0.05 \
  --commission-max-rate=0.10 \
  --commission-max-change-rate=0.01 \
  --min-self-delegation=1 \
  --from=$WALLET_NAME \
  --identity="" \
  --website="" \
  --details="Hedge to the moon!" \
  --fees 2000uhedge --gas 200000 \
  -y
```
Do not forget to save `priv_validator_key.json` file located in $HOME/.hedge/config/

## State sync

### 1. Stop the node
```bash
sudo systemctl stop hedged
```
### 2. Backup priv_validator_state.json 
```bash
cp $HOME/.hedge/data/priv_validator_state.json $HOME/.hedge/priv_validator_state.json.backup
```
### 3. Reset DB
```bash
hedged tendermint unsafe-reset-all --home $HOME/.hedge --keep-addr-book
```
### 4. Setup required variables (One command)
```bash
PEERS="cb7cfc03fbfc78fed10b24394041db54ef8658b7@peer-hedge-testnet.trusted-point.com:26995" && \
RPC="https://rpc-hedge-testnet.trusted-point.com:443" && \
LATEST_HEIGHT=$(curl -s --max-time 3 --retry 2 --retry-connrefused $RPC/block | jq -r .result.block.header.height) && \
TRUST_HEIGHT=$((LATEST_HEIGHT - 1500)) && \
TRUST_HASH=$(curl -s --max-time 3 --retry 2 --retry-connrefused "$RPC/block?height=$TRUST_HEIGHT" | jq -r .result.block_id.hash) && \

if [ -n "$PEERS" ] && [ -n "$RPC" ] && [ -n "$LATEST_HEIGHT" ] && [ -n "$TRUST_HEIGHT" ] && [ -n "$TRUST_HASH" ]; then
    sed -i \
        -e "/\[statesync\]/,/^\[/{s/\(enable = \).*$/\1true/}" \
        -e "/^rpc_servers =/ s|=.*|= \"$RPC,$RPC\"|;" \
        -e "/^trust_height =/ s/=.*/= $TRUST_HEIGHT/;" \
        -e "/^trust_hash =/ s/=.*/= \"$TRUST_HASH\"/" \
        -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" \
        $HOME/.hedge/config/config.toml
    echo -e "\nLATEST_HEIGHT: $LATEST_HEIGHT\nTRUST_HEIGHT: $TRUST_HEIGHT\nTRUST_HASH: $TRUST_HASH\nPEERS: $PEERS\n\nALL IS FINE"
else
    echo -e "\nError: One or more variables are empty. Please try again or change RPC\nExiting...\n"
fi
```
### 4. Move priv_validator_state.json back
```bash
mv $HOME/.hedge/priv_validator_state.json.backup $HOME/.hedge/data/priv_validator_state.json
```
### 5. Start the node
```bash
sudo systemctl restart hedged && sudo journalctl -u hedged -f -o cat
```
You should see the following logs. It may take up to 5 minutes for the snapshot to be discovered. If doesn't work, try downloading [snapshot](#download-snapshot)
```py
2:39PM INF sync any module=statesync msg="Discovering snapshots for 15s" server=node
2:39PM INF Discovered new snapshot format=3 hash="?^��I��\r�=�O�E�?�CQD�6�\x18�F:��\x006�" height=602000 module=statesync server=node
2:39PM INF Discovered new snapshot format=3 hash="%���\x16\x03�T0�v�f�C��5�<TlLb�5��l!�M" height=600000 module=statesync server=node
2:42PM INF VerifyHeader hash=CFC07DAB03CEB02F53273F5BDB6A7C16E6E02535B8A88614800ABA9C705D4AF7 height=602001 module=light server=node
```
After some time you should see the following logs. It make take 5 minutes for the node to catch up the rest of the blocks
```py
2:43PM INF indexed block events height=602265 module=txindex server=node
2:43PM INF executed block height=602266 module=state num_invalid_txs=0 num_valid_txs=0 server=node
2:43PM INF commit synced commit=436F6D6D697449447B5B31313720323535203139203132392031353920313035203136352033352031353320313220353620313533203139352031372036342034372033352034372032333220373120313939203720313734203620313635203338203336203633203235203136332039203134395D3A39333039417D module=server
2:43PM INF committed state app_hash=75FF13819F69A523990C3899C311402F232FE847C707AE06A526243F19A30995 height=602266 module=state num_txs=0 server=node
2:43PM INF indexed block events height=602266 module=txindex server=node
2:43PM INF executed block height=602267 module=state num_invalid_txs=0 num_valid_txs=0 server=node
2:43PM INF commit synced commit=436F6D6D697449447B5B323437203134322032342031313620323038203631203138362032333920323238203138312032333920313039203336203420383720323238203236203738203637203133302032323220313431203438203337203235203133302037302032343020313631203233372031312036365D3A39333039427D module=server
```
### 6. Check the synchronization status
```bash
hedged status | jq .SyncInfo
```
### 7. Disable state sync
```bash
sed -i -e "/\[statesync\]/,/^\[/{s/\(enable = \).*$/\1false/}" $HOME/.hedge/config/app.toml
```
## Download fresh addrbook.json

### 1. Stop the node and use `wget` to download the file
```bash
sudo systemctl stop hedged && \
wget -O $HOME/.hedge/config/addrbook.json https://rpc-hedge-testnet.trusted-point.com/addrbook.json
```
### 2. Restart the node
```bash
sudo systemctl restart hedged && sudo journalctl -u hedged -f -o cat
```
### 3. Check the synchronization status
```bash
hedged status | jq .SyncInfo
```
The file is being updated every 5 minutes

## Add fresh persistent peers

### 1. Extract persistent_peers from our endpoint
```bash
PEERS=$(curl -s --max-time 3 --retry 2 --retry-connrefused "https://rpc-hedge-testnet.trusted-point.com/peers.txt")
if [ -z "$PEERS" ]; then
    echo "No peers were retrieved from the URL."
else
    echo -e "\nPEERS: "$PEERS""
    sed -i "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" "$HOME/.hedge/config/config.toml"
    echo -e "\nConfiguration file updated successfully.\n"
fi
```
### 2. Restart the node
```bash
sudo systemctl restart hedged && sudo journalctl -u hedged -f -o cat
```
### 3. Check the synchronization status
```bash
hedged status | jq .SyncInfo
```
Peers are being updated every 5 minutes

## Download Snapshot

### 1. Download latest snapshot from our endpoint
```bash
wget https://rpc-hedge-testnet.trusted-point.com/latest_snapshot.tar.lz4 
```
### 2. Stop the node
```bash
sudo systemctl stop hedged
```
### 3. Backup priv_validator_state.json 
```bash
cp $HOME/.hedge/data/priv_validator_state.json $HOME/.hedge/priv_validator_state.json.backup
```
### 4. Reset DB
```bash
hedged tendermint unsafe-reset-all --home $HOME/.hedge --keep-addr-book
```
### 5. Extract files fromt the arvhive 
```bash
lz4 -d -c ./latest_snapshot.tar.lz4 | tar -xf - -C $HOME/.hedge
```
### 6. Move priv_validator_state.json back
```bash
mv $HOME/.hedge/priv_validator_state.json.backup $HOME/.hedge/data/priv_validator_state.json
```
### 7. Restart the node
```bash
sudo systemctl restart hedged && sudo journalctl -u hedged -f -o cat
```
### 8. Check the synchronization status
```bash
hedged status | jq .SyncInfo
```
Snapshot is being updated every 3 hours

## Useful commands
### Check node status 
```bash
hedged status | jq
```
### Query your validator
```bash
hedged q staking validator $(hedged keys show $WALLET_NAME --bech val -a) 
```
### Query missed blocks counter & jail details of your validator
```bash
hedged q slashing signing-info $(hedged tendermint show-validator)
```
### Unjail your validator 
```bash
hedged tx slashing unjail --from $WALLET_NAME --fees 2000uhedge --gas 200000 -y
```
### Delegate tokens to your validator 
```bash 
hedged tx staking delegate $(hedged keys show $WALLET_NAME --bech val -a)  <AMOUNT>uhedge --from $WALLET_NAME --fees 2000uhedge --gas 200000 -y
```
### Get your p2p peer address
```bash
hedged status | jq -r '"\(.NodeInfo.id)@\(.NodeInfo.listen_addr)"'
```
### Edit your validator
```bash 
hedged tx staking edit-validator --website="<WEBSITE>" --details="<DESCRIPTION>" --moniker="<NEW_MONIKER>" --from=$WALLET_NAME --fees 2000uhedge --gas 200000 -y
```
### Send tokens between wallets 
```bash
hedged tx bank send $WALLET_NAME <TO_WALLET> <AMOUNT>uhedge --fees 2000uhedge --gas 200000 -y
```
### Query your wallet balance 
```bash
hedged q bank balances $WALLET_NAME
```
### Monitor server load
```bash 
sudo apt update
sudo apt install htop -y
htop
```
### Query active validators
```bash
hedged q staking validators -o json --limit=1000 \
| jq '.validators[] | select(.status=="BOND_STATUS_BONDED")' \
| jq -r '.tokens + " - " + .description.moniker' \
| sort -gr | nl
```
### Query inactive validators
```bash
hedged q staking validators -o json --limit=1000 \
| jq '.validators[] | select(.status=="BOND_STATUS_UNBONDED")' \
| jq -r '.tokens + " - " + .description.moniker' \
| sort -gr | nl
```
### Check logs of the node
```bash
sudo journalctl -u hedged -f -o cat
```
### Restart the node
```bash
sudo systemctl restart hedged
```
### Stop the node
```bash
sudo systemctl stop hedged
```
### Upgrade the node
```bash
HEDGE_VERSION=<version>

cd $HOME
wget -O hedged https://github.com/hedgeblock/testnets/releases/download/$HEDGE_VERSION/hedged_linux_amd64_v0.1.0
sudo chmod +x hedged
mv $HOME/hedged $HOME/go/bin
hedged version

# Restrt the node
sudo systemctl restart hedged && sudo journalctl -u hedged -f -o cat
```
### Delete the node from the server
```bash
# !!! IF YOU HAVE CREATED A VALIDATOR, MAKE SURE TO BACKUP `priv_validator_key.json` file located in $HOME/.hedge/config/ 
sudo systemctl stop hedged
sudo systemctl disable hedged
sudo rm /etc/systemd/system/hedged.service
rm -rf $HOME/.hedge
```
### Example gRPC usage
```bash
wget https://github.com/fullstorydev/grpcurl/releases/download/v1.7.0/grpcurl_1.7.0_linux_x86_64.tar.gz
tar -xvf grpcurl_1.7.0_linux_x86_64.tar.gz
chmod +x grpcurl
./grpcurl  -plaintext  localhost:$GRPC_PORT list
### MAKE SURE gRPC is enabled in app.toml
# grep -A 3 "\[grpc\]" $HOME/.hedge/config/app.toml
```
### Example REST API query
```bash
curl localhost:$API_PORT/cosmos/staking/v1beta1/validators
### MAKE SURE API is enabled in app.toml
# grep -A 3 "\[api\]" $HOME/.hedge/config/app.toml
```
