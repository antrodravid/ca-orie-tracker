# Calorie Tracker 
## Overview

The Calorie Tracker Smart Contract is a Solidity-based Ethereum smart contract designed to allow a user to log their consumed calories on the Ethereum blockchain. It provides a simple mechanism for tracking daily calorie intake and imposes a limit to prevent exceeding a specified daily calorie limit.

## License

This software is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Prerequisites

- Ethereum development environment (e.g., [Remix](https://remix.ethereum.org/), [Truffle](https://www.trufflesuite.com/))
- Solidity compiler version ^0.8.0

## Smart Contract Details

### CalorieTracker Contract

- **user**: The Ethereum address of the user who deploys the contract.
- **consumedCalories**: A mapping of Ethereum addresses to the total calories consumed by each user.

### Constructor

- Initializes the `user` variable with the Ethereum address of the deploying user.

### logCalories Function

- **Modifiers**:
  - `require(msg.sender == user, "Only the user can log calories")`: Ensures that only the deploying user can log calories.
  - `assert(calories >= 100)`: Asserts that the logged calories must be greater than or equal to 100.

- **Logic**:
  - Checks if the sum of previously consumed calories and the new calories exceeds the daily limit (10,000 calories). If so, reverts with the message "Daily calorie limit exceeded."
  - Updates the `consumedCalories` mapping with the new calorie intake.

## Usage

1. Deploy the CalorieTracker smart contract to the Ethereum blockchain using your preferred development environment.

2. The deploying user can then use the `logCalories` function to log their daily calorie intake. The function enforces that only the user can log calories and that each log must be for at least 100 calories.

3. The contract keeps track of the total calories consumed by the user and prevents exceeding the daily limit of 10,000 calories.

## Security Considerations

- Ensure that only the intended user deploys the smart contract to prevent unauthorized access to the CalorieTracker functionalities.
- The daily calorie limit is set to 10,000 calories, and exceeding this limit will trigger a revert. Adjust this limit based on your specific requirements.

