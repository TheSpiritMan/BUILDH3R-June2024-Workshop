# BUILDH3R_June_AlphaSwap

This is a proof of task for AlphaSwap.


## Task
- Complete a private swap transaction with `snarkos` command line.
- I will be doing this locally in my VM.

## Setup VM
-  Install `rust` locally. Below command will install cli. [More deatils](https://www.rust-lang.org/tools/install)
    ```
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```
- Install SnarkOS. [More Details](https://github.com/ProvableHQ/snarkOS):
    ```
    git clone https://github.com/AleoHQ/snarkOS.git --depth 1
    cd snarkOS
    ./build_ubuntu.sh
    cargo install --locked --path .
    ```
- Install SnarkVM. [More Details](https://github.com/ProvableHQ/snarkVM):
    ```
    cargo install snarkvm
    ```

- Make sure all the binaries are added in PATH.


## Perform Task:
- Create Snark Account:
    ```
    snarkos account new
    ```
    Output:
    <details><summary> Detailed Output </summary><blockquote>
    
    ~~~
    vagrant@Luma-Workshop:~/Projects/AlphaSwap-Zenox/Task$ snarkos account new
    Private Key  APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6
        View Key  AViewKey1ueEqKhmPNV7d3pfo4GwCiPjiCoBmrBS4PJRm9n5bzbsY
        Address  aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa
    ~~~
    </blockquote></details>
    <img src=./Assets/snarkos-account-creation.png>

- Claim Aleo testnet Credits. Visit [https://faucetbeta.sotertech.io/](https://faucetbeta.sotertech.io/) to claim Aleo Testnet Credits. I have submitted requested [https://testnetbeta.aleo123.io/address/aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa](https://testnetbeta.aleo123.io/address/aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa).
    

- Claim AlphaSwap Testnet USDT Token:
    - Code Snippet:
        ```
        snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "your own private key" token_faucet_v1.aleo claim 5527204198704484578620591539455109020124318183905545955577744208298624522139field 10000000u128
        ```
    - In my case, `private key` is `APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6`
    - Command:
        ```
        snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6" token_faucet_v1.aleo claim 5527204198704484578620591539455109020124318183905545955577744208298624522139field 10000000u128
        ```

        Output:
        <details><summary> Detailed Output </summary><blockquote>
        
        ~~~
        vagrant@Luma-Workshop:~/Projects/AlphaSwap-Zenox/Setup/snarkOS$ snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6" token_faucet_v1.aleo claim 5527204198704484578620591539455109020124318183905545955577744208298624522139field 10000000u128

        📦 Creating execution transaction for 'token_faucet_v1.aleo/claim'...


        ⚠  "powers-of-beta-17.usrs.7c27308" does not exist. Downloading and storing it (in "/home/vagrant/.aleo/resources/powers-of-beta-17.usrs.7c27308").

        Installation - Downloading "https://s3-us-west-1.amazonaws.com/mainnet.parameters/powers-of-beta-17.usrs.7c27308"
        Installation - 100.00% complete (6 MB total)   Installation - Storing file in "/home/vagrant/.aleo/resources/powers-of-beta-17.usrs.7c27308"

        ⚠  "shifted-powers-of-beta-17.usrs.2025178" does not exist. Downloading and storing it (in "/home/vagrant/.aleo/resources/shifted-powers-of-beta-17.usrs.2025178").

        Installation - Downloading "https://s3-us-west-1.amazonaws.com/mainnet.parameters/shifted-powers-of-beta-17.usrs.2025178"
        Installation - 100.00% complete (6 MB total)   Installation - Storing file in "/home/vagrant/.aleo/resources/shifted-powers-of-beta-17.usrs.2025178"
        ✅ Created execution transaction for 'token_faucet_v1.aleo/claim'
        ⌛ Execution at17euheq5zpyz4am6f9cpe2dcvttczphpjhqdw65u3dqgryv664ugsnuf82t ('token_faucet_v1.aleo/claim') has been broadcast to https://api.explorer.aleo.org/v1/testnet/transaction/broadcast.
        at17euheq5zpyz4am6f9cpe2dcvttczphpjhqdw65u3dqgryv664ugsnuf82t
        ~~~
        </blockquote></details>
        <img src=./Assets/claim-alphaswap-testnet-USDT-token.png>

- Convert Public USDT to Private USDT:
    - Code Snippet:
        ```
        snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "your own private key" alphaswap_v1.aleo transfer_public_to_private 5527204198704484578620591539455109020124318183905545955577744208298624522139field "your own address" 1000000u128
        ```
    
    - In my case, `private key` is `APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6` and `address` is `aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa`.
    - Command: 
        ```
        snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6" alphaswap_v1.aleo transfer_public_to_private 5527204198704484578620591539455109020124318183905545955577744208298624522139field "aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa" 1000000u128
        ```

        Output:
        <details><summary> Detailed Output </summary><blockquote>
        
        ~~~
        vagrant@Luma-Workshop:~/Projects/AlphaSwap-Zenox/Task$ snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6" alphaswap_v1.aleo transfer_public_to_private 5527204198704484578620591539455109020124318183905545955577744208298624522139field "aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa" 1000000u128

        📦 Creating execution transaction for 'alphaswap_v1.aleo/transfer_public_to_private'...

        ✅ Created execution transaction for 'alphaswap_v1.aleo/transfer_public_to_private'
        ⌛ Execution at169rvr2fpf8t60dxqumn5czzwrxwxy9zaarqawy8n0sagx6rpvs8sl06wmc ('alphaswap_v1.aleo/transfer_public_to_private') has been broadcast to https://api.explorer.aleo.org/v1/testnet/transaction/broadcast.
        at169rvr2fpf8t60dxqumn5czzwrxwxy9zaarqawy8n0sagx6rpvs8sl06wmc
        ~~~
        </blockquote></details>
        <img src=./Assets/convert-public-to-private-USDT.png>
    
    - From above output, transaction ID: `at169rvr2fpf8t60dxqumn5czzwrxwxy9zaarqawy8n0sagx6rpvs8sl06wmc`

- Get the private output record by Tx ID:
    - Visit: [https://explorer.aleo.org](https://explorer.aleo.org)
    - Search by above transcation ID.
    - Below output can be seen:
    
        <img src=./Assets/tx-on-explorer.png>

    - In my case, output record: 
        <!-- <details><summary> Detailed Output </summary><blockquote>

        ~~~
        record1qyqspfj735jzmfecuc58v7l4gwj4y8a0x4h7uyhw2s0ygjn9n6k3sjqwqgzhgmmtv4hyxqqzqgq0lxf369xkejpqla66j0y2gakgq6k6gdqtspaml0vzzr35a608yrf2499852x83zwpjtcdprhj8kc4c254mty45edjld4w9ha0pvckpvrxzmt0w4h8ggcqqgqsq8lfq2t52j3j8su9szppsd7rr4q5rfappfyrtk28t3fl5w4xvtsrnp4ng0mc5u4huyj280h0ll99yhlfjz3uughwl0v2xyhfagevt5zqsapn3w
        ~~~
        </blockquote></details> -->

        ```
        record1qyqspfj735jzmfecuc58v7l4gwj4y8a0x4h7uyhw2s0ygjn9n6k3sjqwqgzhgmmtv4hyxqqzqgq0lxf369xkejpqla66j0y2gakgq6k6gdqtspaml0vzzr35a608yrf2499852x83zwpjtcdprhj8kc4c254mty45edjld4w9ha0pvckpvrxzmt0w4h8ggcqqgqsq8lfq2t52j3j8su9szppsd7rr4q5rfappfyrtk28t3fl5w4xvtsrnp4ng0mc5u4huyj280h0ll99yhlfjz3uughwl0v2xyhfagevt5zqsapn3w
        ```

- Decrypt Record:
    - Code Snippet. For More, visit [this link](https://concbon-mene.medium.com/deploying-and-executing-programs-in-aleo-4b535676e807):
        ```
        snarkos developer decrypt -v <VIEW_KEY> -c <RECORD_CIPHERTEXT>
        ```
    
    - In my case,
        - VIEW_KEY: `AViewKey1ueEqKhmPNV7d3pfo4GwCiPjiCoBmrBS4PJRm9n5bzbsY`
        - RECORD_CIPHERTEXT: `record1qyqspfj735jzmfecuc58v7l4gwj4y8a0x4h7uyhw2s0ygjn9n6k3sjqwqgzhgmmtv4hyxqqzqgq0lxf369xkejpqla66j0y2gakgq6k6gdqtspaml0vzzr35a608yrf2499852x83zwpjtcdprhj8kc4c254mty45edjld4w9ha0pvckpvrxzmt0w4h8ggcqqgqsq8lfq2t52j3j8su9szppsd7rr4q5rfappfyrtk28t3fl5w4xvtsrnp4ng0mc5u4huyj280h0ll99yhlfjz3uughwl0v2xyhfagevt5zqsapn3w`
    
    - Command For Me:
        ```
        snarkos developer decrypt -v AViewKey1ueEqKhmPNV7d3pfo4GwCiPjiCoBmrBS4PJRm9n5bzbsY -c record1qyqspfj735jzmfecuc58v7l4gwj4y8a0x4h7uyhw2s0ygjn9n6k3sjqwqgzhgmmtv4hyxqqzqgq0lxf369xkejpqla66j0y2gakgq6k6gdqtspaml0vzzr35a608yrf2499852x83zwpjtcdprhj8kc4c254mty45edjld4w9ha0pvckpvrxzmt0w4h8ggcqqgqsq8lfq2t52j3j8su9szppsd7rr4q5rfappfyrtk28t3fl5w4xvtsrnp4ng0mc5u4huyj280h0ll99yhlfjz3uughwl0v2xyhfagevt5zqsapn3w
        ```
        <details><summary> Detailed Output </summary><blockquote>

        ~~~
        vagrant@Luma-Workshop:~/Projects/AlphaSwap-Zenox/Task$ snarkos developer decrypt -v AViewKey1ueEqKhmPNV7d3pfo4GwCiPjiCoBmrBS4PJRm9n5bzbsY -c record1qyqspfj735jzmfecuc58v7l4gwj4y8a0x4h7uyhw2s0ygjn9n6k3sjqwqgzhgmmtv4hyxqqzqgq0lxf369xkejpqla66j0y2gakgq6k6gdqtspaml0vzzr35a608yrf2499852x83zwpjtcdprhj8kc4c254mty45edjld4w9ha0pvckpvrxzmt0w4h8ggcqqgqsq8lfq2t52j3j8su9szppsd7rr4q5rfappfyrtk28t3fl5w4xvtsrnp4ng0mc5u4huyj280h0ll99yhlfjz3uughwl0v2xyhfagevt5zqsapn3w

        {
        owner: aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa.private,
        token: 5527204198704484578620591539455109020124318183905545955577744208298624522139field.private,
        amount: 1000000u128.private,
        _nonce: 1973876259326365823408090218958076076956931351914894715655012934181796998040group.public
        }
        ~~~
        </blockquote></details>
        <img src=./Assets/decrypt-record.png>


- Private Swap:
    - Code Snippet:
        ```
        snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "private_key" alphaswap_v1.aleo swap_exact_private_for_private -r "Decrypted_record" 3026468451225309503872241584315905836458320845457788618560081218076006983319field 500000u128 0u128 "your_address_for_sending" "your_address_for_receiving"
        ```
    - In my case:
        - private_key: `APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6`
        - Decrypted_record: 
            ```
            {
            owner: aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa.private,
            token: 5527204198704484578620591539455109020124318183905545955577744208298624522139field.private,
            amount: 1000000u128.private,
            _nonce: 1973876259326365823408090218958076076956931351914894715655012934181796998040group.public
            }
            ```
    - My command will be:
        ```
        snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6" alphaswap_v1.aleo swap_exact_private_for_private "{
        owner: aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa.private,
        token: 5527204198704484578620591539455109020124318183905545955577744208298624522139field.private,
        amount: 1000000u128.private,
        _nonce: 1973876259326365823408090218958076076956931351914894715655012934181796998040group.public
        }" 3026468451225309503872241584315905836458320845457788618560081218076006983319field 500000u128 0u128 "aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa" "aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa"
        ```

        <details><summary> Detailed Output </summary><blockquote>

        ~~~
        vagrant@Luma-Workshop:~/Projects/AlphaSwap-Zenox/Task$ snarkos developer execute --network 1 --query "https://api.explorer.aleo.org/v1" --broadcast "https://api.explorer.aleo.org/v1/testnet/transaction/broadcast" -p "APrivateKey1zkpGzxyJXQs4j1DMVWM1bFt1sNW62Lo9cR6JH6UqpdPnAr6" alphaswap_v1.aleo swap_exact_private_for_private "{
        owner: aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa.private,
        token: 5527204198704484578620591539455109020124318183905545955577744208298624522139field.private,
        amount: 1000000u128.private,
        _nonce: 1973876259326365823408090218958076076956931351914894715655012934181796998040group.public
        }" 3026468451225309503872241584315905836458320845457788618560081218076006983319field 500000u128 0u128 "aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa" "aleo1k93ktaumr3fuvd230hwqruenhp4yjs6u5l3jqse0r43kda3djvrsd3hhpa"

        📦 Creating execution transaction for 'alphaswap_v1.aleo/swap_exact_private_for_private'...


        ⚠  "powers-of-beta-18.usrs.7a12bcb" does not exist. Downloading and storing it (in "/home/vagrant/.aleo/resources/powers-of-beta-18.usrs.7a12bcb").

        Installation - Downloading "https://s3-us-west-1.amazonaws.com/mainnet.parameters/powers-of-beta-18.usrs.7a12bcb"
        Installation - 100.00% complete (12 MB total)   Installation - Storing file in "/home/vagrant/.aleo/resources/powers-of-beta-18.usrs.7a12bcb"

        ⚠  "shifted-powers-of-beta-18.usrs.9a1859e" does not exist. Downloading and storing it (in "/home/vagrant/.aleo/resources/shifted-powers-of-beta-18.usrs.9a1859e").

        Installation - Downloading "https://s3-us-west-1.amazonaws.com/mainnet.parameters/shifted-powers-of-beta-18.usrs.9a1859e"
        Installation - 100.00% complete (12 MB total)   Installation - Storing file in "/home/vagrant/.aleo/resources/shifted-powers-of-beta-18.usrs.9a1859e"

        ⚠  "inclusion.prover.8faa4d3" does not exist. Downloading and storing it (in "/home/vagrant/.aleo/resources/inclusion.prover.8faa4d3").

        Installation - Downloading "https://s3-us-west-1.amazonaws.com/testnet.parameters/inclusion.prover.8faa4d3"
        Installation - 100.00% complete (222 MB total)   Installation - Storing file in "/home/vagrant/.aleo/resources/inclusion.prover.8faa4d3"
        ✅ Created execution transaction for 'alphaswap_v1.aleo/swap_exact_private_for_private'
        ⌛ Execution at15u9djd39exaz007p2tk8trrmjlp77kw7dgmft0ha3yl7jwzp7yxqqy2aw2 ('alphaswap_v1.aleo/swap_exact_private_for_private') has been broadcast to https://api.explorer.aleo.org/v1/testnet/transaction/broadcast.
        at15u9djd39exaz007p2tk8trrmjlp77kw7dgmft0ha3yl7jwzp7yxqqy2aw2
        
        ~~~
        </blockquote></details>
        <img src=./Assets/private-swap.png>
    
    - From above output, transaction ID: `at15u9djd39exaz007p2tk8trrmjlp77kw7dgmft0ha3yl7jwzp7yxqqy2aw2`
    - Visit [this link](https://explorer.aleo.org) and search Txn ID, output should be like similar:
        <img src=./Assets/private-swap-explorer.png>
