# Empty Set Dollar
The dollar protocol is operated by a DAO that governs and operates the supply of its stablecoin ESD, a fully decentralized self-stabilizing dollar.

# Empty Set Dollar Subgraph
This Subgraph ingests the following events emitted by the contracts of the ESD protocol. 

## Basic Terminologies

**Bonding** - Bonding is the act of locking your token in the Empty Set Dollar DAO to gain benefits such as voting or rewards.

**Staging** - Tokens must pass through a staging phase when entering the DAO. When the tokens are staged they will be available to bond. This state is used to control the deposit and withdrawal of tokens when your tokens are "fluid". 

## Getting started with querying
Below are some of the queries supported by the Subgraph. The queries show most of the information that is queryable, but there are many other filtering options that can be used, just check out the querying api.

Meta's `lpAddress` stores the address of the current pool contract.
```
{
  metas(first: 5) {
    id
    lpAddress
  }
}
```

Dollar's DAO splits time into distinct `epochs` of roughly one day to simplify logic around governance, supply regulation, and flash loan resistance. The following query will return the protocol state during a particular epoch.

```
{
  epochSnapshots(first: 5) {
    id
    epoch
    timestamp
    block

    expiredCoupons
    couponsExpiration
    oraclePrice

    daoBondedEsdTotal (ESD can be bonded for rewards, minting ESDS)
    daoBondedEsdsTotal (Amount of ESDS)

    daoBondedEsdsFrozen  (total ESDS is in accounts that are frozen)
    daoBondedEsdsFluid
    daoBondedEsdsLocked (total ESDS locked during voting)
    
    daoStagedEsdTotal 
    daoStagedEsdFrozen
    daoStagedEsdFluid
    daoStagedEsdFrozen 
    
    lpBondedUniV2Total
    lpBondedUniV2Frozen
    lpBondedUniV2Fluid
    
    lpStagedUniV2Total
    lpStagedUniV2Frozen
    lpStagedUniV2Fluid
    
    lpClaimableEsdTotal
    lpClaimableEsdFrozen
    lpClaimableEsdFluid
    lpRewardedEsdTotal
  }
}
```
 expiredCoupons : Number of coupons that got expired during the current Epoch
 
 couponsExpiration : Epoch when the Coupons will get expired
 
 oraclePrice : The current price from the Uniswap price oracle

    daoBondedEsdTotal (ESD can be bonded for rewards, minting ESDS)
    daoBondedEsdsTotal (Amount of ESDS)

    daoBondedEsdsFrozen  (total ESDS is in accounts that are frozen)
    daoBondedEsdsFluid
    daoBondedEsdsLocked (total ESDS locked during voting)
    
    daoStagedEsdTotal 
    daoStagedEsdFrozen
    daoStagedEsdFluid
    daoStagedEsdFrozen 
    
    lpBondedUniV2Total
    lpBondedUniV2Frozen
    lpBondedUniV2Fluid
    
    lpStagedUniV2Total
    lpStagedUniV2Frozen
    lpStagedUniV2Fluid
    
    lpClaimableEsdTotal
    lpClaimableEsdFrozen
    lpClaimableEsdFluid
    lpRewardedEsdTotal



```
{
  fundsToBeFrozens(first: 5) {
    id
    epoch
    daoStagedEsdFluidToFrozen
    daoStagedEsdLockedToFrozen
    daoBondedEsdsFluidToFrozen
    daoBondedEsdsLockedToFrozen
    lpStagedUniV2FluidToFrozen
    lpBondedUniV2FluidToFrozen
    lpClaimableEsdFluidToFrozen    
  }
}
```

```
{
  esdSupplyHistories(first: 5) {
    id
    epoch
    daoLockedTotal
    lpLockedTotal
    totalSupply
  }
}
```

```
{
  lpUniV2TokenHistories(first: 5) {
    id
    epoch
    totalStaged
    totalBonded
    totalSupply
  }
}
```

```
{
  addressInfos(first: 5) {
    id
    esdBalance
    uniV2Balance
    daoBondedEsds
    daoStagedEsd
    daoLockedUntilEpoch
    daoFluidUntilEpoch
    lpBondedUniV2
    lpStagedUniV2
    lpClaimableEsd
    lpFluidUntilEpoch
  }
}
```


## Contract Events Mapped by the SubGraph
SubGraph currently listens to the following events to update the state of the indexed data.

#### UpgradeableContract
        - Upgraded(indexed address) 

#### UniswapV2PairContract
        - Transfer(indexed address,indexed address,uint256)

#### DollarContract
        - Transfer(indexed address,indexed address,uint256)

#### DaoContract
        - Advance(indexed uint256,uint256,uint256)
        - Deposit(indexed address,uint256)
        - Withdraw(indexed address,uint256)
        - Bond(indexed address,uint256,uint256,uint256)
        - Unbond(indexed address,uint256,uint256,uint256)
        - Vote(indexed address,indexed address,uint8,uint256)
        - StabilityReward(indexed uint256,uint256,uint256)
        - SupplyDecrease(indexed uint256,uint256,uint256)
        - SupplyIncrease(indexed uint256,uint256,uint256,uint256,uint256)
        - SupplyNeutral(indexed uint256)
        - CouponExpiration(indexed uint256,uint256,uint256,uint256,uint256)

#### LpContract
        - Deposit(indexed address,uint256)
        - Withdraw(indexed address,uint256)
        - Provide(indexed address,uint256,uint256,uint256)
        - Bond(indexed address,uint256,uint256)
        - Unbond(indexed address,uint256,uint256,uint256)
        - Claim(indexed address,uint256)


## Networks and Performance
This subgraph can be found on The Graph Hosted Service at [https://thegraph.com/explorer/subgraph/elfedy/ayaesg](https://thegraph.com/explorer/subgraph/elfedy/ayaesg).

You can also run this subgraph locally, if you wish. Instructions for that can be found in The Graph Documentation.

## Contract Upgrades
The subgraph has been kept in sync with the development of ESD.

