## Welcome to the ArchiDAO Ethereum Developer Companion

_Last reviewed: November 2026. See the [changelog](CHANGELOG.md) for what changed._

Early versions of this guide were developed as a companion to the AthensLabs Blockchain Developer Bootcamp 2022. Since then we have kept updating it for the use of blockchain in Architecture, Engineering and Construction (AEC), including moving the tutorials onto newer development frameworks. The fundamentals of blockchains have not changed much; the tooling and the network around them have changed a lot. The guide focuses on the Ethereum ecosystem, which remains the most active smart contract and decentralised application ecosystem, and is organised as a series of structured links and notes that give you the basic knowledge to build decentralised applications.

- The companion supports active learning: you are expected to design, code, test and deploy an actual decentralised application (see the [Project Brief](#project-brief)).
- A suggested 12-week schedule is in the [syllabus](syllabus.md).

### Contents

- [What changed since the last edition](#what-changed-since-the-last-edition)
- [Learning outcomes](#learning-outcomes)
- [Onboarding and full learning paths](#onboarding-and-full-learning-paths)
- [Setting up a development environment](#setting-up-a-development-environment)
- [Review of blockchain technologies](#review-of-blockchain-technologies)
- [Blockchain basics](#blockchain-basics)
- [Ethereum primitives](#ethereum-primitives)
- [Networks, testnets and explorers](#networks-testnets-and-explorers)
- [The Ethereum roadmap and network upgrades](#the-ethereum-roadmap-and-network-upgrades)
- [Development frameworks](#development-frameworks)
- [Solidity fundamentals](#solidity-fundamentals)
- [Writing smart contracts](#writing-smart-contracts)
- [Token standards and EIPs](#token-standards-and-eips)
- [Testing, debugging and security](#testing-debugging-and-security)
- [Ethereum and the end user](#ethereum-and-the-end-user)
- [Layer 2 and scaling](#layer-2-and-scaling)
- [Storage, naming, indexing and oracles](#storage-naming-indexing-and-oracles)
- [Decentralised finance](#decentralised-finance)
- [DAOs and token engineering](#daos-and-token-engineering)
- [AI agents and Ethereum](#ai-agents-and-ethereum)
- [Blockchain in architecture, engineering and construction](#blockchain-in-architecture-engineering-and-construction)
- [Videos and developers to follow](#videos-and-developers-to-follow)
- [Policy and regulation](#policy-and-regulation)
- [History](#history)
- [Community, news and help](#community-news-and-help)
- [Deprecated and archived](#deprecated-and-archived)
- [Project Brief](#project-brief)

## What changed since the last edition

If you are coming back to this guide, or following an older tutorial, these are the changes that matter most (as of November 2026):

- **Network upgrades.** Dencun (March 2024) added blob transactions ([EIP-4844](https://eips.ethereum.org/EIPS/eip-4844)) that made rollups far cheaper. Pectra (May 2025) let ordinary accounts act as smart accounts ([EIP-7702](https://eips.ethereum.org/EIPS/eip-7702)) and raised the validator balance cap. Fusaka (3 December 2025) shipped PeerDAS and "blob parameter only" forks that raise blob capacity without a full upgrade. The block gas limit rose to 60 million in late 2025.
- **Next upgrade.** Glamsterdam (enshrined proposer-builder separation, block-level access lists and gas repricing) activated on Sepolia on 6 October 2026. Its Hoodi fork was postponed while developers study how the new gas pricing affects deployed contracts, and no mainnet date is set. Check [ethereum.org](https://ethereum.org/roadmap/glamsterdam/) before relying on gas costs.
- **Testnets.** Goerli and Holešky are gone. Use **Sepolia** for applications and **Hoodi** for validator and staking tests ([announcement](https://blog.ethereum.org/2025/09/01/holesky-shutdown-announcement)).
- **Frameworks.** Truffle and Ganache were archived in December 2023. Brownie is no longer maintained (use Ape for Python). **Foundry 1.x** and **Hardhat 3** (stable, with Solidity tests) are the two main choices; Hardhat 2 reaches end of life by June 2027 at the latest.
- **Libraries.** web3.js was archived in March 2025. Use **viem** (with **wagmi** in React) or **ethers v6**.
- **Language and libraries.** Solidity is on the 0.8.x line (0.8.37 at the time of writing) and its repository has moved to the Argot Collective. OpenZeppelin Contracts is on 5.x; ERC-777 was removed in 5.0.
- **Naming.** "Ethereum 2.0" and "Eth2" are retired terms. Ethereum now has an *execution layer* and a *consensus layer*, and "sharding" has become data availability sampling for rollups.

## Learning outcomes

By following the companion, learners will be able to **show evidence** of:

1. Describing blockchain primitives and basics and giving examples of their use.
2. Preparing and demonstrating a development environment for Ethereum.
3. Composing basic smart contracts and their tests, and deploying them to a test network.
4. Producing an evaluation of common security issues in smart contracts.
5. Building, deploying and showcasing a decentralised application on Ethereum or an Ethereum layer 2.

- Indicative workload: minimum 10 hours per week, with at least 4 hours per week of hands-on practice, for 12 weeks.
- Recommended workload: 20 hours per week, with 10 hours per week devoted to hands-on practice, for 12 weeks.

## Onboarding and full learning paths

Pick one of these as your spine and use the rest of the companion as reference.

- [Speedrun Ethereum (BuidlGuidl)](https://speedrunethereum.com/) - free, hands-on challenges built on Scaffold-ETH 2; each challenge ships a working dapp.
- [Cyfrin Updraft](https://updraft.cyfrin.io/courses) - free courses from blockchain basics through Solidity, Foundry, security and formal verification.
- [Alchemy University](https://university.alchemy.com/) - free Ethereum and Solidity courses.
- [Ethereum developer docs - ethereum.org](https://ethereum.org/developers/docs/) - the canonical reference for concepts.
- [Ethereum developer tutorials - ethereum.org](https://ethereum.org/developers/tutorials/)
- [Mastering Ethereum, 2nd edition (O'Reilly, 2025)](https://www.oreilly.com/library/view/mastering-ethereum-2nd/9781098168414/) - updated for proof of stake, rollups and zero-knowledge proofs; the [source is on GitHub](https://github.com/ethereumbook/ethereumbook).
- [Solidity by Example](https://solidity-by-example.org/)

## Setting up a development environment

You need a Unix-like shell, Git, Node.js and an editor. Linux and macOS work natively; on Windows use WSL.

- Linux distributions
  - [Ubuntu 26.04 LTS or 24.04 LTS](https://ubuntu.com/download/desktop)
  - [Fedora Workstation](https://fedoraproject.org/workstation/)
  - [Linux Mint](https://linuxmint.com/)
  - [MX Linux](https://mxlinux.org/)
  - [Puppy Linux - good for old machines](https://puppylinux-woof-ce.github.io/)
  - [openSUSE](https://www.opensuse.org/)
  - [DistroWatch - compare distributions](https://distrowatch.com/)
- Windows
  - [Install the Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install)
- macOS
  - [macOS](https://www.apple.com/macos/) - the current release is macOS 27 "Golden Gate" (September 2026), which runs on Apple silicon Macs only. Install the Xcode command line tools and [Homebrew](https://brew.sh/).
- Runtimes
  - [Node.js](https://nodejs.org/) - use an even-numbered LTS release; Hardhat 3 needs Node.js 22.10 or later.
  - [Rust](https://www.rust-lang.org/tools/install) - optional, for building Foundry or Reth from source.
  - [Python](https://www.python.org/downloads/) - for Ape and web3.py.
- Editors and IDEs (integrated development environments)
  - [Remix IDE](https://remix.ethereum.org) - browser IDE, the quickest way to start.
  - [Remix Desktop](https://remix-ide.readthedocs.io/en/latest/desktop.html) - the current desktop version (the old `remix-desktop` repository is archived).
  - [Visual Studio Code](https://code.visualstudio.com/) with the [Solidity extension by Nomic Foundation](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity)
  - [VS Code Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) - for pair programming.
  - [JetBrains IDEs](https://www.jetbrains.com/idea/)
  - [Pulsar - the community successor to Atom](https://pulsar-edit.dev/)
- Git clients
  - [git](https://git-scm.com/)
  - [GitHub Desktop - best for macOS and Windows](https://github.com/apps/desktop)
  - [Oh My Git - learning Git as a game](https://ohmygit.org/)
- Node access (RPC providers) - you do not need to run your own node to build apps.
  - [Nodes as a service - ethereum.org](https://ethereum.org/developers/docs/nodes-and-clients/nodes-as-a-service/)
  - [Alchemy](https://www.alchemy.com/), [Infura](https://www.infura.io/), [QuickNode](https://www.quicknode.com/)
  - [Chainlist - public RPC endpoints and chain IDs](https://chainlist.org/)
- Local development environment
  - [Set up your local development environment - ethereum.org](https://ethereum.org/developers/local-environment/)

## Review of blockchain technologies

- Blockchain context
  - [The Byzantine Generals' Problem, by L. Lamport, R. Shostak and M. Pease (1982)](https://lamport.azurewebsites.net/pubs/byz.pdf)
  - [Byzantine Generals' problem](https://medium.com/coinmonks/a-note-from-anthony-if-you-havent-already-please-read-the-article-gaining-clarity-on-key-787989107969)
  - [How Satoshi Nakamoto solved the Byzantine Generals' Problem](https://news.bitcoin.com/triple-entry-bookkeeping-how-satoshi-nakamoto-solved-the-byzantine-generals-problem/)
  - [The Bitcoin white paper, annotated](https://fermatslibrary.com/s/bitcoin)
  - [How does a blockchain work? - video](https://www.youtube.com/watch?v=SSo_EIwHSd4)
  - [A visual blockchain demo - video](https://www.youtube.com/watch?v=_160oMzblY8)
- Distributed ledgers
  - [A review of distributed ledger technologies, by N. El Ioini and C. Pahl](https://www.researchgate.net/profile/Claus-Pahl/publication/328475892_A_Review_of_Distributed_Ledger_Technologies/links/5bd0085ba6fdcc204a036252/A-Review-of-Distributed-Ledger-Technologies.pdf)
  - [Distributed Ledger Technology: Beyond Blockchain - UK Government Office for Science (2016)](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/492972/gs-16-1-distributed-ledger-technology.pdf)
  - [World Bank on DLTs](https://www.worldbank.org/en/topic/financialsector/brief/blockchain-dlt)
- Consensus mechanisms
  - [Consensus mechanisms - ethereum.org](https://ethereum.org/developers/docs/consensus-mechanisms/)
  - [Proof of stake - ethereum.org](https://ethereum.org/developers/docs/consensus-mechanisms/pos/)
  - [Proof of work - ethereum.org (historical for Ethereum since the Merge)](https://ethereum.org/developers/docs/consensus-mechanisms/pow/)
  - [Proof of stake vs proof of work](https://decrypt.co/resources/proof-of-work-vs-proof-of-stake)
  - [Understanding distributed consensus](https://medium.com/s/story/lets-take-a-crack-at-understanding-distributed-consensus-dad23d0dc95)
  - [Review of blockchain consensus mechanisms](https://medium.com/wavesprotocol/review-of-blockchain-consensus-mechanisms-f575afae38f2)
- Transactions and blocks
  - [Transactions - ethereum.org](https://ethereum.org/developers/docs/transactions/)
  - [Blocks - ethereum.org](https://ethereum.org/developers/docs/blocks/)
- Mining and staking
  - Ethereum stopped mining at the Merge (September 2022). Mining still matters for understanding Bitcoin and Ethereum's history.
  - [Ethash - ethereum.org](https://ethereum.org/developers/docs/consensus-mechanisms/pow/mining/mining-algorithms/ethash/)
  - [The Merge - ethereum.org](https://ethereum.org/roadmap/merge/)
  - [Staking - ethereum.org](https://ethereum.org/staking/)
  - [Staking Launchpad](https://launchpad.ethereum.org/)
- Network peer discovery and messaging
  - [Networking layer - ethereum.org](https://ethereum.org/developers/docs/networking-layer/)
  - [Analysing the underlying peer-to-peer network of the Ethereum blockchain, Wang et al.](https://arxiv.org/pdf/2010.01373.pdf)
- Public and private blockchains
  - [On public and private blockchains - V. Buterin (2015)](https://blog.ethereum.org/2015/08/07/on-public-and-private-blockchains/)
- Other distributed ledger platforms
  - [Hyperledger Fabric (LF Decentralized Trust, formerly Hyperledger Foundation)](https://www.lfdecentralizedtrust.org/projects/fabric)
  - [Corda](https://github.com/corda/corda)
  - [IOTA](https://www.iota.org/)
  - [Blockchain vs. Tangle vs. Hashgraph - a high-level overview and comparison](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3144241)

## Blockchain basics

- Cryptography
  - [Cryptography - Wikipedia](https://en.wikipedia.org/wiki/Cryptography)
  - [Schneier on cryptography](https://www.schneier.com/blog/archives/2016/03/cryptography_is.html)
  - [Practical Cryptography for Developers (free online book)](https://cryptobook.nakov.com/cryptography-overview)
  - [Lecture series on cryptography by Christof Paar](https://www.youtube.com/watch?v=2aHkqB2-46k&list=UU1usFRN4LCMcfIV7UjHNuQg&index=25)
- Cryptographic hash functions
  - [Secure hash algorithms](https://brilliant.org/wiki/secure-hashing-algorithms/)
  - [SHA-2 - Wikipedia](https://en.wikipedia.org/wiki/SHA-2)
  - [SHA-3 - Wikipedia](https://en.wikipedia.org/wiki/SHA-3)
  - [FIPS 180-4: Secure Hash Standard (SHA-1 and SHA-2)](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
  - [FIPS 202: SHA-3 and Keccak](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.202.pdf) - note that Ethereum's `keccak256` is the original Keccak, not the final NIST SHA-3.
  - [eth-hash (keccak256 in Python)](https://github.com/ethereum/eth-hash)
  - [Lecture by Christof Paar on hash functions](https://www.youtube.com/watch?v=JWskjzgiIa4)
- Using cryptographic hash functions
  - [Cryptographic hashing on Hackernoon](https://hackernoon.com/cryptographic-hashing-c25da23609c3)
  - [Hashing functions in blockchain](https://hackernoon.com/learn-the-blockchain-basics-part-3-hashing-functions-vt1435ow)
- Public key cryptography
  - [Symmetric and asymmetric public key cryptography](https://hackernoon.com/how-does-symmetric-and-asymmetric-public-key-cryptography-work-i6dy37pl)
  - [Public key cryptography: RSA keys](https://hackernoon.com/public-key-cryptography-rsa-keys-izda3ylv)
- Elliptic curve cryptography
  - [Practical elliptic curve cryptography](https://cryptobook.nakov.com/asymmetric-key-ciphers/elliptic-curve-cryptography-ecc)
  - [A (relatively easy to understand) primer on elliptic curve cryptography - Cloudflare](https://blog.cloudflare.com/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/)
  - [Mastering Bitcoin: elliptic curve cryptography explained](https://github.com/bitcoinbook/bitcoinbook/blob/develop/ch04_keys.adoc)
- Merkle trees
  - [What is a Merkle tree? - Decentralized Thoughts](https://decentralizedthoughts.github.io/2020-12-22-what-is-a-merkle-tree/)
  - [Merkle tree introduction](https://hackernoon.com/merkle-tree-introduction-4c44250e2da7)
  - [Merkle tree demo](https://prathamudeshmukh.github.io/merkle-tree-demo/)
  - [Merkle trees in Solidity](https://soliditydeveloper.com/merkle-tree)
  - [Merkle Patricia trie - ethereum.org](https://ethereum.org/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)
  - [Merkle proofs in Solidity - OpenZeppelin MerkleProof](https://docs.openzeppelin.com/contracts/5.x/api/utils#MerkleProof)
- Blockchain structure
  - [A survey on security and privacy issues of blockchain technology - intro to basic structure](https://www.researchgate.net/publication/325173502_A_survey_on_security_and_privacy_issues_of_blockchain_technology)
- Building a blockchain
  - [Learn blockchains by building one](https://hackernoon.com/learn-blockchains-by-building-one-117428612f46)
  - [How to build a blockchain in Python](https://www.activestate.com/blog/how-to-build-a-blockchain-in-python/)
  - [Build a blockchain in less than 60 lines of code](https://medium.com/coinmonks/python-tutorial-build-a-blockchain-713c706f6531)
  - [Blockchain basics - Solidity docs](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#blockchain-basics)
- Smart contracts
  - [Formalizing and Securing Relationships on Public Networks - N. Szabo (1997), the first description of smart contracts](https://firstmonday.org/ojs/index.php/fm/article/view/548)
  - [Smart contracts - Wikipedia](https://en.wikipedia.org/wiki/Smart_contract)
  - [Smart contracts - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/)
- Blockchain nodes
  - [Nodes and clients - ethereum.org](https://ethereum.org/developers/docs/nodes-and-clients/)
- Blockchain forks
  - [A history of Bitcoin hard forks](https://www.investopedia.com/tech/history-bitcoin-hard-forks/)
  - [An overview of forks and coordination in blockchain development](https://www.researchgate.net/publication/349492184_An_Overview_of_Forks_and_Coordination_in_Blockchain_Development)

## Ethereum primitives

- [Ethereum "pre-history"](https://vitalik.eth.limo/general/2017/09/14/prehistory.html) - Vitalik Buterin's blog post. Interesting to read as Buterin goes through the thought process of creating a fee-based ledger that is Turing complete, i.e. a state machine. Note the simplicity of the programmatic loop he uses to validate the concept.
- [Ethereum white paper](https://ethereum.org/whitepaper/)
- [Ethereum yellow paper, Dr Gavin Wood](https://ethereum.github.io/yellowpaper/paper.pdf) - the formal specification is now maintained as the [execution specs](https://github.com/ethereum/execution-specs) and [consensus specs](https://github.com/ethereum/consensus-specs).
- [Ethereum developer docs](https://ethereum.org/developers/docs/)
- [Web2 vs Web3](https://ethereum.org/developers/docs/web2-vs-web3/)
- Accounts
  - [Accounts - ethereum.org](https://ethereum.org/developers/docs/accounts/)
  - Externally owned accounts (EOAs) are controlled by a private key; contract accounts are controlled by code.
  - Since Pectra, an EOA can delegate to contract code ([EIP-7702](https://eips.ethereum.org/EIPS/eip-7702)), so the line between the two has blurred. See [account abstraction](https://ethereum.org/roadmap/account-abstraction/).
  - [How smart contract deployment works](https://programtheblockchain.com/posts/2018/01/09/how-smart-contract-deployment-works/)
- Transactions, gas and fees
  - [Transactions - ethereum.org](https://ethereum.org/developers/docs/transactions/) - note the typed transactions: type 2 (EIP-1559 fees), type 3 (blobs) and type 4 (EIP-7702 set-code).
  - [Gas and fees - ethereum.org](https://ethereum.org/developers/docs/gas/)
- Blocks
  - [Blocks - ethereum.org](https://ethereum.org/developers/docs/blocks/)
- Ethereum Virtual Machine
  - [Ethereum Virtual Machine - ethereum.org](https://ethereum.org/developers/docs/evm/)
  - [evm.codes - interactive opcode reference and playground](https://www.evm.codes/)
  - [Ethereum EVM illustrated (2018)](https://takenobu-hs.github.io/downloads/ethereum_evm_illustrated.pdf)
- Generating Ethereum addresses
  - [How to generate Ethereum addresses](https://hackernoon.com/how-to-generate-ethereum-addresses-technical-address-generation-explanation-25r3zqo)
- Running an Ethereum node
  - Since the Merge a node runs two pieces of software: an **execution client** and a **consensus client**.
  - [Run a node - ethereum.org](https://ethereum.org/run-a-node/)
  - [Spin up your own node - ethereum.org](https://ethereum.org/developers/docs/nodes-and-clients/run-a-node/)
  - [Client diversity - ethereum.org](https://ethereum.org/developers/docs/nodes-and-clients/client-diversity/) and [clientdiversity.org](https://clientdiversity.org/)
  - Execution clients: [Geth](https://geth.ethereum.org/), [Nethermind](https://www.nethermind.io/), [Besu](https://besu.hyperledger.org/), [Erigon](https://github.com/erigontech/erigon), [Reth](https://reth.rs/), [ethrex](https://github.com/lambdaclass/ethrex)
  - Consensus clients: [Lighthouse](https://lighthouse.sigmaprime.io/), [Prysm](https://github.com/OffchainLabs/prysm), [Teku](https://consensys.io/teku), [Nimbus](https://nimbus.team/), [Lodestar](https://lodestar.chainsafe.io/), [Grandine](https://github.com/grandinetech/grandine)
  - Light client: [Helios](https://github.com/a16z/helios)

## Networks, testnets and explorers

- [Networks - ethereum.org](https://ethereum.org/developers/docs/networks/) - lists current testnets and faucets.
- [Development networks - ethereum.org](https://ethereum.org/developers/docs/development-networks/)
- Public testnets
  - [Sepolia](https://github.com/eth-clients/sepolia) - the recommended testnet for smart contracts and dapps.
  - [Hoodi](https://github.com/eth-clients/hoodi) - for validator, staking and infrastructure testing (launched March 2025, replacing Holešky).
  - [Ephemery](https://ephemery.dev/) - a short-lived testnet that resets every 28 days, for validator lifecycle tests.
- Layer 2 testnets (all settle to Sepolia)
  - [Arbitrum Sepolia](https://sepolia.arbiscan.io/)
  - [OP Sepolia](https://sepolia-optimism.etherscan.io/)
  - [Base Sepolia](https://sepolia.basescan.org/)
  - [Starknet Sepolia](https://sepolia.voyager.online/)
- Local and private networks
  - Anvil (Foundry) and the Hardhat network are what you will use day to day; see [Development frameworks](#development-frameworks).
  - [Kurtosis ethereum-package - spin up a full multi-client devnet](https://github.com/ethpandaops/ethereum-package)
  - [Private networks with Geth](https://geth.ethereum.org/docs/fundamentals/private-network)
- Block explorers
  - [Etherscan (mainnet)](https://etherscan.io/), [Sepolia Etherscan](https://sepolia.etherscan.io/), [Hoodi Etherscan](https://hoodi.etherscan.io/)
  - [Blockscout - open-source explorer](https://www.blockscout.com/)
  - [Sourcify - decentralised contract verification](https://sourcify.dev/)
- Deprecated testnets: Ropsten, Rinkeby, Kovan, Goerli (and its L2 testnets) and Holešky are all shut down. Tutorials that use them need to be adapted to Sepolia.

## The Ethereum roadmap and network upgrades

This section replaces the old "Ethereum 2" section.

- [The Ethereum roadmap - ethereum.org](https://ethereum.org/roadmap/)
- [History of network upgrades - ethereum.org](https://ethereum.org/history/)
- [Danksharding and blobs - ethereum.org](https://ethereum.org/roadmap/danksharding/)
- [Glamsterdam - ethereum.org](https://ethereum.org/roadmap/glamsterdam/) - next upgrade; in public-testnet testing, mainnet date not confirmed as of November 2026.
- [Fusaka mainnet announcement - EF blog](https://blog.ethereum.org/2025/11/06/fusaka-mainnet-announcement)
- [Forkcast - track upcoming upgrades and their EIPs](https://forkcast.org/)
- [Ethereum project management - All Core Developers call agendas and notes](https://github.com/ethereum/pm)
- [EPF wiki - Ethereum Protocol Studies](https://epf.wiki/) - the best open curriculum for the core protocol.
- [Ethereum Research forum](https://ethresear.ch/)

## Development frameworks

- [Solidity and blockchain development big picture (2020)](https://soliditydeveloper.com/solidity-overview-2020)
- Current toolchains
  - [Foundry](https://getfoundry.sh/) ([GitHub](https://github.com/foundry-rs/foundry)) - Rust-based; tests are written in Solidity. Includes `forge` (build/test), `cast` (CLI), `anvil` (local node) and `chisel` (REPL).
  - [Hardhat 3](https://hardhat.org/) ([docs](https://hardhat.org/docs)) - TypeScript-first, with Solidity tests, multichain support and a Rust-powered runtime. [Hardhat 2 end of life](https://hardhat.org/docs/reference/hardhat-2-end-of-life) - migrate older projects.
  - [Ape Framework](https://github.com/ApeWorX/ape) - the maintained Python framework, successor to Brownie.
  - [Scaffold-ETH 2](https://scaffoldeth.io/) ([docs](https://docs.scaffoldeth.io/)) - a full-stack starter (Next.js, wagmi, viem, RainbowKit) on top of Hardhat or Foundry.
  - [Remix IDE](https://remix.ethereum.org) ([docs](https://remix-ide.readthedocs.io/en/latest/)) - fine for learning and quick experiments.
- Choosing: start with Foundry if you are comfortable writing tests in Solidity, or with Hardhat 3 if your team lives in TypeScript. Both can share a project, and Scaffold-ETH 2 supports either.
- Developer tools guides
  - [Developer tooling - ethereum.org](https://ethereum.org/developers/docs/frameworks/)
  - [Ethereum developer tools list (Consensys, historic but broad)](https://github.com/ConsenSys/ethereum-developer-tools-list)

## Solidity fundamentals

- [Solidity language](https://soliditylang.org/)
- [Solidity documentation](https://docs.soliditylang.org/en/latest/)
- [Solidity cheatsheet](https://docs.soliditylang.org/en/latest/cheatsheet.html)
- [Solidity forum](https://forum.soliditylang.org/)
- Layout and structure
  - [Layout of a Solidity source file](https://docs.soliditylang.org/en/latest/layout-of-source-files.html)
  - [Structure of a contract](https://docs.soliditylang.org/en/latest/structure-of-a-contract.html)
- Data types and variables
  - [Types](https://docs.soliditylang.org/en/latest/types.html)
  - [Units and global variables](https://docs.soliditylang.org/en/latest/units-and-global-variables.html)
  - [Variables by example](https://solidity-by-example.org/variables/)
- Functions
  - [Functions](https://docs.soliditylang.org/en/latest/contracts.html#functions)
  - [Functions by example](https://solidity-by-example.org/function/)
  - [Function modifiers](https://solidity-by-example.org/function-modifier/)
  - [Function selectors](https://solidity-by-example.org/function-selector/)
  - [Custom errors](https://docs.soliditylang.org/en/latest/contracts.html#errors) - cheaper and clearer than revert strings.
- Storage, memory and transient storage
  - [Data locations by example](https://solidity-by-example.org/data-locations/)
  - [Storage, memory and the stack](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#storage-memory-and-the-stack)
  - [Layout of state variables in storage](https://docs.soliditylang.org/en/latest/internals/layout_in_storage.html)
  - Transient storage (`transient` variables, EIP-1153) has been supported since Solidity 0.8.28.
- Reading smart contracts
  - [Solidity by Example](https://solidity-by-example.org/)
  - [OpenZeppelin Contracts 5.x documentation](https://docs.openzeppelin.com/contracts/5.x/)
  - [OpenZeppelin Contracts on GitHub](https://github.com/OpenZeppelin/openzeppelin-contracts)
- Smart contract Application Binary Interface (ABI)
  - [ABI specification](https://docs.soliditylang.org/en/latest/abi-spec.html)
  - [Explaining the Ethereum contract ABI and EVM bytecode](https://medium.com/@eiki1212/explaining-ethereum-contract-abi-evm-bytecode-6afa6e917c3b)
  - [What is an ABI? - QuickNode](https://www.quicknode.com/guides/ethereum-development/smart-contracts/what-is-an-abi)
- Events and logs
  - [Events](https://docs.soliditylang.org/en/latest/contracts.html#events)
  - [Events by example](https://solidity-by-example.org/events/)
- Factory contracts and deterministic deployment
  - [Contract that creates other contracts](https://solidity-by-example.org/new-contract/)
  - [Precompute a contract address with CREATE2](https://solidity-by-example.org/app/create2/)
  - [Minimal proxy clones (ERC-1167) - OpenZeppelin](https://docs.openzeppelin.com/contracts/5.x/api/proxy#Clones)
- More guides
  - [Solidity fast track part 1](https://soliditydeveloper.com/solidity-fast-track)
  - [Solidity fast track part 2](https://soliditydeveloper.com/solidity-fast-track-2)
  - [Learn X in Y minutes - Solidity](https://learnxinyminutes.com/docs/solidity/)
- Other smart contract languages
  - [Vyper](https://docs.vyperlang.org/) - Pythonic contract language, supported by Ape, Foundry and Hardhat.

## Writing smart contracts

- Introductory smart contracts
  - [Hello World](https://solidity-by-example.org/hello-world/)
  - [First app: counter](https://solidity-by-example.org/first-app/)
  - [Multi-sig wallet](https://solidity-by-example.org/app/multi-sig-wallet/)
- Inter-contract execution
  - [Calling other contracts](https://solidity-by-example.org/calling-contract/)
  - [Interfaces](https://solidity-by-example.org/interface/)
  - [Basic example of interaction between two contracts - Ethereum StackExchange](https://ethereum.stackexchange.com/questions/1599/basic-example-of-interaction-between-2-contracts)
- Inheritance
  - [Inheritance - Solidity docs](https://docs.soliditylang.org/en/latest/contracts.html#inheritance)
  - [Inheritance by example](https://solidity-by-example.org/inheritance/)
- Libraries
  - [Smart contract libraries - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/libraries/)
  - [OpenZeppelin Contracts](https://www.openzeppelin.com/solidity-contracts) and the [OpenZeppelin Contracts Wizard](https://wizard.openzeppelin.com/)
  - [Solady - gas-optimised building blocks](https://github.com/Vectorized/solady)
  - Install with your framework (`forge install` or `npm install`); the old "Ethereum Package Manager" (EthPM) is no longer used.
- Upgradeable contracts
  - [Upgrading smart contracts - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/upgrading/)
  - [OpenZeppelin Upgrades](https://docs.openzeppelin.com/upgrades-plugins/)
  - [Proxies - OpenZeppelin (ERC-1967, UUPS, transparent, beacon)](https://docs.openzeppelin.com/contracts/5.x/api/proxy)
- Smart contract system design
  - [Smart contract anatomy - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/anatomy/)
  - [Smart contract composability - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/composability/)
- Worked examples
  - [Proof of existence](https://github.com/ramyhardan/proof-of-existence)
  - [Simple bank](https://nicogs.medium.com/building-a-bank-with-solidity-for-beginners-ethereum-blockchain-development-tutorial-ba50ce6e8eb0)
  - [Multi-signature wallet exercise (Consensys Academy)](https://github.com/ConsenSys-Academy/multisig-wallet-exercise)
  - [Supply chain exercise (Consensys Academy)](https://github.com/ConsenSys-Academy/supply-chain-exercise)
  - [Ether wallet, English auction, Dutch auction, crowdfund and more - Solidity by Example apps](https://solidity-by-example.org/app/ether-wallet/)
  - [Speedrun Ethereum challenges - tokenisation, staking, token vendor, DEX and more](https://speedrunethereum.com/)
  - Older exercises use Truffle and Solidity 0.5-0.7; port them to Foundry or Hardhat 3 and Solidity 0.8 as practice.
- Games
  - [CryptoZombies](https://cryptozombies.io/) - fun for syntax, but written for an older Solidity version.

## Token standards and EIPs

- [EIPs - Ethereum Improvement Proposals](https://eips.ethereum.org/) and [ERCs - application-level standards](https://github.com/ethereum/ERCs)
- [Token standards - ethereum.org](https://ethereum.org/developers/docs/standards/tokens/)
- Core token standards
  - [ERC-20 - fungible tokens](https://eips.ethereum.org/EIPS/eip-20)
  - [ERC-721 - non-fungible tokens](https://eips.ethereum.org/EIPS/eip-721)
  - [ERC-1155 - multi-token standard](https://eips.ethereum.org/EIPS/eip-1155)
  - [ERC-4626 - tokenised vaults](https://eips.ethereum.org/EIPS/eip-4626)
  - [ERC-2612 - permit (gasless approvals)](https://eips.ethereum.org/EIPS/eip-2612)
- Signatures and accounts
  - [EIP-712 - typed structured data signing](https://eips.ethereum.org/EIPS/eip-712)
  - [ERC-1271 - signature validation for contracts](https://eips.ethereum.org/EIPS/eip-1271)
  - [ERC-4337 - account abstraction via an entry point contract](https://eips.ethereum.org/EIPS/eip-4337)
  - [EIP-7702 - set code for EOAs (Pectra)](https://eips.ethereum.org/EIPS/eip-7702)
  - [ERC-6551 - token-bound accounts](https://eips.ethereum.org/EIPS/eip-6551)
- Real-world assets and identity
  - [ERC-3643 - permissioned tokens for regulated real-world assets](https://eips.ethereum.org/EIPS/eip-3643)
  - [ERC-8004 - trustless agents (draft)](https://eips.ethereum.org/EIPS/eip-8004)
- Hands-on
  - [Create and deploy an ERC-20 - OpenZeppelin ERC-20 guide](https://docs.openzeppelin.com/contracts/5.x/erc20)
  - [Creating ERC-20 supply - OpenZeppelin](https://docs.openzeppelin.com/contracts/5.x/erc20-supply)
  - [ERC-721 guide - OpenZeppelin](https://docs.openzeppelin.com/contracts/5.x/erc721)
  - [ERC-1155 guide - OpenZeppelin](https://docs.openzeppelin.com/contracts/5.x/erc1155)
  - [NFTs - ethereum.org](https://ethereum.org/nft/)
- Note: ERC-777 is no longer recommended and was removed from OpenZeppelin Contracts in 5.0; use ERC-20 instead.

## Testing, debugging and security

- Why test?
  - [What is unit testing?](https://smartbear.com/learn/automated-testing/what-is-unit-testing/)
  - [Software testing methodologies](https://smartbear.com/learn/automated-testing/software-testing-methodologies/)
  - [Testing smart contracts - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/testing/)
- Writing tests
  - [Tests in Foundry (unit, fuzz, invariant)](https://getfoundry.sh/forge/tests/overview)
  - [Testing in Hardhat 3 (Solidity and TypeScript tests)](https://hardhat.org/docs)
  - [Unit testing in Remix](https://remix-ide.readthedocs.io/en/latest/unittesting.html)
- Debugging
  - `forge test -vvvv` traces, `cast run` and `cast call` are your first tools.
  - [Tenderly - transaction simulation and debugging](https://tenderly.co/)
  - [How to debug common smart contract errors - Tenderly](https://blog.tenderly.co/how-to-debug-common-smart-contract-errors/)
- Smart contract security best practices
  - [Smart contract security - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/security/)
  - [Smart contract security best practices - Consensys Diligence](https://consensys.github.io/smart-contract-best-practices/)
  - [Building Secure Contracts - Trail of Bits](https://secure-contracts.com/)
  - [EEA EthTrust Security Levels v3](https://entethalliance.org/specs/ethtrust-sl/v3/) and its [checklist](https://entethalliance.org/specs/ethtrust-sl/v3/checklist.html) - supersedes the unmaintained SWC registry.
  - [Solidity security considerations](https://docs.soliditylang.org/en/latest/security-considerations.html)
  - [Known attack vectors and common anti-patterns - Sigma Prime](https://blog.sigmaprime.io/solidity-security.html)
- Common exploits (work through these with code)
  - [Re-entrancy](https://solidity-by-example.org/hacks/re-entrancy/)
  - [Phishing with tx.origin](https://solidity-by-example.org/hacks/phishing-with-tx-origin/)
  - [Denial of service](https://solidity-by-example.org/hacks/denial-of-service/)
  - [Front running](https://solidity-by-example.org/hacks/front-running/)
  - [Signature replay](https://solidity-by-example.org/hacks/signature-replay/)
  - [Rekt - post-mortems of real exploits](https://rekt.news/)
  - [Solodit - searchable database of audit findings](https://solodit.cyfrin.io/)
- Gas optimisation
  - [Gas saving techniques by example](https://solidity-by-example.org/gas-golf/)
  - Measure, don't guess: `forge snapshot` and `forge test --gas-report`. Glamsterdam will reprice state access, so re-measure after it ships.
- Static analysis, fuzzing and formal verification
  - [Slither - static analysis](https://github.com/crytic/slither)
  - [Aderyn - static analysis](https://github.com/Cyfrin/aderyn)
  - [Echidna - property-based fuzzer](https://github.com/crytic/echidna) and [Medusa](https://github.com/crytic/medusa)
  - [Halmos - symbolic testing for Foundry tests](https://github.com/a16z/halmos)
  - [Certora Prover](https://docs.certora.com/)
  - [Formal verification of smart contracts - ethereum.org](https://ethereum.org/developers/docs/smart-contracts/formal-verification/)
- Safety checklist before you deploy
  - Tests pass with high coverage, including fuzz and invariant tests.
  - Static analysis output reviewed; every finding fixed or justified.
  - Access control reviewed: who can call what, and who can upgrade.
  - External calls follow checks-effects-interactions; re-entrancy guards where needed.
  - Deployed and verified on a testnet first; contract source verified on the explorer.
  - Keys for deployment and admin roles kept in a hardware wallet or a multisig such as [Safe](https://safe.global/).
- Audit contests (to learn from public reports)
  - [Code4rena](https://code4rena.com/), [Sherlock](https://www.sherlock.xyz/), [Cantina](https://cantina.xyz/)
- Learning through games
  - [Ethernaut - OpenZeppelin](https://ethernaut.openzeppelin.com/)
  - [Damn Vulnerable DeFi](https://www.damnvulnerabledefi.xyz/)
  - Capture the Ether was built on the now-shut Ropsten testnet; read the challenges and solve them locally.

## Ethereum and the end user

- Web3 introduction
  - [What is Web3? - ethereum.org](https://ethereum.org/web3/)
  - [What is Web3? The decentralised web explained - freeCodeCamp](https://www.freecodecamp.org/news/what-is-web3/)
- JavaScript/TypeScript libraries
  - [viem](https://viem.sh/) - lightweight, typed, the default in most new projects.
  - [wagmi](https://wagmi.sh/) - React hooks on top of viem for wallet connection and contract calls.
  - [ethers.js v6](https://docs.ethers.org/v6/)
  - [JavaScript API libraries - ethereum.org](https://ethereum.org/developers/docs/apis/javascript/) - includes a migration note for web3.js users.
- Python
  - [web3.py](https://web3py.readthedocs.io/)
- Wallets
  - [MetaMask](https://metamask.io/) ([developer docs](https://docs.metamask.io/))
  - [Rabby](https://rabby.io/)
  - [Safe - smart account multisig](https://safe.global/) ([docs](https://docs.safe.global/))
  - [Find a wallet - ethereum.org](https://ethereum.org/wallets/find-wallet/)
- Wallet connection kits
  - [RainbowKit](https://rainbowkit.com/)
  - [Reown AppKit (formerly WalletConnect Web3Modal)](https://reown.com/)
- Integrating with React
  - [Scaffold-ETH 2](https://scaffoldeth.io/) - the fastest route to a working React/Next.js front end.
  - [wagmi getting started](https://wagmi.sh/react/getting-started)
- User experience
  - Smart accounts (ERC-4337, EIP-7702) enable gas sponsorship, batched calls and passkey logins. Design for these rather than raw private keys.

## Layer 2 and scaling

Most user activity now happens on rollups that post their data to Ethereum.

- [Scaling - ethereum.org](https://ethereum.org/developers/docs/scaling/)
- [Optimistic rollups](https://ethereum.org/developers/docs/scaling/optimistic-rollups/) and [zero-knowledge rollups](https://ethereum.org/developers/docs/scaling/zk-rollups/)
- [Data availability - ethereum.org](https://ethereum.org/developers/docs/data-availability/)
- [L2BEAT - risk and activity of every rollup](https://l2beat.com/)
- Developer docs for major L2s
  - [Arbitrum](https://docs.arbitrum.io/)
  - [OP Stack and the Superchain (Optimism)](https://docs.optimism.io/)
  - [Base](https://docs.base.org/)
  - [ZKsync](https://docs.zksync.io/)
  - [Starknet](https://docs.starknet.io/) - uses Cairo rather than Solidity.
  - [Scroll](https://docs.scroll.io/)
  - [Linea](https://docs.linea.build/)
- Zero-knowledge proofs
  - [Zero-knowledge proofs - ethereum.org](https://ethereum.org/zero-knowledge-proofs/)
  - [Fundamentals of zero-knowledge proofs - Cyfrin Updraft](https://updraft.cyfrin.io/courses)

## Storage, naming, indexing and oracles

- Decentralised storage
  - [Decentralised storage - ethereum.org](https://ethereum.org/developers/docs/storage/)
  - [IPFS](https://ipfs.tech/) ([docs](https://docs.ipfs.tech/))
  - [IPFS simply explained - video](https://www.youtube.com/watch?v=5Uj6uR3fp-U)
  - [IPFS and friends: a qualitative comparison of next-generation peer-to-peer data networks](https://arxiv.org/pdf/2102.12737.pdf)
  - [Storacha (formerly web3.storage)](https://storacha.network/)
  - [Filecoin](https://docs.filecoin.io/)
  - [Arweave](https://arweave.org/)
- Naming
  - [ENS - Ethereum Name Service](https://ens.domains/) ([docs](https://docs.ens.domains/))
  - [ENS: the good, the bad, and the ugly](https://arxiv.org/abs/2104.05185)
- Indexing and querying chain data
  - [The Graph](https://thegraph.com/docs/)
  - [Ponder - TypeScript indexing framework](https://ponder.sh/)
- Oracles
  - [Oracles - ethereum.org](https://ethereum.org/developers/docs/oracles/)
  - [Chainlink documentation](https://docs.chain.link/) and [Chainlink CCIP for cross-chain messages](https://docs.chain.link/ccip)
- Attestations
  - [Ethereum Attestation Service (EAS)](https://attest.org/) - signed, on-chain or off-chain statements about anything; useful for provenance and certification.

## Decentralised finance

- [What is DeFi? - ethereum.org](https://ethereum.org/defi/)
- [Finematics - DeFi concepts explained (video)](https://www.youtube.com/c/Finematics/videos)
- [Uniswap docs (v2-v4)](https://docs.uniswap.org/)
- [Uniswap V2 by example](https://solidity-by-example.org/defi/uniswap-v2/)
- [Aave docs](https://aave.com/docs)
- [DeFiLlama - TVL and protocol data](https://defillama.com/)
- Flash loans: read the Aave docs above, then try the flash-loan challenges in Damn Vulnerable DeFi.
- Security flaw walkthroughs: [Rekt](https://rekt.news/) and [Damn Vulnerable DeFi](https://www.damnvulnerabledefi.xyz/)
- Decentralised exchanges: start with the [Speedrun Ethereum DEX challenge](https://speedrunethereum.com/) and then read the Uniswap v2 core contracts.

## DAOs and token engineering

- [What is a DAO? - ethereum.org](https://ethereum.org/dao/)
- [Top 10 words to know about DAOs - ArchiDAO](https://archidao.substack.com/p/top-10-words-to-know-about-dao-decentralized)
- DAO frameworks and tools
  - [OpenZeppelin Governor](https://docs.openzeppelin.com/contracts/5.x/governance)
  - [Aragon](https://aragon.org/)
  - [Colony](https://colony.io/)
  - [Safe](https://safe.global/) - the treasury multisig behind most DAOs.
  - [Snapshot - off-chain voting](https://snapshot.box/)
  - [Tally - on-chain governance interface](https://www.tally.xyz/)
- Token engineering
  - [Token Engineering Academy](https://tokenengineering.net/)
  - Token simulations: [cadCAD](https://cadcad.org/) and [radCAD](https://github.com/CADLabs/radCAD)
  - Ostrom's principles for governing the commons: [Elinor Ostrom's Nobel lecture (2009)](https://www.nobelprize.org/prizes/economic-sciences/2009/ostrom/lecture/)

## AI agents and Ethereum

A fast-moving area: autonomous software agents that hold wallets, pay for services and build reputations on-chain.

- [ERC-8004: Trustless Agents (draft)](https://eips.ethereum.org/EIPS/eip-8004) - identity, reputation and validation registries for agents; reference registries were deployed to mainnet in January 2026.
- [x402](https://www.x402.org/) - an open protocol for HTTP-native payments, used for agent-to-service micropayments.
- AI-assisted development: AI coding agents are now common in Solidity work (Remix, Foundry and OpenZeppelin all ship AI features). Treat generated contracts as untrusted code: test, fuzz and review them as you would a stranger's pull request.

## Blockchain in architecture, engineering and construction

Why this companion exists. AEC projects are fragmented across many organisations that must share information and money without fully trusting each other. Blockchains offer shared records, programmable payments and new forms of governance. Typical use cases are provenance of design information (BIM model versions, approvals), payment and milestone automation, supply-chain and material passports for circularity, performance-based contracts linked to digital twins, and DAOs for design collectives or competitions.

- Books
  - [Blockchain for Construction - T. Dounas and D. Lombardi (eds.), Springer, 2022](https://doi.org/10.1007/978-981-19-3759-0)
- Papers
  - [Dounas, T., Lombardi, D. and Jabi, W. (2021) Framework for decentralised architectural design BIM and Blockchain integration. International Journal of Architectural Computing, 19(2), 157-173](https://doi.org/10.1177/1478077120963376)
  - [Dounas, T., Lombardi, D. and Jabi, W. (2019) Towards blockchains for architectural design: consensus mechanisms for collaboration in BIM. eCAADe/SIGraDi 2019](https://doi.org/10.5151/proceedings-ecaadesigradi2019_296)
  - [Dounas, T. and Lombardi, D. (2019) Blockchain grammars: designing with DAOs. CAADRIA 2019](https://rgu-repository.worktribe.com/output/323143/blockchain-grammars-designing-with-daos)
  - [Li, J., Greenwood, D. and Kassem, M. (2019) Blockchain in the built environment and construction industry: a systematic review, conceptual models and practical use cases. Automation in Construction, 102, 288-307](https://doi.org/10.1016/j.autcon.2019.02.005)
  - [Hunhevicz, J.J. and Hall, D.M. (2020) Do you need a blockchain in construction? Use case categories and decision framework for DLT design options. Advanced Engineering Informatics, 45, 101094](https://arxiv.org/abs/2004.04626)
  - [Li, J. and Kassem, M. (2021) Applications of distributed ledger technology (DLT) and blockchain-enabled smart contracts in construction. Automation in Construction, 132, 103955](https://doi.org/10.1016/j.autcon.2021.103955)
  - [Hunhevicz, J.J., Motie, M. and Hall, D.M. (2022) Digital building twins and blockchain for performance-based (smart) contracts. Automation in Construction, 133, 103981](https://arxiv.org/abs/2105.05192)
  - [Msawil, M., Greenwood, D. and Kassem, M. (2022) A systematic evaluation of blockchain-enabled contract administration in construction projects. Automation in Construction, 143, 104553](https://doi.org/10.1016/j.autcon.2022.104553)
- Standards to look at for AEC prototypes
  - ERC-721/ERC-1155 for material passports and asset records, EAS for attestations of design or inspection events, ERC-3643 for regulated real-asset tokens, OpenZeppelin Governor for project governance. See [Token standards and EIPs](#token-standards-and-eips).

## Videos and developers to follow

- Full courses
  - [Learn Blockchain, Solidity and full-stack Web3 development with JavaScript - Patrick Collins, 32 hours (2022)](https://www.youtube.com/watch?v=gyMwXuJrbJQ) - still a good walkthrough, but uses Hardhat 2 and ethers v5; Cyfrin Updraft has the current versions.
  - [The complete guide to full-stack Ethereum development - Nader Dabit](https://www.youtube.com/watch?v=WsZyb2T83lo)
- Channels
  - [Cyfrin Updraft / Patrick Collins](https://www.youtube.com/c/PatrickCollins) - [GitHub](https://github.com/PatrickAlphaC)
  - [Smart Contract Programmer](https://www.youtube.com/channel/UCJWh7F3AFyQ_x01VKzr9eyA/featured)
  - [ETHGlobal - protocol tutorials and hackathon talks](https://www.youtube.com/c/ETHGlobal)
  - [Austin Griffith (BuidlGuidl, Scaffold-ETH)](https://www.youtube.com/channel/UC_HI2i2peo1A-STdG22GFsA/featured) - [GitHub](https://github.com/austintgriffith)
  - [Eat The Blocks](https://www.youtube.com/channel/UCZM8XQjNOyG2ElPpEUtNasA) - [GitHub](https://github.com/jklepatch/eattheblocks)
  - [Nader Dabit](https://www.youtube.com/c/naderdabit) - [GitHub](https://github.com/dabit3)
  - [Chainlink](https://www.youtube.com/channel/UCnjkrlqaWEBSnKZQ71gdyFA)
  - [Dapp University](https://www.youtube.com/c/DappUniversity) - older tutorials, mostly Truffle and web3.js.
  - [HashLips - generative NFTs](https://www.youtube.com/channel/UC1LV4_VQGBJHTJjEWUmy8nA) - [GitHub](https://github.com/HashLips)
- Visual no-code builder
  - [Eth.Build - an educational sandbox for Web3](https://eth.build/)

## Policy and regulation

- [Decentralisation - Internet Policy Review](https://policyreview.info/concepts/decentralisation)
- [Hacker-engineers and their economies, by J.K. Brekke](https://www.tandfonline.com/doi/abs/10.1080/13563467.2020.1806223)
- [EU Markets in Crypto-Assets Regulation (MiCA), Regulation (EU) 2023/1114](https://eur-lex.europa.eu/eli/reg/2023/1114/oj) - the EU framework for crypto-asset issuers and service providers.
- Regulation changes quickly and differs by country; check your own jurisdiction before you launch anything with real value.

## History

- [Ethereum "pre-history" - V. Buterin](https://vitalik.eth.limo/general/2017/09/14/prehistory.html)
- [History of Ethereum's network upgrades - ethereum.org](https://ethereum.org/history/)
- Books: _Out of the Ether: The Amazing Story of Ethereum and the $55 Million Heist that Almost Destroyed It All_ by Matthew Leising (2020), and _The Infinite Machine: How an Army of Crypto-hackers Is Building the Next Internet with Ethereum_ by Camila Russo (2020).

## Community, news and help

- Where to ask for help
  - [Ethereum StackExchange](https://ethereum.stackexchange.com/)
  - [Solidity forum](https://forum.soliditylang.org/)
  - [r/ethdev - Reddit community](https://www.reddit.com/r/ethdev/)
  - [Foundry](https://github.com/foundry-rs/foundry/discussions) and [Hardhat](https://github.com/NomicFoundation/hardhat/discussions) GitHub discussions
- Standards and research discussion
  - [Fellowship of Ethereum Magicians](https://ethereum-magicians.org/)
  - [Ethereum Research](https://ethresear.ch/)
- News
  - [Ethereum Foundation blog](https://blog.ethereum.org/)
  - [The Defiant](https://thedefiant.io/)
  - [The Block](https://www.theblock.co/)
  - [Decrypt](https://decrypt.co/)
  - [CoinDesk](https://www.coindesk.com/)
  - [Cointelegraph](https://cointelegraph.com/)
  - [Week in Ethereum News archive (ended January 2025)](https://weekinethereum.substack.com/archive)
- Events and hackathons
  - [ETHGlobal](https://ethglobal.com/)
  - [Devcon](https://devcon.org/)
- Additional GitHub repositories
  - [Awesome Ethereum](https://github.com/bekatom/awesome-ethereum)
  - [Awesome Solidity](https://github.com/bkrem/awesome-solidity)
  - [Consensys Developer Tools List](https://github.com/ConsenSys/ethereum-developer-tools-list)
- Where to find a job
  - [Crypto Jobs List](https://cryptojobslist.com/)
  - [web3.career](https://web3.career/)
- Organisations
  - [Ethereum Foundation](https://ethereum.foundation/)
  - [Nomic Foundation (Hardhat)](https://nomic.foundation/)
  - [OpenZeppelin](https://www.openzeppelin.com/)
  - [Consensys](https://consensys.io/)
  - [Protocol Labs](https://www.protocol.ai/)

## Deprecated and archived

You will meet these in older tutorials. Do not start new work with them.

| Tool or resource | Status | Use instead |
| --- | --- | --- |
| Truffle, Ganache, Drizzle, Truffle Boxes | [Archived December 2023](https://consensys.io/blog/consensys-announces-the-sunset-of-truffle-and-ganache-and-new-hardhat) | Foundry, Hardhat 3, Anvil |
| Brownie | [No longer maintained](https://github.com/eth-brownie/brownie) | Ape Framework |
| Hardhat 2 | [End of life by 1 June 2027 at the latest](https://hardhat.org/docs/reference/hardhat-2-end-of-life) | Hardhat 3 |
| web3.js | [Archived March 2025](https://blog.chainsafe.io/web3-js-sunset/) | viem, ethers v6 |
| Rimble UI | Archived | RainbowKit, Scaffold-ETH 2 components |
| OpenEthereum | Discontinued | Geth, Nethermind, Besu, Erigon, Reth |
| Ropsten, Rinkeby, Kovan, Goerli, Holešky testnets | Shut down | Sepolia, Hoodi |
| Remix Desktop (old `ethereum/remix-desktop` repo) | Archived May 2024 | [Current Remix Desktop](https://remix-ide.readthedocs.io/en/latest/desktop.html) |
| EthFiddle | Supports only old Solidity | Remix IDE |
| SWC Registry | [Not maintained since 2020](https://github.com/SmartContractSecurity/SWC-registry) | EthTrust Security Levels |
| ERC-777 | Removed from OpenZeppelin 5.0 | ERC-20 |
| eth.wiki and the Ethereum GitHub wiki | Deprecated, repository removed | ethereum.org |
| EthHub | No longer maintained | ethereum.org |
| Week in Ethereum News | Ended January 2025 | EF blog, The Defiant |
| DeFi Pulse | No longer updated | DeFiLlama |
| DAOstack | Discontinued | OpenZeppelin Governor, Aragon |
| web3.storage | Renamed | Storacha |
| Flint (Swift-like contract language) | Research project, inactive | Solidity, Vyper |
| "Ethereum 2.0" / "Eth2" | Retired terms | Consensus layer, execution layer |

## Project Brief

Design, build, test and deploy a decentralised application that addresses a real problem in architecture, engineering or construction (or another domain agreed with your tutor). Work alone or in pairs.

**Deliverables**

1. A public Git repository containing:
   - smart contracts in Solidity 0.8.x (or Vyper), built with Foundry or Hardhat 3;
   - a test suite with unit tests and at least one fuzz or invariant test, and a coverage report;
   - a README explaining the problem, the architecture and how to run the project.
2. The contracts deployed and source-verified on Sepolia or an L2 testnet (e.g. Base Sepolia, OP Sepolia, Arbitrum Sepolia).
3. A minimal front end (Scaffold-ETH 2, or viem/wagmi) that lets a user connect a wallet and complete the main flow.
4. A security self-review: Slither or Aderyn output with each finding addressed, and a short assessment against the EthTrust Security Levels checklist.
5. A report (1,500-2,500 words) and a five-minute demo video covering the problem, why a blockchain is (or is not) the right tool, design decisions, trade-offs and limitations.

**Example project ideas**

- Material passports: ERC-1155 tokens or EAS attestations recording a component's origin, condition and reuse history.
- Design competition: commit-reveal submission and jury voting, with prize release by smart contract.
- Milestone payments: an escrow that releases test-stablecoin payments when the client and an inspector both sign off.
- BIM provenance: hashes of IFC model versions anchored on-chain, files on IPFS, approvals as signatures.
- A design collective DAO: OpenZeppelin Governor plus a Safe treasury for commissioning and paying contributors.

**How it maps to the learning outcomes**

- Outcomes 1-2: the README and report.
- Outcome 3: contracts, tests and testnet deployment.
- Outcome 4: the security self-review.
- Outcome 5: the deployed dapp and demo.

---

_Maintained by_
- [arlav](https://github.com/arlav)
- [HicoMcD](https://github.com/HicoMcD)

Contributions are welcome: open an issue or a pull request. Links are checked automatically every week.
