# GithubNFT
Smart contract written on Sui Move that creates a collection of NFT with limited allocation and Mint, Burn functions. Code created with things learned on the HackQuest course

# How to use it

Even though the smart contract is written on Sui Move we will need to use SUI CLI to deploy/test our smarat contract. Also the Mint and Burn functions are made true funcion calls.

# Build the package

```bash
sui move build
###############################################################
#You should get a message like this if succeeded
# UPDATING GIT DEPENDENCY https://github.com/MystenLabs/sui.git
# INCLUDING DEPENDENCY Sui
# INCLUDING DEPENDENCY MoveStdlib
# BUILDING github_nft
```

# Deploy the package 

```bash
sui client publish
```

It's no longer required to get the --gas-budget 
The output is long, but you will see something like:

- Transaction Digest: It is basically a thumbprint or hash of the tx just made, you can deep dive on this using sui explorer.

- Sender: Should be your Sui CLI active address. The one that deployed the smart contract
- Gas owner: Should be your Sui CLI active address. The one that deployed the smart contract

- Transaction effects: You will see the objects created, shared and mutated durint the tx. Remember!! in Sui everything is an object.

- Events: It includes the events happened on that block. Relateds eventID with PackageID. Also the parameters used on the Displey module.

- Object changes: Can see also the objects changed, created and mutated.
Balance changes: Will show your current balance on the active sui address.

# Mint your NFT
```bash
// Local contract function call, remember to change the addresses to your own
export PACKAGE="0x68b1e671f49925af079be1135b9dd58ddf39ad8ffb5b9c0575f1e593abd3e278"
export MODULE="github_nft"
export MINTRECORD="0xbb9efb2da320dc21eabeedd2b38ef8bd1b3028584d21d0d00bc1e3175a443dd9"
export RECIPIENT="0xe3b846b88e6640e8dd1fdcdd3c6dd25e2da63b7d59f91b5e5016a37fe894b9ca"
sui client call --package $PACKAGE --module $MODULE --function mint --args $MINTRECORD "Nubytek NFT 1" "https://i.ibb.co/SsDSqXn/Screenshot-2024-10-01-at-10-56-07-AM.png" $RECIPIENT
```



