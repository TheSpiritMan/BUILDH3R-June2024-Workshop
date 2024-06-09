# BUILDH3R_June_Avalanche

This is a proof of task for Avalanche.


## Task
- Deploy a subnet using the `avalanche-cli`. 
- [Option]: Can be done locally installing avalanche-cli or using github codespace. [Github repo Link](https://github.com/ava-labs/avalanche-starter-kit)
- I will be doing this locally in my VM.

## Setup VM
-  Install `avalanche-cli` locally. Below command will install cli.
    ```
    curl -sSfL https://raw.githubusercontent.com/ava-labs/avalanche-cli/main/scripts/install.sh | sh -s
    ```
- Install `cast` and `forge` using `cargo`. Make sure `rust` is pre-installed in the system:
    ```
    cargo install --git https://github.com/foundry-rs/foundry --profile local --locked forge cast chisel anvil
    ```
- Make sure all the binaries are added in PATH.

- Clone `avalanche-starter-kit`
    ```
    git clone https://github.com/ava-labs/avalanche-starter-kit.git && cd avalanche-starter-kit && git submodule update --init --recursive
    ```

## Perform Task:
- Setup ENV:
    ```
    export PK=56289e99c94b6912bfc12adc093c9b51124f0dc54ac7a766b2bc5ccf558d8027
    export KEYSTORE=${PWD}/keystore
    ```

- Create Avalanche Subnet:
    ```
    avalanche subnet create mysubnet
    ```
    Output:
    <details><summary> Detailed Output </summary><blockquote>

    ~~~
    vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ avalanche subnet create mysubnet
    ✔ Subnet-EVM
    ✔ Use latest release version
    ✔ Yes
    ✔ Yes
    creating genesis for subnet mysubnet
    Enter your subnet's ChainId. It can be any positive integer.
    ChainId: 979797
    Select a symbol for your subnet's native token
    ✔ Token symbol: TOK█
    ✔ Low disk use    / Low Throughput    1.5 mil gas/s (C-Chain's setting)
    ✔ Airdrop 1 million tokens to the default ewoq address (do not use in production)
    prefunding address 0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC with balance 1000000000000000000000000
    ✔ No
    ✓ Successfully created subnet configuration
    ~~~

    </blockquote></details>
    <img src=./Assets/create-subnet.png>

- Deploy Avalanche Subnet:
    ```
    avalanche subnet deploy mysubnet
    ```
    Output:
    <details><summary> Detailed Output </summary><blockquote>

    ~~~
    vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ avalanche subnet deploy mysubnet
    ✔ Local Network
    Deploying [mysubnet] to Local Network
    Backend controller started, pid: 75538, output at: /home/vagrant/.avalanche-cli/runs/server_20240609_115738/avalanche-cli-backend.log

    Booting Network. Wait until healthy...
    Node logs directory: /home/vagrant/.avalanche-cli/runs/network_20240609_115740/node<i>/logs
    Network ready to use.

    Deploying Blockchain. Wait until network acknowledges...

    Teleporter Messenger successfully deployed to c-chain (0x253b2784c75e510dD0fF1da844684a1aC0aa5fcf)
    Teleporter Registry successfully deployed to c-chain (0x17aB05351fC94a1a67Bf3f56DdbB941aE6c63E25)

    Teleporter Messenger successfully deployed to mysubnet (0x253b2784c75e510dD0fF1da844684a1aC0aa5fcf)
    Teleporter Registry successfully deployed to mysubnet (0xE3B5b719671F0E385C59F0ce0eED9507a060Df2d)

    using awm-relayer version (v1.3.2)
    Executing AWM-Relayer...

    Blockchain ready to use

    +-------------------+------------------------------------------------------------------------------------+
    |                                           mysubnet RPC URLs                                            |
    +-------------------+------------------------------------------------------------------------------------+
    | Localhost         | http://127.0.0.1:9650/ext/bc/mysubnet/rpc                                          |
    +                   +------------------------------------------------------------------------------------+
    |                   | http://127.0.0.1:9650/ext/bc/Tgm2oSMyHQ7RXS9hwGStvvpGdYA8JLAYs57woLHnsMbuNUHCZ/rpc |
    +-------------------+------------------------------------------------------------------------------------+

    +-------+------------------------------------------+-----------------------+
    |                                  Nodes                                   |
    +-------+------------------------------------------+-----------------------+
    | Name  | Node ID                                  | Localhost Endpoint    |
    +-------+------------------------------------------+-----------------------+
    | node1 | NodeID-7Xhw2mDxuDS44j42TCB6U5579esbSt3Lg | http://127.0.0.1:9650 |
    +-------+------------------------------------------+-----------------------+
    | node2 | NodeID-MFrZFVCXPv5iCn6M9K6XduxGTYp891xXZ | http://127.0.0.1:9652 |
    +-------+------------------------------------------+-----------------------+
    | node3 | NodeID-NFBbbJ4qCmNaCzeW7sxErhvWqvEQMnYcN | http://127.0.0.1:9654 |
    +-------+------------------------------------------+-----------------------+
    | node4 | NodeID-GWPcbFJZFfZreETSoWjPimr846mXEKCtu | http://127.0.0.1:9656 |
    +-------+------------------------------------------+-----------------------+
    | node5 | NodeID-P7oB2McjBGgW2NXXWVYjV8JEDFoW9xDE5 | http://127.0.0.1:9658 |
    +-------+------------------------------------------+-----------------------+

    Browser Extension connection details (any node URL from above works):
    RPC URL:           http://127.0.0.1:9650/ext/bc/Tgm2oSMyHQ7RXS9hwGStvvpGdYA8JLAYs57woLHnsMbuNUHCZ/rpc
    Funded address:    0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC with 1000000 (10^18) - private key: 56289e99c94b6912bfc12adc093c9b51124f0dc54ac7a766b2bc5ccf558d8027
    Funded address:    0x499e4dA3872e532dd1d2A1688177C122931e7e9f with 600 (10^18)
    Network name:      mysubnet
    Chain ID:          979797
    Currency Symbol:   TOK

    ~~~

    </blockquote></details>

    <img src=./Assets/deploy-subnet.png>

- Describe Avalanche Subnet:
    ```
    avalanche subnet describe mysubnet
    ```
    Output:
    <details><summary> Detailed Output </summary><blockquote>

    ~~~
    vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ avalanche subnet describe mysubnet

     _____       _        _ _                                                                                                                                                                                                                                                     
    |  __ \     | |      (_) |                                                                                                                                                                                                                                                    
    | |  | | ___| |_ __ _ _| |___                                                                                                                                                                                                                                                 
    | |  | |/ _ \ __/ _  | | / __|                                                                                                                                                                                                                                                
    | |__| |  __/ || (_| | | \__ \                                                                                                                                                                                                                                                
    |_____/ \___|\__\__,_|_|_|___/                                                                                                                                                                                                                                                
    +--------------------------------+------------------------------------------------------------------------------------+                                                                                                                                                       
    |           PARAMETER            |                                       VALUE                                        |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Subnet Name                    | mysubnet                                                                           |
    +--------------------------------+------------------------------------------------------------------------------------+
    | ChainID                        | 979797                                                                             |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Token Name                     | TOK Token                                                                          |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Token Symbol                   | TOK                                                                                |
    +--------------------------------+------------------------------------------------------------------------------------+
    | VM Version                     | v0.6.5                                                                             |
    +--------------------------------+------------------------------------------------------------------------------------+
    | VM ID                          | qDNsVQJfGpi2RfCcESbeZauGqPVjtXwoopVMtrGkdoUxmFKov                                  |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Local Network SubnetID         | 26eqgD4Kt1MvTKXC9BDjEwBAfhcBcHCKj2EXjR2UuFpSWoAHhw                                 |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Local Network RPC URL          | http://127.0.0.1:9650/ext/bc/Tgm2oSMyHQ7RXS9hwGStvvpGdYA8JLAYs57woLHnsMbuNUHCZ/rpc |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Local Network BlockchainID     | Tgm2oSMyHQ7RXS9hwGStvvpGdYA8JLAYs57woLHnsMbuNUHCZ                                  |
    | (CB58)                         |                                                                                    |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Local Network BlockchainID     | 0x3c97bb14a422abc1646a38c9879171266f727a9447cd7ed412f836430527d05d                 |
    | (HEX)                          |                                                                                    |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Local Network Teleporter       | 0x253b2784c75e510dD0fF1da844684a1aC0aa5fcf                                         |
    | Messenger Address              |                                                                                    |
    +--------------------------------+------------------------------------------------------------------------------------+
    | Local Network Teleporter       | 0xE3B5b719671F0E385C59F0ce0eED9507a060Df2d                                         |
    | Registry Address               |                                                                                    |
    +--------------------------------+------------------------------------------------------------------------------------+

      _____              _____             __ _                                                                                                                                                                                                                                   
     / ____|            / ____|           / _(_)                                                                                                                                                                                                                                  
    | |  __  __ _ ___  | |     ___  _ __ | |_ _  __ _                                                                                                                                                                                                                             
    | | |_ |/ _  / __| | |    / _ \| '_ \|  _| |/ _  |                                                                                                                                                                                                                            
    | |__| | (_| \__ \ | |___| (_) | | | | | | | (_| |                                                                                                                                                                                                                            
     \_____|\__,_|___/  \_____\___/|_| |_|_| |_|\__, |                                                                                                                                                                                                                            
                                                 __/ |                                                                                                                                                                                                                            
                                                |___/                                                                                                                                                                                                                             
    +--------------------------+-------------+                                                                                                                                                                                                                                    
    |      GAS PARAMETER       |    VALUE    |
    +--------------------------+-------------+
    | GasLimit                 |     8000000 |
    +--------------------------+-------------+
    | MinBaseFee               | 25000000000 |
    +--------------------------+-------------+
    | TargetGas (per 10s)      |    15000000 |
    +--------------------------+-------------+
    | BaseFeeChangeDenominator |          36 |
    +--------------------------+-------------+
    | MinBlockGasCost          |           0 |
    +--------------------------+-------------+
    | MaxBlockGasCost          |     1000000 |
    +--------------------------+-------------+
    | TargetBlockRate          |           2 |
    +--------------------------+-------------+
    | BlockGasCostStep         |      200000 |
    +--------------------------+-------------+

              _         _                                                                                                                                                                                                                                                         
        /\   (_)       | |                                                                                                                                                                                                                                                        
       /  \   _ _ __ __| |_ __ ___  _ __                                                                                                                                                                                                                                          
      / /\ \ | | '__/ _  | '__/ _ \| '_ \                                                                                                                                                                                                                                         
     / ____ \| | | | (_| | | | (_) | |_) |                                                                                                                                                                                                                                        
    /_/    \_\_|_|  \__,_|_|  \___/| .__/                                                                                                                                                                                                                                         
                                   | |                                                                                                                                                                                                                                            
                                   |_|                                                                                                                                                                                                                                            
    +--------------------------------+--------------------------------------------+------------------------+---------------------------+------------------------------------------------------------------+                                                                       
    |          DESCRIPTION           |                  ADDRESS                   | AIRDROP AMOUNT (10^18) |   AIRDROP AMOUNT (WEI)    |                           PRIVATE KEY                            |
    +--------------------------------+--------------------------------------------+------------------------+---------------------------+------------------------------------------------------------------+
    | Main funded account EWOQ       | 0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC |                1000000 | 1000000000000000000000000 | 56289e99c94b6912bfc12adc093c9b51124f0dc54ac7a766b2bc5ccf558d8027 |
    +--------------------------------+--------------------------------------------+------------------------+---------------------------+------------------------------------------------------------------+
    | Teleporter deploys             | 0x499e4dA3872e532dd1d2A1688177C122931e7e9f |                    600 |     600000000000000000000 | 4df4e48b0c947b770b06160a59b2b8c0c7547b7d57fdb46f720c915650ca0eb4 |
    | cli-teleporter-deployer        |                                            |                        |                           |                                                                  |
    +--------------------------------+--------------------------------------------+------------------------+---------------------------+------------------------------------------------------------------+


      _____                                    _ _                                                                                                                                                                                                                                
     |  __ \                                  (_) |                                                                                                                                                                                                                               
     | |__) | __ ___  ___ ___  _ __ ___  _ __  _| | ___  ___                                                                                                                                                                                                                      
     |  ___/ '__/ _ \/ __/ _ \| '_   _ \| '_ \| | |/ _ \/ __|                                                                                                                                                                                                                     
     | |   | | |  __/ (_| (_) | | | | | | |_) | | |  __/\__ \                                                                                                                                                                                                                     
     |_|   |_|  \___|\___\___/|_| |_| |_| .__/|_|_|\___||___/                                                                                                                                                                                                                     
                                        | |                                                                                                                                                                                                                                       
                                        |_|                                                                                                                                                                                                                                       

    +------------+-----------------+-------------------+                                                                                                                                                                                                                          
    | PRECOMPILE | ADMIN ADDRESSES | ENABLED ADDRESSES |
    +------------+-----------------+-------------------+
    | Warp       | n/a             | n/a               |
    +------------+-----------------+-------------------+


    ~~~

    </blockquote></details>

    <img src=./Assets/describe-subnet.png>

- Modify `Blockchain-ID`:
    - Copy value of `Local Network BlockchainID(HEX)` from above output.
    - Replace with `destinationBlockchainID:` of `src/0-send-receive/senderOnCChain.sol` file in line No. `20`. 

- Deploy Contracts:
    - Deploy sender contract:
        ```
        forge create --rpc-url local-c --private-key $PK src/0-send-receive/senderOnCChain.sol:SenderOnCChain
        ```
        Output:
        <details><summary> Detailed Output </summary><blockquote>

        ~~~
        vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ forge create --rpc-url local-c --private-key $PK src/0-send-receive/senderOnCChain.sol:SenderOnCChain
        [⠊] Compiling...
        [⠒] Compiling 2 files with Solc 0.8.18
        [⠢] Solc 0.8.18 finished in 71.19ms
        Compiler run successful!
        Deployer: 0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC
        Deployed to: 0x5DB9A7629912EBF95876228C24A848de0bfB43A9
        Transaction hash: 0x4394a0c0622757c15047f421612083459465bde882d87935842a14262acab44c
        ~~~

        </blockquote></details>
        <img src=./Assets/sender-contract.png>

    - Deploy receiver contract:
        ```
        forge create --rpc-url mysubnet --private-key $PK src/0-send-receive/receiverOnSubnet.sol:ReceiverOnSubnet
        ```
        Output:
        <details><summary> Detailed Output </summary><blockquote>

        ~~~
        vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ forge create --rpc-url mysubnet --private-key $PK src/0-send-receive/receiverOnSubnet.sol:ReceiverOnSubnet
        [⠊] Compiling...
        [⠒] Compiling 2 files with Solc 0.8.18
        [⠢] Solc 0.8.18 finished in 75.72ms
        Compiler run successful!
        Deployer: 0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC
        Deployed to: 0x52C84043CD9c865236f11d9Fc9F56aa003c1f922
        Transaction hash: 0x995dcf48a49d54597571b0167b92a95028d75c6fec5f8e133b693be3df73fd30

        ~~~

        </blockquote></details>
        <img src=./Assets/receiver-contract.png>

- Sending Message:
    - Code snippet
        ```
        cast send --rpc-url local-c --private-key $PK <sender_contract_address> "sendMessage(address,string)" <receiver_contract_address> "Hello"
        ```
    - Replace `<sender_contract_address>` and `<receiver_contract_address>` with the actual value from above output. In my case:
        - sender_contract_address: `0x5DB9A7629912EBF95876228C24A848de0bfB43A9`
        - receiver_contract_address: `0x52C84043CD9c865236f11d9Fc9F56aa003c1f922`
    
    - Sending the message in blockchain:
        ```
        cast send --rpc-url local-c --private-key $PK 0x5DB9A7629912EBF95876228C24A848de0bfB43A9  "sendMessage(address,string)" 0x52C84043CD9c865236f11d9Fc9F56aa003c1f922 "Hello Avalanche Lab Practioner"
        ```
        Output:
        <details><summary> Detailed Output </summary><blockquote>

        ~~~
        vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ cast send --rpc-url local-c --private-key $PK 0x5DB9A7629912EBF95876228C24A848de0bfB43A9  "sendMessage(address,string)" 0x52C84043CD9c865236f11d9Fc9F56aa003c1f922 "Hello Avalanche Lab Practioner"

        blockHash               0x1f57ab1bf0c7f3260562474b4f112bb9755d0be40610eea9110b6b56927f0e9c
        blockNumber             6
        contractAddress         
        cumulativeGasUsed       170313
        effectiveGasPrice       2306241250000
        from                    0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC
        gasUsed                 170313
        logs                    [{"address":"0x253b2784c75e510dd0ff1da844684a1ac0aa5fcf","topics":["0x1eac640109dc937d2a9f42735a05f794b39a5e3759d681951d671aabbce4b104","0x55e1fcfdde01f9f6d4c16fa2ed89ce65a8669120a86f321eef121891cab61241"],"data":"0x","blockHash":"0x1f57ab1bf0c7f3260562474b4f112bb9755d0be40610eea9110b6b56927f0e9c","blockNumber":"0x6","transactionHash":"0x26d1364d74b2df04a367ff3ee8d6e91fc0c51f4fe7e7e2339ec405cdaf4f38dd","transactionIndex":"0x0","logIndex":"0x0","removed":false},{"address":"0x253b2784c75e510dd0ff1da844684a1ac0aa5fcf","topics":["0x2a211ad4a59ab9d003852404f9c57c690704ee755f3c79d2c2812ad32da99df8","0xe064b99223866c40c850d1337a9aebbd79cdda62acb5746384c9e6acc5aeded8","0x3c97bb14a422abc1646a38c9879171266f727a9447cd7ed412f836430527d05d"],"data":"0x00000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000005db9a7629912ebf95876228c24a848de0bfb43a93c97bb14a422abc1646a38c9879171266f727a9447cd7ed412f836430527d05d00000000000000000000000052c84043cd9c865236f11d9fc9f56aa003c1f92200000000000000000000000000000000000000000000000000000000000186a00000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000012000000000000000000000000000000000000000000000000000000000000001400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000001e48656c6c6f204176616c616e636865204c6162205072616374696f6e65720000","blockHash":"0x1f57ab1bf0c7f3260562474b4f112bb9755d0be40610eea9110b6b56927f0e9c","blockNumber":"0x6","transactionHash":"0x26d1364d74b2df04a367ff3ee8d6e91fc0c51f4fe7e7e2339ec405cdaf4f38dd","transactionIndex":"0x0","logIndex":"0x1","removed":false},{"address":"0x0200000000000000000000000000000000000005","topics":["0x56600c567728a800c0aa927500f831cb451df66a7af570eb4df4dfbf4674887d","0x000000000000000000000000253b2784c75e510dd0ff1da844684a1ac0aa5fcf","0x0c99a35d3e18281a05a5dc733f04bd4f1f0e159b0bd4cec3f1663178317d392f"],"data":"0x0000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000022c00000000053955e1fcfdde01f9f6d4c16fa2ed89ce65a8669120a86f321eef121891cab612410000020200000000000100000014253b2784c75e510dd0ff1da844684a1ac0aa5fcf000001e0000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000010000000000000000000000005db9a7629912ebf95876228c24a848de0bfb43a93c97bb14a422abc1646a38c9879171266f727a9447cd7ed412f836430527d05d00000000000000000000000052c84043cd9c865236f11d9fc9f56aa003c1f92200000000000000000000000000000000000000000000000000000000000186a00000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000012000000000000000000000000000000000000000000000000000000000000001400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000001e48656c6c6f204176616c616e636865204c6162205072616374696f6e657200000000000000000000000000000000000000000000","blockHash":"0x1f57ab1bf0c7f3260562474b4f112bb9755d0be40610eea9110b6b56927f0e9c","blockNumber":"0x6","transactionHash":"0x26d1364d74b2df04a367ff3ee8d6e91fc0c51f4fe7e7e2339ec405cdaf4f38dd","transactionIndex":"0x0","logIndex":"0x2","removed":false}]
        logsBloom               0x01000000000000800000000000001000000000000000000000000000000000000000000080000010000010000000000000000000000000000000000000000008000000000100000000000000000000000000000000000000000000000000001600000000000000000004000000000000000400000000000000000000000000000000000000000000000041000000000000000000020000000000000000020000040000000000000000000100000800000000000000000000000000000000000000400001008000010000040000000400000000000000000000001000000000000000000200000000000000000004000000000000000000000000008000000000
        root                    
        status                  1 (success)
        transactionHash         0x26d1364d74b2df04a367ff3ee8d6e91fc0c51f4fe7e7e2339ec405cdaf4f38dd
        transactionIndex        0
        type                    2
        blobGasPrice            
        blobGasUsed             
        to                      0x5DB9A7629912EBF95876228C24A848de0bfB43A9
        ~~~

        </blockquote></details>
        <img src=./Assets/message-sending.png>
    
    - Here I have sent `Hello Avalanche Lab Practioner` as a message.

- Sending the message in blockchain:
    - Code snippet
        ```
        cast call --rpc-url mysubnet <receiver_contract_address> "lastMessage()(string)"
        ```
    - Replace `<receiver_contract_address>` with the actual value from above output. In my case:
        - receiver_contract_address: `0x52C84043CD9c865236f11d9Fc9F56aa003c1f922`
    - Verifying the message in blockchain:
        ```
        cast call --rpc-url mysubnet 0x52C84043CD9c865236f11d9Fc9F56aa003c1f922 "lastMessage()(string)"
        ```
        Output:
        <details><summary> Detailed Output </summary><blockquote>

        ~~~
        vagrant@Luma-Workshop:~/Projects/Avalanche-Labs/avalanche-starter-kit$ cast call --rpc-url mysubnet 0x52C84043CD9c865236f11d9Fc9F56aa003c1f922 "lastMessage()(string)"
        "Hello Avalanche Lab Practioner"
        ~~~

        </blockquote></details>
        <img src=./Assets/message-verifying.png>

### Clean-Up
- Destroy Network:
    ```
    avalanche network clean
    ```
- Delete Subnet, here `mysubnet` is a name of subnet:
    ```
    avalanche subnet delete mysubnet
    ```

## Conclusion:
- This task is completed. 
- Here, We have:
    - Created and deployed Avalanche subnet using Avalanche-CLI.
    - Send and receive Message using that subnet.


