# NFT minting Project

This project is my solution from the exercise @buildspace.so about NFT minting to the Opensea with solidity hardhat which ramdom generate 3 words and random backgound colour.User can mint NFT not over 50 NFTs.

Before running this project, you need API key from Alchemy to be as node provider for deploy smart contract to rinkeby test network and API key from etherscan for verify your smart contract.

Try running some of the following tasks:

- For test function from smart contract with ether.js
```shell
npx hardhat run scripts/run.js 
```

- For upload file to the rinkeby test network
npx hardhat run scripts/deploy.js --network rinkeby
```
After deployed contract finished, you can visit [opensea](https://testnets.opensea.io) and find the collection of your smart contract address.