# NFT minting Project (Solidity)

This project is my solution from the exercise in @buildspace.so about NFT minting to the Opensea with solidity hardhat which ramdom generate 3 words and random backgound colour.User can mint NFT not over 50 NFTs.

NFT is JSON format like

```json
{
    "name": "Thanasornsawan",
    "description": "An NFT from thanasornsawan",
    "image": "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHByZXNlcnZlQXNwZWN0UmF0aW89InhNaW5ZTWluIG1lZXQiIHZpZXdCb3g9IjAgMCAzNTAgMzUwIj4KICAgIDxzdHlsZT4uYmFzZSB7IGZpbGw6IHdoaXRlOyBmb250LWZhbWlseTogc2VyaWY7IGZvbnQtc2l6ZTogMTRweDsgfTwvc3R5bGU+CiAgICA8cmVjdCB3aWR0aD0iMTAwJSIgaGVpZ2h0PSIxMDAlIiBmaWxsPSJibGFjayIgLz4KICAgIDx0ZXh0IHg9IjUwJSIgeT0iNTAlIiBjbGFzcz0iYmFzZSIgZG9taW5hbnQtYmFzZWxpbmU9Im1pZGRsZSIgdGV4dC1hbmNob3I9Im1pZGRsZSI+VGhhbmFzb3Juc2F3YW48L3RleHQ+Cjwvc3ZnPg=="
}
```
So, when you want the NFT to show on Opensea, you have to host this JSON file somewhere but it may not a good idea to rely on 3rd party.The best way is encode all JSON file into base64 format.That's why this project use base64 library.

Before running this project, you need to install dotenv and hardhat-etherscan plugin.
```shell
npm install dotenv
npm install --save-dev @nomiclabs/hardhat-etherscan
```
In order to use some plugins, API keys or custom network with secret config we need a .env file. You can check hardhat.config.js for more details.
This project use API key from Alchemy to be as node provider for deploy smart contract to rinkeby test network, API key from etherscan for verify your smart contract and private key of your metamask wallet on rinkeby test network and setup all credentials in your own .env file.

```javascript
require("@nomiclabs/hardhat-waffle");
require("dotenv").config();
require("@nomiclabs/hardhat-etherscan");

/**
 * @type import('hardhat/config').HardhatUserConfig
 */
module.exports = {
  solidity: "0.8.4",
  networks: {
    rinkeby: {
      url: process.env.DEVELOP_ALCHEMY_KEY,
      accounts: [process.env.PRIVATE_KEY]
    },
  },
  etherscan: {
    // Your API key for Etherscan
    // Obtain one at https://etherscan.io/
    apiKey: process.env.ETHERSCAN_KEY
  }
};
```

Try running some of the following tasks:

- For test function from smart contract with ether.js
```shell
npx hardhat run scripts/run.js 
```

- For upload file to the rinkeby test network
```shell
npx hardhat run scripts/deploy.js --network rinkeby
```
After deployed contract finished, you can visit [opensea test network](https://testnets.opensea.io) and find the collection of your smart contract address.

- If have any problem during run hardhat command,try this one.
```shell
npx hardhat clean
```
- For auto verify your smart contract on etherscan from command
```shell
npx hardhat verify <smart contract address> --network rinkeby
```
