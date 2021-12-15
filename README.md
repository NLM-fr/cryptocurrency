# Cryptocurrency
Creating my own token on the Solana Blockchain

I'll explain here the process of creating my own token named SPACE Coin

## Table of contents

* [Server](#server)
* [Deployment](#deployment)
* [Author Information](#author-information)

## Server Setup

First of all we need to setup our linux machine

I used a VPS I have from OVH, I have setup Debian | Docker since I use this server for other projects too.
We need to connect to our VPS I used the SSH connection with Visual Studio

## Wallet creation
We are going to create a Solana wallet on the machine we use this command to install Solana tools:

```
sh -c "$(curl -sSfL https://release.solana.com/v1.8.5/install)"
```

Then we need to exit from our terminal 'Exit' and log back in so our PATH variable are uptaded on our SHELL

We are now going to create the cryptocurrency wallet that will hold Solana
```
solana-keygen new
```
Press Enter if you don't want to enter a Passphrase

- The keypair is saved to the /root/.config/solana/id.json this is where the private address is.

- The public key is the key needed to send and receive token.

- The seedphrase and passphrase needs to be saved somewhere in case we need to recover the wallet so it needs to be kept safely somewhere 





```
solana balance #check balance on the wallet	
sudo apt install libudev-dev
sudo apt install libssl-dev pkg-config
sudo apt install build-essential -y
cargo install spl-token-cli
spl-token create-token #creating the token we get a token ID (this costs some sol in my case 0.0014716 SOL)
spl-token create-account tokenid #creating an account that will hold all the token (Creation cost 0.00204428 SOL) 
spl-token mint tokenid amount tokenaccountid #we are minting the amount of token we want for our token for the tokenid to the address of the token(cost 0.000005 SOL)
spl-token accounts										#we can check the amount of token minted
```

Creation of a phantom wallet to send token
spl-token transfer --fund-recipient --allow-unfunded-recipient tokenid amount recipientaddress 	#we are transfering funds to an address from our token address (cost 0.00204428 SOL)
--fund-recipient					#funding the wallet creation for our token
--allow-unfunded-recipient				#allowing the empty wallet to receive token

Name and Logo for our token:

We need to upload our logo less then 200kb to a github repository and get the address of the download link https://raw.githubusercontent.com/NLM-fr/cryptocurrency/main/logo.png
Fork the repository of Solana Labs https://github.com/solana-labs/token-list (press . when on the page of the forked repository to open visual studio on github)

Then in the asset repository we are going to add our token address
Add a repository with the tokenid as name and upload the logo in there.

Then we need to add our token to the solana.tokenlist.json in the /src/tockens repository
Add this to the end of the json
{
      "chainId": 101,
      "address": "tokenid",
      "symbol": "SPACE",
      "name": "Space Coin",
      "decimals": 0,
      "logoURI": "https://raw.githubusercontent.com/NLM-fr/cryptocurrency/main/logo.png",
      "tags": [
        "social-token"
      ]
    }
We just need to commit the changes with a message "Adding Space Coin token"

We are going to add a pull request to the Solana Labs github repository 
Go to Pull requests and press New pull request
Select compare accross forks and change the head repostory to the one we forked and create pull request 
Then wait for everything to upload and you should be good you can go on https://solscan.io/ to check your new tocken 



Space SPACE
Token ID/address	9WNFtVYj1dUiF5nUM7zBz644hPbKgEDuxk6iHAohQfii
Token account ID 	CDNyMQZJ6dy7uec43H7MjDfSmLgziq1y5QAqHvoFT4MF
Token Logo		https://raw.githubusercontent.com/NLM-fr/cryptocurrency/main/logo.png
