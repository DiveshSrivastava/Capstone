# Udacity Blockchain Capstone
This is a Udacity Blockchain Capsotne project to build a decentralized housing product with following tasks
1) Minting our own tokens to represent our title to the real estate properties. 
2) Before minting a token, we need to verify that we own the property. 
3) We will use zk-SNARKs to create a verification system which can prove we have title to the property without revealing that specific information on the property. 
4) Once the token has been verified we will place it on a blockchain market place (OpenSea) for others to purchase. The detail steps of the project is as follows:

        a) building of the ERC 721 tokens for the real estate homes
        b) compiling and integrating zokrates into the tokens that is just built

# Project Prerequisites 
* Truffle v5.1.0 (core: 5.1.0)
* Solidity v0.5.12 (solc-js)
* Node v11.12.0
* Web3.js v1.2.2

# Zokrates ( Generate Zero Knowledge Proof )
* Step 1: Run ZoKrates in Docker
        > docker run -v /path/to/zokrates/zokrates/code:/home/zokrates/code -ti zokrates/zokrates /bin/bash
        > cd code/square
* Step 2: Compile the program written in ZoKrates DSL
        > zokrates compile -i square.code
* Step 3: Generate the Trusted Setup
        > zokrates setup
* Step 4: Compute Witness
        > zokrates compute-witness -a 3 9
* Step 5: Generate Proof
        > zokrates generate-proof
* Step 6: Export Verifier
        > zokrates export-verifier

# Build Project 
Go to root project folder after cloning into local drives and run following commands 
    > cd eth-contracts
    > npm install
    > npm install truffle-hdwallet-provider
    > truffle compile

# Test Project
    > Truffle test test/TestERC721Mintable.js
    > Truffle test test/TestSolnSquareVerifier.js

# Deploye Project To Rinkeby
    > Update mnemonic and infura url in truffle-config.js
    > Truffle migrate --network rinkeby

# Rinkeby Deployed Project Details
 1)  Deploying 'Verifier'
   --------------------
    transaction hash:    0x6d0ac8e23acbbf86b802ead756041183031752c5e3af4fdca2ca6a66504affac
    Blocks: 1            Seconds: 9
    contract address:    0xf2CfFDA7a1377f90b8ca328549229c23690e3224
 2) Deploying 'SolnSquareVerifier'
   ------------------------------
    transaction hash:    0x90aadf4668c825aa2b5e34b7b783cd9a4208ffee81038159c5291b3dc72425e8
    Blocks: 0            Seconds: 5
    contract address:    0xA88d84aeb054bd80043F218108E83424537b221E

#  Contract ABI 
* The contract abi can be obtained in following way :
1) If deployed using truffle :
        Build folder will contain json of contract with abi information
2) If deployed using Remix :
        ABI option is available after deployment for the contract
        
* Current project ABI for SolnSquareVerifier is taken from build folder:
[
    {
      "inputs": [
        {
          "internalType": "address",
          "name": "verifierAddress",
          "type": "address"
        },
        {
          "internalType": "string",
          "name": "name",
          "type": "string"
        },
        {
          "internalType": "string",
          "name": "symbol",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "constructor"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "internalType": "address",
          "name": "owner",
          "type": "address"
        },
        {
          "indexed": true,
          "internalType": "address",
          "name": "approved",
          "type": "address"
        },
        {
          "indexed": true,
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "Approval",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "internalType": "address",
          "name": "owner",
          "type": "address"
        },
        {
          "indexed": true,
          "internalType": "address",
          "name": "operator",
          "type": "address"
        },
        {
          "indexed": false,
          "internalType": "bool",
          "name": "approved",
          "type": "bool"
        }
      ],
      "name": "ApprovalForAll",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [],
      "name": "OwnerShipIsTransfered",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "internalType": "address",
          "name": "caller",
          "type": "address"
        }
      ],
      "name": "Paused",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "internalType": "uint256",
          "name": "solutionIndex",
          "type": "uint256"
        },
        {
          "indexed": true,
          "internalType": "address",
          "name": "solutionAddress",
          "type": "address"
        }
      ],
      "name": "SolutionAdded",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "internalType": "address",
          "name": "from",
          "type": "address"
        },
        {
          "indexed": true,
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "indexed": true,
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "Transfer",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "internalType": "address",
          "name": "caller",
          "type": "address"
        }
      ],
      "name": "Unpaused",
      "type": "event"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "BaseTokenURI",
      "outputs": [
        {
          "internalType": "string",
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "bytes32",
          "name": "_myid",
          "type": "bytes32"
        },
        {
          "internalType": "string",
          "name": "_result",
          "type": "string"
        }
      ],
      "name": "__callback",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "bytes32",
          "name": "_myid",
          "type": "bytes32"
        },
        {
          "internalType": "string",
          "name": "_result",
          "type": "string"
        },
        {
          "internalType": "bytes",
          "name": "_proof",
          "type": "bytes"
        }
      ],
      "name": "__callback",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "approve",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "address",
          "name": "owner",
          "type": "address"
        }
      ],
      "name": "balanceOf",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "currentOwner",
      "outputs": [
        {
          "internalType": "address",
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "getApproved",
      "outputs": [
        {
          "internalType": "address",
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "address",
          "name": "owner",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "operator",
          "type": "address"
        }
      ],
      "name": "isApprovedForAll",
      "outputs": [
        {
          "internalType": "bool",
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "mint",
      "outputs": [
        {
          "internalType": "bool",
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "name",
      "outputs": [
        {
          "internalType": "string",
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "numberOfSolutions",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "ownerOf",
      "outputs": [
        {
          "internalType": "address",
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "from",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "safeTransferFrom",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "from",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        },
        {
          "internalType": "bytes",
          "name": "_data",
          "type": "bytes"
        }
      ],
      "name": "safeTransferFrom",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "internalType": "bool",
          "name": "approved",
          "type": "bool"
        }
      ],
      "name": "setApprovalForAll",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [],
      "name": "setContact",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "bytes32",
          "name": "",
          "type": "bytes32"
        }
      ],
      "name": "solutions",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "solutionIndex",
          "type": "uint256"
        },
        {
          "internalType": "address",
          "name": "solutionAddress",
          "type": "address"
        },
        {
          "internalType": "bool",
          "name": "solutionExists",
          "type": "bool"
        },
        {
          "internalType": "bool",
          "name": "minted",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "bytes4",
          "name": "interfaceId",
          "type": "bytes4"
        }
      ],
      "name": "supportsInterface",
      "outputs": [
        {
          "internalType": "bool",
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "symbol",
      "outputs": [
        {
          "internalType": "string",
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "index",
          "type": "uint256"
        }
      ],
      "name": "tokenByIndex",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "address",
          "name": "owner",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "index",
          "type": "uint256"
        }
      ],
      "name": "tokenOfOwnerByIndex",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "tokenURI",
      "outputs": [
        {
          "internalType": "string",
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "totalSupply",
      "outputs": [
        {
          "internalType": "uint256",
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "from",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "transferFrom",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "address",
          "name": "newOwner",
          "type": "address"
        }
      ],
      "name": "transferOwnership",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "uint256[2]",
          "name": "a",
          "type": "uint256[2]"
        },
        {
          "internalType": "uint256[2][2]",
          "name": "b",
          "type": "uint256[2][2]"
        },
        {
          "internalType": "uint256[2]",
          "name": "c",
          "type": "uint256[2]"
        },
        {
          "internalType": "uint256[2]",
          "name": "input",
          "type": "uint256[2]"
        }
      ],
      "name": "addSolution",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "internalType": "uint256",
          "name": "a",
          "type": "uint256"
        },
        {
          "internalType": "uint256",
          "name": "b",
          "type": "uint256"
        },
        {
          "internalType": "address",
          "name": "to",
          "type": "address"
        }
      ],
      "name": "mintNewNFT",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    }
  ]

