# Astron-Core
# Version: 1.0.0.1
Official Astron Core Cryptocurrency Repository.

# Contact:
> 💬Telegram:
**https://t.me/astron_dev**

> 💬Facebook:
**https://www.facebook.com/groups/153710193172790**

> 💬Twitter:
**https://twitter.com/Astron_DEV**

> 💬BTCTalk:
**...**

> ✉️E-mail:
**contato@astron.dev**

> 🌎Website:
**https://astron.dev**

> 🌎Block Explorer:
**http://explorer.astron.services**

# ESPECIFICAÇÕES:
- **Nome:** Astron <br>
- **Simbolo:** DEV <br>
- **Algoritimo:** Quark <br>
- **Block type:** PoS/PoW/MN <br>
- **Reward	(PoW):** 2% - end time block: 45.002 <br>
- **Reward (PoS):** 5% - reward up hailvings<br>
- **Reward Superblock:** 3% <br>
- **Reward Masternode:** 98% - reward down hailvings<br>
- **Masternode amount:** 25000 DEV's <br>
- **Confirmações de Masternode:** 21 blocos <br>
- **Maturidade de Masternode:** 16 <br>
- **BlockTime:** 1 minute <br>
- **Resete Dificuldade:**	3 minutes <br>
- **Confirmações de Transação:** 5 blocos <br>

**Use the following instructions to compile a daemon and GUI wallet for Ubuntu Server 18.04.**

**Update your Ubuntu machine.**

sudo apt-get update<br>
sudo apt-get upgrade<br>

**Install the required dependencies.**

sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl1.0-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev -y<br>

sudo apt-get install libminiupnpc-dev libzmq3-dev libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev unzip libgmp3-dev -y<br>

**Install Berkeley DB.**

sudo add-apt-repository ppa:bitcoin/bitcoin<br>
sudo apt-get update<br>
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y<br>

**Create a directory for the source code.**

cd ~/<br>
mkdir source_code<br>

**Download the source code from Github.**

sudo apt-get install git -y<br>
git clone https://github.com/Astron-Developer/Astron-Core.git source_code<br>
cd source_code<br>
./autogen.sh<br>
./configure --with-incompatible-bdb<br>
make<br>

**the astrond astron-cli and astron-tx files are in source_code/src**<br>

**the astron-qt file will be in source_code/src/qt**<br>

**move files to usr/bin**<br>

# astron.conf
```sh
rpcuser=rpc_exampleuser
rpcpassword=rpc_exemplepass
rpcallowip=0.0.0.0/0
listen=1
server=1
txindex=1
daemon=1
addnode=node1.astron.dev
addnode=node2.astron.dev
addnode=node3.astron.dev
addnode=node4.astron.dev
```
