# Sample Hardhat Project

This project demonstrates a basic Hardhat use case. It comes with a sample contract, a test for that contract, and a script that deploys that contract.

Try running some of the following tasks:

```shell
npx hardhat help
npx hardhat test
REPORT_GAS=true npx hardhat test
npx hardhat node
npx hardhat run scripts/deploy.js
```

Most of the times setting .env often causes a lot of problems so developers just put them into
the main hardhat.config.js file. I wanted to have a method that was to always work
to making sure that API key as well as the private key were always hidden.

To sucessfully use dotenv.

1. npm init -y
2. npm i doteenv
3. in the folder where the API key and private key is required, at the top of the file type in: require("dotenv").config(); - name the file: test.js
3. type in the same file console.log("process.env.API_KEY") - this will allow you to test if dotenv even works!
4. create .env file
5. type in the .env file API_KEY=12345
6. in the command line type in: node test.js
7. the output should be: 12345 - if it is then you have configured it correctly. 

The best way to get it to work on hardhat.config.js is to:

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
require("@nomicfoundation/hardhat-toolbox");
require("dotenv").config();


const ALCHEMY_API_KEY = process.env.API_KEY;
const SEPOLIA_PRIVATE_KEY = process.env.PRIVATE_KEY;

/** @type import('hardhat/config').HardhatUserConfig */
module.exports = {
  solidity: "0.8.9",
  networks: {
    sepolia: {
      url: `https://eth-sepolia.g.alchemy.com/v2/${ALCHEMY_API_KEY}`,
      accounts: [SEPOLIA_PRIVATE_KEY]
    }
  }
};

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

in the .env file type in ALCHEMY_API_KEY=<alchemy_api_key> (with no quotation marks since there are no spaces in the API key)
also tpye in a line below PRIVATE_KEY=<private key> (with no quotation marks since there are no spaces in the private key)

This will always ensure that your API key and private keys are always hidden when you commit to GitHub. And will save you a lot of 
time.

Best!