# Mint Tokens
1) Use MyEtherWallet to mint 10 tokens
2) Use the ABI and the deployed SolnSquareVerifier's contract address
3) List the tokens by going to: https://rinkeby.opensea.io/get-listed/step-two

# Opensea Storefront
* OpenSea Marketplace Storefront link's https://testnets.opensea.io/0xcad33ab2d17f270efa7df727e0ef6343cc938d19

* Marketplace Seller: 0xCaD33Ab2D17f270EFA7Df727e0Ef6343cC938d19
* Tokens with buyer:
        1) https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/6
        2) https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/7
        3) https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/8
        4) https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/9
        5) https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/10

* Marketplace Buyer: 0xe3DDfD42dA9010b13BFC063d53D28ba43E0b9d3b
* Tokens with Seller:
        1)  https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/5
        2)  https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/1
        3)  https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/2
        4  https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/3
        5)  https://testnets.opensea.io/assets/0xa88d84aeb054bd80043f218108e83424537b221e/4

# Project Tasks
* Clone the project repository -                                                                                                  **Completed**
* Explore the code base.                                                                                                          **Completed**
* Fill out ERC721 Mintable Contract in ERC721Mintable.sol                                                                         **Completed**
* Fill out ERC721 Mintable Contract in ERC721Mintable.sol                                                                         **Completed**
* Write test cases TestERC721Mintable.js                                                                                          **Completed**
* Compile and pass test cases in TestERC721Mintable.js                                                                            **Completed**
* Implement Zokrates                                                                                                              **Completed**
* Write a test script to verify the solidity contract generated by Zokrates executed successfully - TestSquareVerifier.js         **Completed**
* Write test contract for ZK and ERC721 integration - SolnSquareVerifier.sol	                                                  **Completed**
* Compile and pass with TestSolnSquareVerifier.js                                                                                 **Completed**
* Deploy latest contracts generated by Zokrates (a.k.a verifier.sol)                                                              **Completed**
* Deploy SolnSquareVerifier contract to Rinkeby network                                                                           **Completed**
* Mint 10 tokens	                                                                                                          **Completed**
* Generate OpenSea marketplace                                                                                                    **Completed**
* Test and Verify OpenSea with your SolnSquareVerifier tokens	                                                                  **Completed**
* Complete required documentation and submit	                                                                                  **Completed**

# ********* Note : All screenshots of the above tasks are present in Snips.df file *********

# Project Resources
* [Remix - Solidity IDE](https://remix.ethereum.org/)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Truffle Framework](https://truffleframework.com/)
* [Ganache - One Click Blockchain](https://truffleframework.com/ganache)
* [Open Zeppelin ](https://openzeppelin.org/)
* [Interactive zero knowledge 3-colorability demonstration](http://web.mit.edu/~ezyang/Public/graph/svg.html)
* [Docker](https://docs.docker.com/install/)
* [ZoKrates](https://github.com/Zokrates/ZoKrates)
