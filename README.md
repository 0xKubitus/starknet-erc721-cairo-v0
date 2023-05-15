# Starknet ERC721 Workshop Guide (Cairo version 0)

This repository contains the solutions to the exercises presented in the [ERC721 Workshop](https://github.com/starknet-edu/starknet-erc721) created by StarkWare to teach developers how to use StarkNet.

You can find detailed guides on how to solve each exercise step by step on [David Barreto' blog](https://david-barreto.com/)

- [Project Setup](https://david-barreto.com/starknet-erc721-workshop-setup/)
- [Exercise 1: Deploying an ERC721](https://david-barreto.com/starknet-erc721-workshop-exercise-1/)
- [Exercise 2: Creating Token Attributes](https://david-barreto.com/starknet-erc721-workshop-exercise-2/)
- [Exercise 3: Minting NFTs](https://david-barreto.com/starknet-erc721-workshop-exercise-3/)
- [Exercise 4: Burning NFTs](https://david-barreto.com/starknet-erc721-workshop-exercise-4/)
- [Exercise 5: Adding permissions and payments](https://david-barreto.com/starknet-erc721-workshop-exercise-5/)
- [Exercise 6: Claiming an NFT](https://david-barreto.com/starknet-erc721-workshop-exercise-6/)
- [Exercise 7: Adding Metadata](https://david-barreto.com/starknet-erc721-workshop-exercise-7/)

</br>
<hr>
</br>

## IMPORTANT NOTES:

**ATTENTION: This workshop uses Cairo version 0 contracts and its guide is adapted to older versions of the cairo compiler.**  
=> If you are using a recent version of Cairo (v0.9.0 or higher), the commands from the above guide might now be deprecated... No worries, I've got your back!

</br>

### 1) THE 'COMPILE' COMMAND:

Since [Cairo v0.11.0.2 was released](https://github.com/starkware-libs/cairo-lang/releases/tag/v0.11.0.2) this is how to compile Cairo version 0 contracts:

```bash
starknet-compile-deprecated path/of/your/contract.cairo --output path/to/compiled/contract.json --abi path/to/abis
```

_(adding "abi" flag is not necessary, but is used to invoke/call your functions from the CLI)_

</br>
<hr>
</br>

### 2) THE 'DECLARE' COMMAND:

Also, note that in case you're running Cairo version >= 0.9.0 (if I remember well), you need to
["DECLARE"](https://book.starknet.io/chapter_1/deploying_contracts.html#declare_a_contract_class) your contracts (and get their class hash) before deploying them.  
=> Since in this tutorial our contracts will be written in cairo version 0, here is how you should declare your contracts:

```bash
starknet declare --contract path/of/your/compiled/contract.json --deprecated
```

</br>

BONUS:  
You may need to specify the account used to pay fees if you have multiple accounts setup locally:  
-> Open your terminal and run: `cat ~/.starknet_accounts/starknet_open_zeppelin_accounts.json`  
=> you now have all details about your local accounts.

So, if you want/need to use a specific account ->

```bash
starknet declare --contract path/of/your/compiled/contract.json --deprecated --account your_account_name_here
```

</br>
<hr>
</br>

### 3) THE 'DEPLOY' COMMAND:

Now, here's how to deploy your cairo 0 contracts (not sure exactly if/how/when it changed):

```bash
starknet deploy --class_hash 0xclassHashOfYourFunction --inputs arg1 arg2 argx --network alpha-goerli --account your_account_name_here
```

_Obviously, "inputs" are not necessary relevant but this is where you give arguments to your constructor function - note that the arguments' values should be decimals (integers) or hex._

</br>
</br>
</br>

#### In case these command are not relevant anymore by the time you're reading this => feel free to check the Cairo language [versions release details](https://github.com/starkware-libs/cairo-lang/releases).
