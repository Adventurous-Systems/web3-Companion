## Syllabus

_Last reviewed: November 2026. Section names match the headings in the [companion](index.md)._

### Indicative content

* Setting up a development environment
  - Operating system (Linux, macOS, Windows with WSL)
  - Node.js, Git and Git clients
  - Editors and IDEs (Remix, VS Code)
  - RPC providers and node access

* Review of blockchain technologies
  - Blockchain context and the Byzantine Generals' Problem
  - Distributed ledgers and DLT platforms
  - Consensus mechanisms (proof of work, proof of stake)
  - Transactions and blocks
  - Mining and staking
  - Network peer discovery and messaging

* Blockchain basics
  - Cryptography, hash functions and Merkle trees
  - Public key and elliptic curve cryptography
  - Blockchain structure
  - Smart contracts
  - Blockchain nodes
  - Forks

* Ethereum primitives
  - History, white paper and yellow paper
  - Accounts (EOAs, contract accounts, EIP-7702 smart accounts)
  - Transactions, gas and fees
  - Blocks and the EVM
  - Execution and consensus clients

* Networks, testnets and explorers
  - Mainnet, Sepolia and Hoodi; layer 2 testnets
  - Local networks (Anvil, Hardhat network)
  - Etherscan, Blockscout and contract verification

* The Ethereum roadmap and network upgrades
  - The Merge, Dencun, Pectra, Fusaka and Glamsterdam
  - How upgrades are decided (EIPs, All Core Developers calls)

* Development frameworks
  - Foundry: setting up, `forge`, `cast`, `anvil`
  - Hardhat 3: setting up, Solidity and TypeScript tests
  - Ape Framework (for Pythonistas)
  - Scaffold-ETH 2

* Solidity fundamentals
  - Basic layout and structure of a smart contract
  - Data types and variables
  - Functions, modifiers and custom errors
  - Storage, memory and transient storage
  - Reading smart contracts
  - Smart contract Application Binary Interface (ABI)
  - Events and logs
  - Factory contracts and CREATE2

* Writing smart contracts
  - Basic smart contracts
  - Inter-contract execution
  - Inheritance
  - Libraries (OpenZeppelin, Solady)
  - Upgradeable contracts and proxies
  - Smart contract system design
  - Examples I: proof of existence, simple bank, supply chains
  - Examples II: voting, tokens, auctions

* Token standards
  - What is an EIP and an ERC?
  - ERC-20, ERC-721 and ERC-1155 walkthroughs
  - ERC-4626, ERC-2612 and signature standards (EIP-712, ERC-1271)
  - Account abstraction (ERC-4337, EIP-7702)

* Testing, debugging and security
  - Why test?
  - Unit, fuzz and invariant tests in Solidity (Foundry, Hardhat 3)
  - TypeScript tests (Hardhat 3, viem)
  - What a good test suite avoids: quality control
  - Common exploits: re-entrancy, tx.origin, denial of service, front running
  - Static analysis and fuzzing (Slither, Aderyn, Echidna, Medusa)
  - Security checklists (EthTrust Security Levels)
  - Gas optimisation

* Ethereum and the end user
  - Web3 introduction
  - viem, wagmi, ethers v6 and web3.py
  - Wallets and wallet connection (MetaMask, Safe, RainbowKit)
  - Integrating with React and Scaffold-ETH 2

Further afield:
* Layer 2 and scaling (rollups, blobs, L2BEAT)
* Storage (IPFS, Filecoin, Arweave), ENS, indexing (The Graph) and oracles (Chainlink)
* Attestations (EAS)
* Decentralised finance
* Decentralised autonomous organisations and token engineering
* AI agents and Ethereum (ERC-8004, x402)
* Blockchain in architecture, engineering and construction

### Suggested 12-week schedule

| Week | Focus | Companion sections | Hands-on |
| --- | --- | --- | --- |
| 1 | Environment and context | Setting up a development environment; Review of blockchain technologies | Install Node.js, Git, Foundry or Hardhat 3; deploy "Hello World" in Remix |
| 2 | Blockchain basics | Blockchain basics | Build a toy blockchain in Python or JavaScript; hash and Merkle tree exercises |
| 3 | Ethereum primitives | Ethereum primitives; Networks, testnets and explorers; The Ethereum roadmap | Fund a Sepolia account; read a transaction on Etherscan; use `cast` to query mainnet |
| 4 | Solidity I | Solidity fundamentals | Solidity by Example exercises; first Speedrun Ethereum challenge |
| 5 | Solidity II and testing | Writing smart contracts; Testing, debugging and security | Simple bank with unit and fuzz tests |
| 6 | Tokens | Token standards and EIPs | ERC-20 and ERC-721 with OpenZeppelin; deploy and verify on Sepolia |
| 7 | Front end | Ethereum and the end user | Scaffold-ETH 2 or viem/wagmi front end for your token |
| 8 | Security | Testing, debugging and security | Ethernaut levels; run Slither or Aderyn on your own code |
| 9 | Further afield and project proposal | Layer 2; Storage, naming, indexing and oracles; DAOs; AEC | Submit a one-page project proposal |
| 10 | Project build | Project Brief | Contracts and tests |
| 11 | Project build | Project Brief | Front end, testnet deployment, security self-review |
| 12 | Project showcase | Project Brief | Report, demo video and presentation |

### Learning outcomes

By following the companion, learners will be able to show evidence of:

1. Describing blockchain primitives and basics and giving examples of their use.
2. Preparing and demonstrating a development environment for Ethereum.
3. Composing basic smart contracts and their tests, and deploying them to a test network.
4. Producing an evaluation of common security issues in smart contracts.
5. Building, deploying and showcasing a decentralised application on Ethereum or an Ethereum layer 2.

- Indicative workload: minimum 10 hours per week, with at least 4 hours per week of hands-on practice.
- Recommended workload: 20 hours per week, with 10 hours per week devoted to hands-on practice.
