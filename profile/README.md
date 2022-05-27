# The Monitor

This repository contains the codebase of our dapp *The Monitor*, our submission to Chainlink's Spring Hackathon 2022.

_The Monitor_'s front-end is deployed on IPFS through fleek at the following URL: [https://yellow-term-9557.on.fleek.co/](https://yellow-term-9557.on.fleek.co/).

The latest version of the contract deployed on Kovan can be seen on [Etherscan](https://kovan.etherscan.io/address/0x6736c1233D8aA9e796FD7b5eAe1a41Cdaf573170).

The Keeper we registered to kepp *The Monitor* ticking on Kovan can be seen there: [https://keepers.chain.link/kovan/3303](https://keepers.chain.link/kovan/3374).


## Try it out

- Deposit some Kovan ETH into our contract using our [front-end](https://yellow-term-9557.on.fleek.co/)
- Set an Order (ideally with a low price for ETH, to make sure your order will trigger a swap)
- Mimic a staking reward by sending ETH (ideally lower than the amount that you deposited, to allow the swap to take place) to the address you used to deposit into *The Monitor*
- Wait a few minutes for the upkeep to take place (currently, the upkeep interval is set to **15 minutes**)

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

We developed the contract using Brownie, and use Pytest for testing. The contract makes use of Chainlink's Keepers to keep an eye on when staking rewards drop on our users' addresses, and of Chainlink's Price feeds to get the price of ETH in USD to trigger the swap orders set up by our users.

### Front-End Code

Our front-end uses Next.js, and makes use of Web3uikit and ethers to connect to Web 3. In addition to this, we make use of Covalent to fetch the events emitted by our contracts when a swap takes place, to display the history of swaps for each user.

