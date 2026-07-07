# ⛓️ Blockchain Smart Contracts

> Solidity smart contracts — ERC20, ERC721, DeFi protocols, deployed with Hardhat

[![Stars](https://img.shields.io/github/stars/arya123224/blockchain-smart-contracts?style=for-the-badge&color=F7931A)](https://github.com/arya123224/blockchain-smart-contracts)
![Solidity](https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white)
![Ethereum](https://img.shields.io/badge/Ethereum-3C3C3D?style=for-the-badge&logo=ethereum&logoColor=white)

## 📂 Contracts

### ERC-20 Token
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract HarshToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("HarshToken", "HKT") {
        _mint(msg.sender, initialSupply * 10 ** decimals());
    }
}
```

### ERC-721 NFT
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract HarshNFT is ERC721 {
    uint256 public tokenCounter;
    constructor() ERC721("HarshNFT", "HNFT") { tokenCounter = 0; }

    function mint(address to) public returns (uint256) {
        uint256 newId = tokenCounter;
        _safeMint(to, newId);
        tokenCounter++;
        return newId;
    }
}
```

### Simple DeFi Vault
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleVault {
    mapping(address => uint256) public balances;

    function deposit() external payable { balances[msg.sender] += msg.value; }

    function withdraw(uint256 amount) external {
        require(balances[msg.sender] >= amount, "Insufficient");
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }
}
```

## 🛠️ Tech Stack
- Solidity 0.8+
- Hardhat
- OpenZeppelin
- Web3.py / Ethers.js
- Ethereum Testnet (Sepolia)

## ⭐ Star this repo!
*By Harsh Kumar — github.com/arya123224*

<!-- Daily update: 2026-07-07 06:02 -->
