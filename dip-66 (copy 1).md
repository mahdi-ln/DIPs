```
DIP: 67
Title: Move to a PoS side-chain
Author(s): Mahdi-ln
Contributors:
Type: Enhancement
Status: <Assigned by DIP Editor>
Date Proposed: 
Date Ratified: <date created on, in ISO 8601 (yyyy-mm-dd) format>
Dependencies:
Replaces:
License: CC0
```

## References

## Sentence Summary

A proposal for Move to an Ethereum PoS side-chain

## Paragraph Summary

 .

sTokens improves staking composability.

## Component Summary

- **[Uniqueness]**
  sTokens is a unique NFT for each staking.
- **[Certificate of Staking]**
  A sTokens holder is considered to be the person who ran the staking stored in sTokens. If you transfer sTokens to another person, that right will also be transferred.

  sTokens stores the values of staking destination, staking amount, last reward unit price, cumulative reward amount, and pending reward amount into each NFT.

- **[NFT, not ERC-20]**
  By staking 10 DEV on a Property token, the staker gets 1 sTokens NFT. By staking 1,000 DEV on a Property token, the staker gets 1 sTokens NFT.
- **[Update]**
  sTokens change the state by withdrawing or adding staking. There is no burn.
- **[Bridge]**
  In some cases, ERC-20 is preferable to NFT. In that case, a user can extend the composability by creating a third-party bridge contract for NFT<>ERC-20.

## Motivation

Arbitrum gas fees has rised to much. It actually flee more users than lock-One of Ethereum PoS doesn't have such problem

## Specification

sTokens are automatically issued upon staking and can be updated upon unstake.

- **[Creating sTokens]**
  sTokens is created as an NFT by STokensManager when users call `Lockup.deposit` and the Lockup contract calls STokensManager.
- **[Updating sTokens]**
  By users call the `Lockup.deposit` or `Lockup.withdraw`, STokensManager is called from the Lockup contract, data of existing sTokens will be updated by STokensManager.
- **[Deleting sTokens]**
  There is no deletions interface in sTokens. By the same procedure as updating sTokens, the amount of staking position is set to 0 to indicate that the position no longer exists.
- **[STokensManager]**
  A new contract to manage minting and updating sTokens, the deployed address by the local variables of Lockup Contract have been retained.

### Why not ERC-20?

Dev Protocol staking rewards change the rate of return at unpredictable timings as third parties increase or decrease staking. To implement that property, Dev Protocol handles a cumulative sum of the reward unit prices that continue to be increased and a snapshot of that cumulative sum at the time for each staking. The staking rewards are unique, and fungible tokens are inconvenient to retain that unique data. This is similar to why Uniswap v3's liquidity tokens are now NFTs instead of ERC-20.

### Proposed Code

