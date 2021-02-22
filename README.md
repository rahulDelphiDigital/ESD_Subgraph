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


Networks and Performance
This subgraph can be found on The Graph Hosted Service at https://thegraph.com/explorer/subgraph/compound-finance/compound.

You can also run this subgraph locally, if you wish. Instructions for that can be found in The Graph Documentation.

Contract Upgrades
The subgraph will be kept in sync with the development of Compound-V2 until the official mainnet launch. The Hosted service will always be updated with the most recent subgraph.

After that, the only changes to V2 should be new assets added, which the subgraph will stay up to date with. This may be possible to do so dynamically, without subgraph updates. To be concluded.

Contracts not tracked at all
These contracts were left out:

PriceOracle.sol - For the testnet this is just a simple price oracle, it will be updated to a real one on mainnet, and likely included in the subgraph
StableCoinInterestRateModel.sol - No data was chosen to be sourced from here
StandardInterestRateModel.sol - No data was chosen to be sourced from here
ABI
The ABI used is ctoken.json. It is a stripped down version of the full abi provided by compound, that satisfies the calls we need to make for both cETH and cERC20 contracts. This way we can use 1 ABI file, and one mapping for cETH and cERC20.
