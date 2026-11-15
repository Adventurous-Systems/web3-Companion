# Changelog

## November 2026

A full review of the companion, which had last been updated in January 2024.

### Ethereum and tooling updates

- Added a "What changed since the last edition" summary: Dencun (blobs), Pectra (EIP-7702), Fusaka (PeerDAS), Glamsterdam status, 60M gas limit.
- Testnets: Sepolia (apps) and Hoodi (validators) as current; Goerli, Holešky and the Goerli L2 testnets moved to deprecated. Added L2 Sepolia testnets and Ephemery.
- Frameworks: Foundry 1.x and Hardhat 3 as the main toolchains, Ape for Python, Scaffold-ETH 2 for full-stack starters. Truffle, Ganache, Drizzle and Brownie moved to deprecated; Hardhat 2 end of life noted.
- Libraries: viem and wagmi added; ethers links moved to v6; web3.js marked archived (March 2025).
- Clients: execution/consensus client lists updated (Reth, ethrex, Grandine added; OpenEthereum removed).
- "Ethereum 2" section replaced by "The Ethereum roadmap and network upgrades".
- Solidity docs links moved from pinned versions (0.8.6, 0.8.7, 0.8.23) to `latest`; OpenZeppelin links moved from 2.x/3.x/4.x to 5.x.
- Operating systems: Ubuntu 26.04/24.04 LTS, macOS 27, current WSL install guide; removed end-of-life Ubuntu 20.04 and 23.10 and the CentOS link.

### New sections

- Onboarding and full learning paths (Speedrun Ethereum, Cyfrin Updraft, Mastering Ethereum 2nd edition).
- Networks, testnets and explorers.
- Layer 2 and scaling.
- Storage, naming, indexing and oracles (Storacha, Ponder, EAS).
- AI agents and Ethereum (ERC-8004, x402).
- Blockchain in architecture, engineering and construction, with key papers.
- Deprecated and archived table.
- Project Brief, and a 12-week schedule in the syllabus.

### Fixes

- Filled empty headings (Exploits, Gas optimisation, Safety checklist, Token simulations, Ostrom principles, History, Academic papers).
- Removed duplicated sections (Frameworks, NFTs, Token standards) and links (one YouTube video was linked under three different titles).
- Fixed broken URLs (`httpe://`, links missing `https://`, vitalik.ca to vitalik.eth.limo), typos and the code fence around the learning outcomes.
- Removed `markdown.md` (GitHub Pages boilerplate pointing at the old AthensLab repository).
- README now points at the Adventurous Systems GitHub Pages URL.
- Added a weekly link checker (GitHub Actions + lychee).

## January 2024

- Previous update (Foundry added, Goerli deprecated, Holešky added).
