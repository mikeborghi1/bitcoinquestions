
### 1. Interacting with cryptocurrency wallets

###### Nearly every cryptocurrency comes with it's own 'official' or 'reference' client, like bitcoinqt litecoinqt ect.

###### These clients have a means of being controlled remotely through what are called rpc commands. Using these, you can do anything the wallet is capable of like getting new addresses and sending transactions. You set an rpc username and password which are sent along with the rpc call in order to prevent others from ontrolling your wallet.  Here is a list of bitcoin rpc calls for the official wallet https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_calls_list  

###### There are many software libraries that simplify the usage of rpc calls by giving the developer simple functions like getnewaddress() so you don't have to manually type out the code that performs the rpc call.  This is what web3 is.  However, these pieces of software typically dont download the blockchain and require you to connect to a fully running node as a source of information.  There are many of these abstracted libraries written in many different languages.  So in order to interact with the blockchains you must either have an instance of the bitcoinqt client and communicate with that directly, or you can use an api like web3 or bitcoinj (java bitcoin api) or the many others to perform the tasks necessary to create a wallet system for an exchange. 

##### This is a very brief overview and i'm leaving a lot out but am happy to flesh out more details.  
##
### 2. Best practicces in managing the entirety of coin holdings

###### The most common implemented system involves the coins being stored in two distinct types of wallets:

* Hot wallet
	* Is connected to the exchange live and withdrawals are processed automatically by the exchange code.  When a user submits a withdrawal, the wallet creates a transaction without any human interaction.
	* This wallet is connected to the internet and is actitvely integrated into he exchange and therefore anyone who can manage to take control of the servers with the wallets that contain coins, then they can grab them all.
	* A hotwallet is necessary for the withdrawals the be processed without human intervention.  This wallet contains only a fraction of the total holdings and usually more is added to it manually by humans in order to have enough stock to process withdrawals.
	* A hotwallet should have enough funds to handle typical withdrawal volumes but the more in this wallet means the more risk you are taking should the server holding the private keys be compromised.
* Cold Wallet
	* A wallet / computer/ paper wallet [(wikipedia)](https://en.bitcoin.it/wiki/Paper_wallet)  that is disconnected from the internet 
	* Many cryptos support multisignature addresses which require a certain number of distinct secret keys to move the coins (e.g. 3 out of 5 keys are needed to move the coins, referred to as 3of5 multisig).  This allows the total responsibility of the holdings to be delegated to multiple people minmizing the risk of internal employee theft
	* Cold wallet funds are 100% untouchable by a server breach (assuming one followed the proper security measures of)


##### There are many other methods of minimizing the impact of a server compromise and one should assume that they will always be able to cover the funds in the hotwallet out of pocket otherwise one would be running an illegal fractional reserve.  

##### Many companies have a dedicated hotwallet monitor in order to keep track of its balance and add funds to ensure withdrawals will always be processesd without delay.

##

### 3. Safety measures against attacks

###### This is a very detailed and complex field of discussion and it really depends on your implementation.  This topic could fill a book but here are same basic operation principles I advice:
* Use multisignature on the cold wallet funds 
* Minimize the amount in the hotwallet as much as possible without introducing delays  in withdrawals due to an empty hotwallet.  this is a game of balance and one must decide for themselves how much risk they are willing to take without severely impacting user experience
* Always keep all software updated and keep a watch on any new security advisories relating to the software you are using. See https://www.exploit-db.com/ to see how consistently new exploits come out for some of the most widely used software.  If you find out  a piece of software you are using has an exploit that would allow for coin theft, bite the bullet and take down your system until a secure form of it is created.  
* Segregate the servers that contain sensitive informationf from those that perform nonsensitive function (e.g. dont put your wallet on the same server that servers webpages.


#### Here are some links for further reading on the topic of cryptocurrency security

* https://hackernoon.com/a-guide-to-cryptocurrency-security-8681552820c1
* https://en.bitcoin.it/wiki/Cold_storage
* https://bitcoinexchangeguide.com/cryptocurrency-security-guide/
* https://www.ledger.fr/2016/08/08/how-to-properly-secure-cryptocurrencies-exchanges/
* https://www.ccn.com/bitcoin-wallet-security-best-practices/
