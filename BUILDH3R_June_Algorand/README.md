# BUILDH3R_June_Algorand

This is a proof of task for Algorand.

## Task
- Create an Algorand Standard Asset (Token/Asset). Then send the asset to three Algorand Accounts.
- Screenshot proof: Print out the information of the three accounts.
- [Option]: Can be done locally installing algorand-cli or using github codespace. [Github repo Link](https://github.com/Ganainmtech/codespace_algorand)
- I will be doing this locally in my VM.

## Setup VM
- Make sure `docker`, `python3` and `pip` are pre-installed in your VM.
- Install `algorand` locally. Below command will install cli.
    ```
    sudo apt update && \
    sudo apt install pipx && \
    pipx ensurepath && \
    sudo pipx ensurepath --global
    pipx install algokit 
    algokit localnet start
    ```

- Setup Local System.
    ```
    curl -s https://raw.githubusercontent.com/Ganainmtech/codespace_algorand/main/algorand_setup.sh | sh
    ```

## Perform Task
- Create new file in terminal named `main.py`. You can use any text editor like `vim`, `nano` or `VSCode` if you have remote SSH to your server.
- Copy and Paste the `main.py`.
- Run that:
    ```
    python3 main.py
    ```
    Output:
    <details><summary> Detailed Output </summary><blockquote>

    ~~~
    vagrant@Luma-Workshop:~/Projects/Algorand-Foundation$ python3 main.py 
    Dispenser Address:  SR6DL5LQTGE6I4RDCBBIG3Z7AYEQJMAJIESEM2ULL37KPNEFZHECSRLAUU
    Creator Address:  DP3UZOYTBEQO3AURMRFLMLTVLB2D7V26VCATI56WNHPALLG6MEP2ACQXHY
    Asset ID:  1002
    Receiver1 Address: 3LKF75UYBOUDYUXIUHTNO5JQVMIZD72DLKIF7XYMTDCZAE2M6BH7E7K4QI
    Receiver2 Address: ZBGWMCX2OOZIKYBV2YXXZ3XZJD45FCIL5QF2YF3R5TOCSGRLVUC3ZKFFIA
    Receiver3 Address: JDOA36X76QXFXH3PJCM7YRBJ2S3UF7XW3VGS2LTBDKHH2VSHO2QOVDERDM
    Before Clawback:
    Receiver1 Account Asset Balance: 100
    Receiver2 Account Asset Balance: 100
    Receiver3 Account Asset Balance: 100
    After Clawback:
    Receiver1 Account Asset Balance: 98
    Receiver2 Account Asset Balance: 98
    Receiver3 Account Asset Balance: 98
    Creator Account Asset Balance: 706
    ~~~
    </blockquote></details>
    <img src=./Assets/final-outcome.png>
