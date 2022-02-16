# full-stack-nft-marketplace

A full stack digital marketplace running on Ethereum, built with 
Polygon, Next.js, Tailwind, Solidity, Hardhat, Ethers.js, and IPFS


GUIDE IN RUNNING THIS PROJECT:

A. Gitpod
To deploy this project to Gitpod, follow these steps:

Click this link to deploy
https://gitpod.io/#github.com/johnchristotle/full-stack-nft-marketplace

Import the RPC address given to you by GitPod into your MetaMask wallet

The chain ID should be 1337. If you have a localhost rpc set up, you may need to overwrite it


B. Local setup
To run this project locally, follow these steps.

1. Clone the project locally, change into the directory, and install the dependencies:
git clone https://github.com/johnchristotle/full-stack-nft-marketplace/

cd full-stack-nft-marketplace

# install using NPM or Yarn
npm install

# or

yarn

2. Start the local Hardhat node

npx hardhat node

3. While the network is running, deploy the contracts to the local network in a separate terminal window

npx hardhat run scripts/deploy.js --network localhost

4. Start the app
npm run dev



CONFIGURATION:
To deploy to Polygon test or main networks, update the configurations located in hardhat.config.js to use a private key and, optionally, deploy to a private RPC like Infura.

require("@nomiclabs/hardhat-waffle");
const fs = require('fs');
const privateKey = fs.readFileSync(".secret").toString().trim() || "01234567890123456789";

// infuraId is optional if you are using Infura RPC
const infuraId = fs.readFileSync(".infuraid").toString().trim() || "";

module.exports = {
  defaultNetwork: "hardhat",
  networks: {
    hardhat: {
      chainId: 1337
    },
    mumbai: {
      // Infura
      // url: `https://polygon-mumbai.infura.io/v3/${infuraId}`
      url: "https://rpc-mumbai.matic.today",
      accounts: [privateKey]
    },
    matic: {
      // Infura
      // url: `https://polygon-mainnet.infura.io/v3/${infuraId}`,
      url: "https://rpc-mainnet.maticvigil.com",
      accounts: [privateKey]
    }
  },
  solidity: {
    version: "0.8.4",
    settings: {
      optimizer: {
        enabled: true,
        runs: 200
      }
    }
  }
};

NOTE: If using Infura, update .infuraid with your Infura project ID.
