# 0G Storage

## Overview

0G Storage is the storage layer for the ZeroGravity data availability (DA) system. The 0G Storage layer holds three important features:

* Built-in - It is natively built into the ZeroGravity DA system for data storage and retrieval.
* General purpose - It is designed to support atomic transactions, mutable key-value (kv) stores as well as archive log systems to enable wide range of applications with various data types.
* Incentive - Instead of being just a decentralized database, 0G Storage introduces PoRA mining algorithm to incentivize storage network participants.

To dive deep into the technical details, continue reading [0G Storage Spec.](docs/)

## Integration

We provide a [SDK](https://github.com/0glabs/0g-js-storage-sdk) for users to easily integrate 0G Storage in their applications with the following features:

* File Merkle Tree Class
* Flow Contract Types
* RPC methods support
* File upload
* Support browser environment
* Tests for different environments (in progress).
* File download (in progress)

## Deployment

Please refer to [Deployment](docs/run.md) page for detailed steps to compile and start a 0G Storage node.

## Test

### Prerequisites

* **Required Python Versions**: Python 3.8, 3.9, or 3.10 are supported. Versions above 3.10 may not be fully compatible (e.g., installation of `pysha3` may fail). Ensure that your Python version matches one of the supported versions.
* **Dependency Installation**: In the root directory, install the required dependencies by running:  
  ```bash
  pip3 install -r requirements.txt
  ```

### Dependencies

Python test framework will launch blockchain fullnodes at local for storage node to interact with. There are 2 kinds of fullnodes supported:

* Conflux eSpace node (by default).
* BSC node (geth).

For Conflux eSpace node, the test framework will automatically compile the binary at runtime, and copy the binary to `tests/tmp` folder. For BSC node, the test framework will automatically download the latest version binary from [github](https://github.com/bnb-chain/bsc/releases) to `tests/tmp` folder.

Alternatively, you can manually copy specific version binaries (conflux or geth) to the `tests/tmp` folder. Note, Do not copy the released Conflux binary from GitHub, since the block height of some CIPs is hardcoded.

Testing is also dependent on the following repositories:

* [0G Storage Contract](https://github.com/0glabs/0g-storage-contracts): It essentially provides two abi interfaces for 0G Storage Node to interact with the on-chain contracts.
  * ZgsFlow: It contains apis to submit chunk data.
  * PoraMine: It contains apis to submit PoRA answers.
* [0G Storage Client](https://github.com/0glabs/0g-storage-client): It is used to interact with certain 0G Storage Nodes to upload/download files.

### Run Tests

Go to the `tests` folder and run the following command to run all tests:

```
python test_all.py
```

or, run any single test, e.g.

```
python sync_test.py
```

## Contributing

To make contributions to the project, please follow the guidelines [here](contributing.md).
