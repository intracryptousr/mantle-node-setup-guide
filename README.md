# Deploying a Rollup Verifier/Replica Node
Deploy a verifier node and sync rollup data as a part of Mantle network
In order to build an app on Mantle network, you'll need access to a Mantle node. There are multiple public [Node RPC Providers](https://docs.mantle.xyz/network/for-devs/resources-and-tooling/node-rpc-providers) that you can choose from, or you can deploy your own depending on the requirements for your specific use cases.

## Running Your Own Node
> If you run a node, please keep a close eye on the latest update on [GitHub Release](https://github.com/mantlenetworkio/mantle/releases) page

### Hardware Requirements
Nodes need to store the transaction history of Mantle and to run l2geth. Recommended specs:
- **CPU** - min. 4 cores, 8th Gen. or higher
- **RAM** - min. 16 GB
- **Storage** - min. 100 GB disk space free (HDD works for now, SSD is better)
- **Bandwidth** - 10mb/s+ download
### Approximate Disk Usage
Usage as of 2022-09-21:
- **Archive node:** ~800gb
- **Full node:** ~60gb

### 1. Deploy a Node With Docker
They include all the configuration settings. We use these images for our own systems, and as such they will be more thoroughly tested than any other configuration.
**Node Configuration**
You can find instructions to build and operate your node on Mantle testnet and mainnet by following the links below:
- [Testnet node](https://github.com/mantlenetworkio/networks/blob/main/run-node.md)
- [Mainnet node](https://github.com/mantlenetworkio/networks/blob/main/run-node-mainnet.md)

### 2. Deploy a Node from Binary
To compile a Mantle node locally and participate in the network as a Verifier, follow these steps:
1. Install Go and C Compiler
Make sure Go (version 1.10 or higher) and a C compiler are installed on your system. You can use your preferred package manager (e.g., apt, yum, brew) to install them.
2. Clone the Mantle Repository
Clone the Mantle GitHub repository using the following command:
```
git clone https://github.com/mantlenetworkio/mantle.git
```
### 3. Navigate to the l2geth Directory
Navigate to the l2geth directory within the Mantle repository:
```
cd mantle/l2geth
```
### 4. Compile the Mantle Geth Node
Compile the Mantle Geth node using the Makefile with the following command:
```
make geth
```
### 5. Start as a Verifier
Start the node as a Verifier to join the Mantle network:
```
./build/bin/geth --rollup.verifier
```
This command launches a local node configured as a Verifier to participate in the validation process within the Mantle network.

### Appendix
**Network DTL URL**
You can change the DTL service URL based on the network your node is going to connect to by updating the `ROLLUP_CLIENT_HTTP` value in the `docker-compose.yml` file.
