# Contracts-Testing

A smart contract project built with Solidity and Foundry, focused on implementing and testing a fully automated raffle system using Chainlink VRF and Keepers. This repository emphasizes unit testing, fuzz testing, and mock-based verification to ensure contract reliability.

## Features

- Raffle contract using Chainlink VRF v2.5  
- Automated upkeep using Chainlink Keepers  
- Verifiable randomness for winner selection  
- Extensive Foundry tests:
  - Unit testing  
  - Event testing  
  - Revert condition checks  
  - Fuzz testing  
- Deployment and interaction scripts  
- Mock contracts for local testing

## Tech Stack

| Component  | Tool/Version       |
|------------|---------------------|
| Language   | Solidity ^0.8.0    |
| Framework  | Foundry (Forge/Cast)|
| Randomness | Chainlink VRF v2.5  |
| Automation | Chainlink Keepers   |
| Testing    | forge-std & mocks   |


## Getting Started

### 1. Install Foundry

```
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

### 2. Install Dependencies

```
forge install
```

### 3. Build Contracts

```
forge build
```

### 4. Run Tests

```
forge test
```

To see verbose output:

```
forge test -vvv
```

## Key Contracts

### Raffle.sol
Implements:
- Entrance fee logic  
- Randomness request via VRF  
- State transitions (OPEN → CALCULATING)  
- Event emissions  
- ETH transfers to winners

### HelperConfig.s.sol
Manages:
- Local vs Sepolia configuration  
- Mock deployment on local networks

### DeployRaffle.s.sol
Responsible for:
- Config retrieval  
- Deployment  
- Subscription setup

### Interactions.s.sol
Includes scripts to:
- Create subscriptions  
- Fund subscriptions  
- Add consumer contracts

## Testing

All tests are in `test/RaffleTest.t.sol` and cover:

- Initial state validation  
- Reverts when insufficient ETH is sent  
- Player recording  
- Event emissions  
- Rejecting entries while CALCULATING  
- `checkUpkeep` logic  
- `performUpkeep` behavior  
- Fuzz tests on VRF fulfillment

Example:

```
forge test --match-test testRaffleRevertsWhenYouDontPayEnough
```

## License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so.

