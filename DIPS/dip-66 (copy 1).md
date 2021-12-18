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

Arbitrum gas fees has rised to much. It actually flee more users than locking-down of Ethereum PoS doesn't have such problem

## Specification


### Proposed Code



