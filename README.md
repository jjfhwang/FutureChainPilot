# FutureChainPilot: Decentralized Automation for EVM Smart Contracts

EVM-compatible smart contract automation via secure API: Gas-optimized strategies deployed using decentralized off-chain computation; enhanced Oracle integration.

## Detailed Description

FutureChainPilot provides a framework for automating the execution of EVM smart contracts based on predefined strategies and external data feeds. It addresses the limitations of traditional smart contract automation by leveraging decentralized off-chain computation, which significantly reduces gas costs and provides a more secure and reliable execution environment. The system is designed to be highly adaptable, allowing developers to define custom automation strategies tailored to their specific needs. It seamlessly integrates with various Oracle solutions, enabling smart contracts to react to real-world events with minimal latency. The core principle is to shift computationally intensive tasks off-chain, performing them in a distributed and verifiable manner, while only submitting the final results to the EVM chain. This architecture facilitates the development of sophisticated and responsive decentralized applications (dApps) that are both efficient and secure.

The framework comprises several key components working in tandem: a series of on-chain smart contracts that define the automation tasks and store the execution logic, a network of off-chain workers that monitor the blockchain and execute the defined strategies, and a secure API layer that enables communication between the on-chain contracts and the off-chain workers. The off-chain workers are designed to be fault-tolerant and decentralized, ensuring that automation tasks are executed even in the event of individual node failures. Security is paramount, with mechanisms in place to verify the integrity of the off-chain computations and prevent malicious actors from manipulating the execution results.

FutureChainPilot's unique approach facilitates the development of complex dApps that would be prohibitively expensive or technically challenging to implement using traditional on-chain methods. It enables use cases such as automated rebalancing of DeFi portfolios, dynamic adjustment of interest rates based on market conditions, and automatic execution of limit orders on decentralized exchanges. By abstracting away the complexities of off-chain computation and Oracle integration, FutureChainPilot empowers developers to focus on building innovative and impactful dApps.

## Key Features

*   **Gas-Optimized Automation:** Executes computationally intensive tasks off-chain, significantly reducing gas costs associated with on-chain execution. The off-chain workers only submit the final results or state updates to the EVM chain.
*   **Decentralized Off-Chain Computation:** Leverages a decentralized network of workers to perform computations, ensuring fault tolerance and preventing single points of failure. A Proof-of-Execution mechanism verifies the integrity of the computation.
*   **Enhanced Oracle Integration:** Supports seamless integration with various Oracle solutions, allowing smart contracts to react to real-world data with minimal latency. Supports Chainlink, Band Protocol and custom oracle implementations via a standardized interface.
*   **Secure API Layer:** Provides a secure and reliable API for communication between on-chain smart contracts and off-chain workers. API requests are signed using cryptographic keys, preventing unauthorized access.
*   **Customizable Automation Strategies:** Allows developers to define custom automation strategies tailored to their specific needs. Strategies are defined as TypeScript modules and deployed to the off-chain worker network.
*   **EVM Compatibility:** Fully compatible with EVM-based blockchains, including Ethereum, Binance Smart Chain, and Polygon. Smart contracts are written in Solidity and deployed using standard development tools.
*   **Modular Architecture:** Designed with a modular architecture, allowing for easy extension and customization. New features and functionalities can be added without disrupting the core system.

## Technology Stack

*   **TypeScript:** Used for developing the off-chain worker logic and API layer, providing type safety and improved code maintainability.
*   **Solidity:** Used for writing the on-chain smart contracts that define the automation tasks and interact with the off-chain workers.
*   **Node.js:** Used for running the off-chain worker processes and hosting the API layer.
*   **Ethers.js/Web3.js:** Used for interacting with the EVM blockchain from both the on-chain smart contracts and the off-chain workers.
*   **Redis:** Used as a caching layer for frequently accessed data, improving performance and reducing latency.
*   **PostgreSQL:** Used as the main database to store automation jobs, execution results, and other relevant data.

## Installation

1.  **Clone the repository:**
    git clone https://github.com/jjfhwang/FutureChainPilot.git
    cd FutureChainPilot

2.  **Install dependencies:**
    npm install

3.  **Install Hardhat globally:**
    npm install --global hardhat

4.  **Compile smart contracts:**
    npx hardhat compile

5.  **Deploy smart contracts:**
    npx hardhat deploy --network <network_name> (e.g., npx hardhat deploy --network goerli)

6.  **Install dependencies for the off-chain worker:**
    cd worker
    npm install

## Configuration

1.  **Create a `.env` file in the root directory:**
    cp .env.example .env

2.  **Configure environment variables:**

    *   `PRIVATE_KEY`: The private key of the account used to interact with the smart contracts.
    *   `RPC_URL`: The RPC URL of the EVM blockchain.
    *   `CONTRACT_ADDRESS`: The address of the deployed smart contract.
    *   `ORACLE_ADDRESS`: The address of the deployed Oracle contract.
    *   `REDIS_HOST`: The host address of the Redis server.
    *   `REDIS_PORT`: The port number of the Redis server.
    *   `POSTGRES_HOST`: The host address of the PostgreSQL database.
    *   `POSTGRES_PORT`: The port number of the PostgreSQL database.
    *   `POSTGRES_USER`: The username for the PostgreSQL database.
    *   `POSTGRES_PASSWORD`: The password for the PostgreSQL database.
    *   `POSTGRES_DB`: The name of the PostgreSQL database.

3.  **Configure the off-chain worker in `worker/config.ts`:**
    Adjust settings such as the polling interval, gas limits, and Oracle update thresholds.

## Usage

1.  **Deploy a custom automation strategy:**
    Create a TypeScript module that implements the `IAutomationStrategy` interface. Deploy this module to the off-chain worker network using the provided CLI tools.

2.  **Register the strategy with the smart contract:**
    Call the `registerStrategy` function on the smart contract, providing the address of the deployed strategy and any necessary parameters.

3.  **Trigger automation tasks:**
    The off-chain workers will automatically monitor the blockchain for events that trigger the registered strategies. Once a trigger condition is met, the worker will execute the strategy and submit the results to the smart contract.

4. Example Solidity contract interaction:
 example
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.0;
    interface IAutomationContract {
        function registerStrategy(address _strategyAddress, bytes calldata _params) external;
        function executeStrategy(uint256 _executionId) external;
    }

Example TypeScript worker implementation

 interface IAutomationStrategy {
  execute(data: any): Promise;
 }

## Contributing

We welcome contributions to FutureChainPilot! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure that your code adheres to the project's coding style.
6.  Include unit tests for any new functionality.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/FutureChainPilot/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the following organizations and individuals for their contributions to the development of FutureChainPilot:

*   The Ethereum Foundation for their ongoing support of the Ethereum ecosystem.
*   The Chainlink team for their work on decentralized Oracle networks.
*   The Hardhat team for their excellent development tools.