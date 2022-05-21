# The Monitor

This repository contains the logic of our Dapp *The Monitor*, our submission to Chainlink's Spring Hackathon 2022.

## What it does

*The Monitor* keeps an eye on your address and checks if you receive any staking rewards. 

Deposit some ETH, set your order, and *The Monitor* will automatically swap a "mirror" amount of the staking rewards you receive for DAI (more tokens coming soon). 

This way, you can sleep easy knowing that a portion of your staking rewards stays tucked away in a stable coin, that you can withdraw from our contract whenever you want! Pretty neat isn't it?

*The Monitor* also keeps an history of the swaps it performs on your behalf, to help with your bookkeeping and, God forbid, tax records.

## The Codebase

This project contains two main repositories:

- [Contract Code](https://github.com/ChainlinkHackathon-StakingMonitor/contract)
- [Front end Code](https://github.com/ChainlinkHackathon-StakingMonitor/front_end)

It also contains a [documentation](https://github.com/ChainlinkHackathon-StakingMonitor/architecture_and_design) repository, which contains the documents we created while designing *The Monitor*.

### Contract Code

We developed the contract using Brownie, and use Pytest for testing. The contract makes use of Chainlink Keepers to keep an eye on when staking rewards drop on our users' addresses, and of Chainlink Price feeds to get the price of ETH in USD to trigger the swap orders set up by our users.

### Front End Code

Our front end uses Next.js, and makes use of Web3uikit and ethers to connect to Web 3. In addition to this, we make use of Covalent to fetch the events emitted by our contracts when a swap takes place, to display the history of swaps for each user.

