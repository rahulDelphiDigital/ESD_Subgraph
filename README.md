# Empty Set Dollar
The dollar protocol is operated by a DAO that governs and operates the supply of its stablecoin ESD, a fully decentralized self-stabilizing dollar.

# Empty Set Dollar Subgraph
This Subgraph ingests the following events emitted by the contracts of the ESD protocol. 

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

