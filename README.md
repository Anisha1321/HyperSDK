
<!--   <img width="90%" alt="tokenvm" src="assets/logo.png"> -->
</p>
<p align="center">
<!--   Mint, Transfer, and Trade User-Generated Tokens, All On-Chain -->
</p>
<p align="center">
<!--   <a href="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-static-analysis.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-static-analysis.yml/badge.svg" /></a> -->
<!--   <a href="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-unit-tests.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-unit-tests.yml/badge.svg" /></a> -->
<!--   <a href="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-sync-tests.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-sync-tests.yml/badge.svg" /></a> -->
<!--   <a href="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-load-tests.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/tokenvm-load-tests.yml/badge.svg" /></a> -->
</p>

# Customized Blockchain Using HyperSDK
In this project we are making some changes in the initial github repository which will create a custom blockchain on HyperSDK framework using 'Go' language.

## Getting Started
1) setting the constants in consts/consts.go
   
<img width="818" alt="SS-1" src="https://github.com/user-attachments/assets/13e16623-665d-4f4f-930a-d28230e899f1">

2) Adding the code in registry/registry.go

![image](https://github.com/user-attachments/assets/b212ecd4-c511-4e6c-bf35-6efcffa4a10e)


launching the hyperchain using the following command.

```bash
./scripts/run.sh;
```


if we don't need 2 Subnets for the testing, we can run 
 
 ```bash
MODE="run-single" ./scripts/run.sh
```



<img align="center" width="1245" alt="image" src="https://github.com/PradeepSahhu/CustomSubnet-using-HyperSDK/assets/94203408/efbc7005-7d68-4ea0-b30a-eb7bbde1b2df">


By default, this allocates all funds on the network to `token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp`.

The private key for this address is
`0x323b1d8f4eed5f0da9da93071b034f2dce9d2d22692c172f3cb252a64ddfafd01b057de320297c29ad0c1f589ea216869cf1938d88c9fbd70d6748323dbf2fa7`.
this key has is also stored at `demo.pk`




To  interact with the `tokenvm`, implement the `token-cli`.
Next, we'll need to build this. by using this command

```bash
./scripts/build.sh
```

This command will put the compiled CLI in `./build/token-cli`._

Lastly, we'll need to add the chains that we created and the default key to the
`token-cli`. we can use the following commands

```bash
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```


<img width="1113" alt="image" src="https://github.com/PradeepSahhu/CustomSubnet-using-HyperSDK/assets/94203408/6e24ec08-6a87-4cb1-95e4-0c5e7840df25">


`chain import-anr` connects to the Avalanche Network Runner server running in
the background and pulls the URIs of all nodes tracking each chain we
created.

### Mint and Trade
#### Step 1: Create our Asset
let's create our own asset. You can do so by running the following command:

```bash
./build/token-cli action create-asset
```

When you are done, the output should look something like this:



<img width="641" alt="SS-3" src="https://github.com/user-attachments/assets/85a208ab-c176-4df1-b421-dacfea092636">

_`txID` is the `assetID` of your new asset._

The "loaded address" here is the address of the default private key (`demo.pk`). We
use this key to authenticate all interactions with the `tokenvm`.

#### Step 2: Mint our Asset
After we've created our own asset, we can now mint some of it. You can do so by
running the following command:
```bash
./build/token-cli action mint-asset
```

When you are done, the output should look something like this:

<img width="616" alt="SS-4" src="https://github.com/user-attachments/assets/c6501c0d-2705-48e3-ba91-630822a1a957">





#### Step 3: View our Balance
Now, let's check that the mint worked right by checking our balance. we can do
so by running the following command:

```bash
./build/token-cli key balance
```

When you are done, the output should look something like this:

<img width="656" alt="SS-5" src="https://github.com/user-attachments/assets/0d6bee49-4b72-4597-bf8b-6986ccc5e5cd">



After all this we can stop our running subnet network by using: 
 to stop the network we started using
`killall avalanche-network-runner`._

## Author
Anisha Kumari @anishakumarixib@gmail.com

