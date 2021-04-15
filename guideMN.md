**Make sure that you have the following requirements.**

- Required amount of astron to setup the masternode.
- A wallet to store your coins.
- A server or VPS.


**Prepare your VPS**
Install Ubuntu Server 18.04 on a VPS.

**Update your Ubuntu machine.**

sudo apt-get update<br>
sudo apt-get upgrade<br>

**Install the required dependencies.**

sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev<br><br>
sudo apt-get install libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip wget vim software-properties-common<br>

**Install Berkeley DB.**

sudo add-apt-repository ppa:bitcoin/bitcoin<br>
sudo apt-get update<br>
sudo apt-get install libdb4.8-dev libdb4.8++-dev<br>

**Download the daemon and tools from Github**

wget "https://github.com/Astron-Developer/Astron-Core/releases/download/1.0.0.0/linux_daemon.zip" -O astron-daemon-linux.zip

**Extract the tar files.**

unzip astron-daemon-linux.zip

**Install the daemon and tools.**

chmod +x astrond astron-cli astron-tx<br>
sudo mv astrond astron-cli astron-tx /usr/bin/<br>

**Create the config file.**

mkdir $HOME/.astron<br>
vim $HOME/.astron/astron.conf<br>

**Paste the following lines in astron.conf.**
```
#----
rpcuser=rpc_astron
rpcpassword=exemplepass
rpcallowip=127.0.0.1
#----
listen=1
server=1
daemon=1
maxconnections=64
#----
#masternode=1
#masternodeprivkey=
externalip=ip_da_vps
#----
```
**Leave the fields “masternode” and “masternodeprivkey” commented out.**

Replace the text “ip_da_vps” with the external IP address of your VPS.<br>

Example:``` externalip=127.0.0.1 ```<br>

**Start your node with the following command.**

astrond

**Wait until the daemon has finished downloading the blockchain.**


**Send the collateral**
Open your wallet and wait until your wallet has downloaded the blockchain.<br>

Go to “Tools”.<br>
Click “Debug console”.<br>
This is the console where you will execute all commands.<br>

**Create a new masternode private key.**

createmasternodekey<br>

Example output<br>
```
7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5
```
**Show your collateral address.**

getaccountaddress "MN1"<br>

Example output<br>

DB5uyEU1G7UdTg8L5HiAZMsDS9vgsKKWfa<br>

**Transfer the required amount of ```30000 DEV``` to the “collateral address” that you created using the command “getaccountaddress "MN1"”.**

**Wait until the transaction has the ```21 confirmations.```**

Go to “Tools”.<br>
Click “Debug console”.<br>
Enter the following command.<br>

getmasternodeoutputs<br>

Example output<br>

```
[
  {
    "txhash": "506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9",
    "outputidx": 1
  }
]
```
Go to “Tools”.<br>
Click “Open Masternode Configuration File”.<br>

Modify the following line and paste it into notepad.<br>
```
MN1 ip_da_vps:24484 7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5 506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9 1
```
```MN1``` - Alias for your masternode.<br>

```ip_da_vps``` - External IP address of your VPS.<br>

```24484``` - Replace with P2P port of your coin.<br>

```7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5``` - Masternode private key from the command “createmasternodekey”.<br>

```506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9``` - Value “txhash” from the command “getmasternodeoutputs”.<br>

```1``` - Value “outputidx” from the command “getmasternodeoutputs”.<br>


**Save the file and close notepad.**

**Close your wallet.**


**Register your masternode**
Place the masternode private key in the config file of your masternode and uncomment the values “masternode” and “masternodeprivkey”.<br>

Example config<br>
```
#----
rpcuser=rpc_astron
rpcpassword=kuw05sqio7bcm8z96o7redv17xws1lw6xpd1qf33
rpcallowip=127.0.0.1
#----
listen=1
server=1
daemon=1
maxconnections=64
#----
masternode=1
masternodeprivkey=7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5
externalip=ip_da_vps
#----
```
**Restart your masternode using the following commands.**

astron-cli stop<br>
astrond<br>

**Open your wallet.**

Go to “Settings”.<br>
Click “Unlock Wallet”.<br>

**Enter your wallet passphrase and unlock your wallet.**

Go to “Tools”.<br>
Click “Debug console”.<br>

**Start your masternode using the command.**

startmasternode alias false MN1<br>

**Your masternode is now registered and will appear in the masternode list.**

**You can check the status of your masternode using the command "getmasternodestatus".**

astron-cli getmasternodestatus<br>

Example output<br>

```
{
  "txhash": "506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9",
  "outputidx": 1,
  "netaddr": "136.144.171.201:9999",
  "addr": "DB5uyEU1G7UdTg8L5HiAZMsDS9vgsKKWfa",
  "status": 4,
  "message": "Masternode successfully started"
}
```
