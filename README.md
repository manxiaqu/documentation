# 🚀 Quickstart

This quick start guide will help developers get started with deploying smart contracts onto the COTI network. If you are already familiar with Ethereum, EVM-related technologies, smart contracts and web3, follow the steps below to get started.

You should already be familiar with concepts such as **Ethereum**, **EVM**, and **Smart Contracts**.

If you are new to Ethereum and smart contracts, get familiar with these topics by following these introductory guides:

* [Introduction to Ethereum](https://ethereum.org/en/developers/docs/intro-to-ethereum/)
* [Introduction to Smart Contracts](https://ethereum.org/en/developers/docs/smart-contracts/)
* [Ethereum Virtual Machine (EVM)](https://ethereum.org/en/developers/docs/evm/)

{% hint style="info" %}
For questions & support [**join our Discord**](https://discord.com/invite/wfAQfbc3Df)!
{% endhint %}

If you want to get familiar with COTI and the wider privacy topic, get started with the [**Introduction**](<README (1).md>) section.

## Native Transfer

The following process will help you deploy the [**`native_transfer.py`**](https://github.com/coti-io/coti-sdk-python/blob/main/examples/basics/native\_transfer.py) example from the [COTI Python SDK](https://github.com/coti-io/coti-sdk-python/tree/main). This script will transfer native funds from your wallet account to a random wallet. It will also:

* Create an account
* Create an EOA private key for execution
* Validate minimum balance

{% hint style="info" %}
Ensure your environment meets all the pre-requisites. Visit the [pre-requisites section of the readme](https://github.com/coti-io/coti-sdk-python/tree/main?tab=readme-ov-file#python-sdk-coti-sdk-python---usage). Alternatively, use an editor like [PyCharm](https://www.jetbrains.com/pycharm/download/), which will take care of the pre-requisites for you.
{% endhint %}

1.  Clone the Python SDK along with its submodules into your desired location

    ```bash
    git clone --recurse-submodules git@github.com:coti-io/coti-sdk-python.git
    ```


2.  Change directory to the newly create one

    ```bash
    cd coti-sdk-python.git
    ```


3.  Install the project's requirements

    ```bash
    python3 -m pip install -r requirements.txt
    ```


4.  Run the `native_transfer.py` script

    ```bash
    python3 examples/basics/native_transfer.py
    ```

    \
    Running the script will automatically create an account and an `ACCOUNT_PRIVATE_KEY` (visible in the `.env` file). The script output will look something like this:



    ```bash
    So you dont have an account yet, dont worry... lets create one right now!
    Creation done!
    provider:  https://devnet.coti.io
    chain-id:  13068200
    latest block:  0xc9ec7259bad015c46a0bef9b0988cac70a62e2abaed7459b5265e425bc5cecb8
    account address: 0x0287a7A5bD5f4802D4A6048730a11B2713A16bd4
    account balance:  0 wei ( 0  ether)
    account nonce:  0
    Traceback (most recent call last):
      File "/Users/user/projects/coti-sdk-python/examples/basics/native_transfer.py", line 24, in <module>
        main()
      File "/Users/user/projects/coti-sdk-python/examples/basics/native_transfer.py", line 12, in main
        validate_minimum_balance(web3)  # validate minimum balance
      File "/Users/user/projects/coti-sdk-python/examples/basics/utils.py", line 69, in validate_minimum_balance
        raise Exception(
    Exception: Not enough balance!, head to discord faucet and getsome...https://discord.com/channels/386571547508473876/1235539223595978752 , ask the BOT:devnet 0x0287a7A5bD5f4802D4A6048730a11B2713A16bd4

    Process finished with exit code 1

    ```

    \
    It is normal to receive the exception `Not enough balance!` on first run. This will be resolved once the account is funded.\

5. Head to the faucet at [**https://faucet.coti.io**](https://faucet.coti.io) to get devnet funds. Send the following message to the bot using your newly created `account address`:\
   \
   `devnet <your_eoa_address>`\
   \
   The bot will reply with the message:\
   \
   `<username> faucet transferred 5 COTIv2 (devnet)` \

6.  Run the `native_transfer.py` script once more

    ```bash
    python3 examples/basics/native_transfer.py
    ```

    \
    The output will be as follows:

    ```bash
    /Users/user/projects/coti-sdk-python/venv/bin/python /Users/user/projects/coti-sdk-python/examples/basics/native_transfer.py 
    provider:  https://devnet.coti.io
    chain-id:  13068200
    latest block:  0x4f5b68d9ef7debc0f86b4fc4c50a81020c8de315d65b4ce12b4372ebedef4f95
    account address: 0x0287a7A5bD5f4802D4A6048730a11B2713A16bd4
    account balance:  10000000000000000000 wei ( 10  ether)
    account nonce:  0
    AttributeDict({'blockHash': HexBytes('0x3e0534655361da10c9ee6454d622609c900e3f552435acc9cc963e370ca1d36b'), 'blockNumber': 3395902, 'contractAddress': None, 'cumulativeGasUsed': 21000, 'effectiveGasPrice': 1000000000, 'from': '0x0287a7A5bD5f4802D4A6048730a11B2713A16bd4', 'gasUsed': 21000, 'logs': [], 'logsBloom': HexBytes('0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'), 'status': 1, 'to': '0x4A68774D7679e63Ea42599Fe076a899036B3642B', 'transactionHash': HexBytes('0x99ad02f33a146945ac3a671857ab5134965b1f3e78fd53a97710bcdcb99dfee7'), 'transactionIndex': 0, 'type': 0})

    Process finished with exit code 0
    ```

    \
    Now that your account is created and funded, we can now onboard the account to get our new network key.

## On-board Account

The following process will help you deploy the [**`onboard_account.py`**](https://github.com/coti-io/coti-sdk-python/blob/main/examples/onboard/onboard\_account.py) example from the [COTI Python SDK](https://github.com/coti-io/coti-sdk-python/tree/main). This script onboards an EOA into the network. It will also:

{% hint style="info" %}
asdf
{% endhint %}

* Create an AES key unique for the user
* Use the AES key to encrypt all data sent back to the wallet

This is a mandatory script for any operation executed in a contract that requires encrypt/decrypt actions.

1.  Run the `onboard_account.py` script

    ```bash
    python3 examples/onboard/onboard_account.py
    ```

    \
    Running the script will automatically create an account and an `ACCOUNT_ENCRYPTION_KEY` (visible in the `.env` file as well as the output). The script output will look something like this:\


    ```bash
    /Users/user/projects/coti-sdk-python/venv/bin/python /Users/user/projects/coti-sdk-python/examples/onboard/onboard_account.py 
    provider:  https://devnet.coti.io
    chain-id:  13068200
    latest block:  0x31f5e889a74777e514abcf83ece21839d96c465419b66b6b977f65d052062c2a
    account address: 0x0287a7A5bD5f4802D4A6048730a11B2713A16bd4
    account balance:  9999936985000000000 wei ( 9.999936985  ether)
    account nonce:  3
    tx receipt:  AttributeDict({'blockHash': HexBytes('0x94dac5f2cf57639fe934457cb33354399567cfad233c2fb3d6a271ecd47830a3'), 'blockNumber': 3399673, 'contractAddress': None, 'cumulativeGasUsed': 225968, 'effectiveGasPrice': 30000000000, 'from': '0x0287a7A5bD5f4802D4A6048730a11B2713A16bd4', 'gasUsed': 225968, 'logs': [AttributeDict({'address': '0xbFC922C10B03EA5dbC90b98dfc8fb334849ccB78', 'topics': [HexBytes('0xb67504ecfeef0230a06f661ea388c2947b4125a35e918ebff5889e3553c29c04'), HexBytes('0x0000000000000000000000000287a7a5bd5f4802d4a6048730a11b2713a16bd4')], 'data': HexBytes('0x00000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000000100702c1a6221b95f4730a6ff7e7e96d4362d75558386340a381714a64ac40cb4100e5e27e5f9606fbc5e89b2064062d15d4a7ad671428ac128eb76eaed7534f36e0829fb4e4cf090db7ae6e1ba3728e6870fe29617c80ec1d0fcfd5c5b39eec6b7252e2d0a1e8f89cf786d9abd288c74e2cad8006f8c8065e6f3ff73bf164d2d9a0e708f26ff938890ea7191655ef6f0a5ffe9acaddaf9f614b2ecc9faf86cfc041b6704cc4865429b069c0fbc02b83ecc5c45f54501542de2c08b85d7c2a88370503c5d7f04ca6e7b0fffeb89dc7b3c8e5834943e93899bab6bc0ac9ce58e8d59247ab8dd7c096c1fe5e65f48a5c3fb6e85e2a6d43f829ebc5da0c75740df33fd'), 'blockNumber': 3399673, 'transactionHash': HexBytes('0x69af701a8f65ebf6c007e512ce6bc5e801884c3ae49ad744f47069053e2ed81e'), 'transactionIndex': 0, 'blockHash': HexBytes('0x94dac5f2cf57639fe934457cb33354399567cfad233c2fb3d6a271ecd47830a3'), 'logIndex': 0, 'removed': False})], 'logsBloom': HexBytes('0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000400000000000000000000001000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000008000000000000000000000000000000000440000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000040000000000000000000000000000000'), 'status': 1, 'to': '0xbFC922C10B03EA5dbC90b98dfc8fb334849ccB78', 'transactionHash': HexBytes('0x69af701a8f65ebf6c007e512ce6bc5e801884c3ae49ad744f47069053e2ed81e'), 'transactionIndex': 0, 'type': 0})
    (True, 'ACCOUNT_ENCRYPTION_KEY', 'fd3d781ddcbd1e1cedd2d75460f30636')

    Process finished with exit code 0
    ```



    {% hint style="info" %}
    This encryption key is **sensitive.** Ensure it is not uploaded to public places and keep it safe. This key is prodiced per EOA wallet, meaning a unique wallet/EOA will have a unique encryption key.
    {% endhint %}

    \
    The `.env` file will also have other useful information, such as the node address, websocket address, and the contract directories.\
    \
    Now that the account is onboarded, let's deploy a contract on-chain.

## Deploy Data On-Chain

The following process will help you deploy the [**`DataOnChain.sol`**](https://github.com/coti-io/confidentiality-contracts/blob/main/contracts/examples/DataOnChain.sol) example from the [**confidentiality-contracts**](https://github.com/coti-io/confidentiality-contracts/) repo, which is imported as a git submodule in the Python SDK. This contract can be used in order to browse and get a feel for the COTI network. This contract should be run at the root of `confidentiality-contracts` directory. If using an editor, set it as your working directory.

1.
