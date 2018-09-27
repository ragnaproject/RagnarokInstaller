# RagnarokInstaller

This script allows for easy setup of linux masternode or CLI wallet. 

Just run with:
```bash
bash <(curl https://raw.githubusercontent.com/ragnaproject/RagnarokInstaller/master/ragnarok_installer)
```
as root on your linux VPS, or computer if you just want CLI wallet. 

# Ragnarok
Shell script to install a [Ragnarok Masternode](https://ragnaproject.io) on a Linux server running Ubuntu 16.04. 
***

## Installation
```
bash <(curl https://raw.githubusercontent.com/ragnaproject/RagnarokInstaller/master/ragnarok_installer)
```
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the Ragnarok Desktop Wallet.  
2. Go to RECEIVE and create a New Address: **MN1**  
3. Send **10000** RAGNA to **MN1**. You need to send all 10000 coins in one single transaction.
4. Wait for 15 confirmations.  
5. Go to **Tools -> "Debug Window - Console"**  
6. Type the following command: **masternode outputs**  
7. Click on **Tools -> open masternode configuration file**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Open **Debug Console** and type:
```
startmasternode alias false <name>  # Replace <name> with your masternode alias
```
11. Login to your VPS and check your masternode status by running the following command. If you get **Status 4**, it means your masternode is active.
```
ragnarok-cli masternode status
```
***

## Usage:
```
ragnarok-cli mnsync status
ragnarok-cli masternode status  
ragnarok-cli getinfo
```
Also, if you want to check/start/stop **ragnarok**, run one of the following commands as **root**:

```
ragnarok-cli getblockcount #To get blockcount
ragnarok-cli stop #To stop masternode
./ragnarokd -resync &  #To Resync
systemctl status condominium.service  #o check Ragnarok service status
systemctl start ragnarok.service  #To start Ragnarok service
systemctl stop ragnarok.service  #To stop Ragnarok service
ragnarok-cli masternode count  #To check masternode list
```  
***

