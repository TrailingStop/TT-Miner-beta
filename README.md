# TT-Miner 2023.2.0 beta 4



# TT-Miner 2023.2.0 beta 3
### New
- linux/hive support



# TT-Miner 2023.2.0 beta 2
### New
- add overclock offset for core & memory to the windows version (option -oc-coreoff[...], -oc-memoff[...] ).

### Fixes
- reenabled the config file to specify general oc settings for TT (option -conf[...]). This will give you the option to set different OC settings per GPU in a mixed rig.




# TT-Miner 2023.2.0 beta 1
### New
- ZIL mining - can be combined with EPIC and a 3rd coin
- dag swap: allows mining of ZIL + EPI and ETC with a 4GB GPU

### Fixes
- memory allocation fix for Ghostrider algo

New option/format:
While the old option format is still valid TT allows you to ‘combine’ some of the most important options to a set so that you can easily see which options belong together. You just add the options and append an identifier you like to define a set for an algo or a coin like this:

To define the settings for EPIC you append a ‘E’ or ‘EP’, or ‘EPIC’ – whatever you like. It is important that you append the same pattern to all option that belongs to the EPIC settings:
-cEPIC -PEPIC <user>@<server>:<port> -oc-coreEPIC 1455

In this sample I append “EPIC” for this block. It defines the coin (-c, connection-settings -P and core overclocking -oc-core).

This pattern for is available for:
-c coin
-a algo
-P connection string
-oc-core lock core clock
-oc-mem lock memory clock
-pc-pl power limit

As in older version of TT you can also append ‘alt’ to an alternate coin to EPIC.

To mine ZIL/Epic and ETC you commandline can look like this (without OC settings)

TT-Miner.exe -cEM EPIC -PEM <epic-user>.<epic-worker>:<epic-password>@<epic-server>:<epic-port> -cETC ETC -PETC <etc-user>.<etc-worker>:<etc-password>@<etc-server>:<etc-port> -cZIL ZIL -PZIL <zil-user>.<zil-worker>:< zil -password>@< zil -server>:< zil -port>
The order of the options doesn’t matter.
[6:31 PM]
If you use an older or smaller GPU with less memory you can mine ZIL, EPIC and ETC. For this you need less than 4GB and add the option:
-dag-swap to the command line. I recommend to add -dag-2disk as well to reduce the time required for swapping. TT also supports -dag-2mem, but this will require a lot of host memory.

If you see any issues, please do not hesitate to report bugs and problems. I’m happy to help.
[6:34 PM]
To use and OC options you need to run TT as administrator. So far I have not found any way to support older GPUs and also core/mem offset is not supported undert windows. For now you need to adjust the offset settings with a tool like 'MSI-Afterburner'


# TT-Miner 2023.1.8 beta 1 Pre-release
### New
- support for OC of older GPUs (Pascal) on HIVE
- support of core/mem offset OC
- introduction of config files to reuse settings for algos/coins depending on either: interface/model/default. Tha new package contains a sample configuration file that you can use as a base to start: SampleConfig.json



# TT-Miner 2022.3 - beta14

- Cuda 11.8 support
- Fixed hashrate-reporting to the ZANO solo mining stratum
- Added GhostRider/Mike algos



# TT-Miner 2022.3 - beta13


- Uses longpoll for solo mining against a Qt-Wallet instead of polling to save protocol/communication overhead and for a faster switch to a new block (avoiding stalled solution)
- Ghostrider/Mike algos are disabled in this beta
- DagSwap for Epic/Alternate mining is disabled in this beta



## Mining fees
| Mining | fee |
| - | - |
| Epic Cash | 2.0 % |
| Ghostrider/Mike algo| 2.5 % |
| Solo to Qt-Wallet | 2.0 % |
| all other | 1.0 % |





## Supported Algorithm

| Algorithm | remarks |
| - | - |
| Ethash | includes Etchash & Ubqhash |
| KawPow | includes FiroPow |
| ProgPow | includes ProgPowZ, vProgPow and ProgPow(Veil) |




## Directly Supported Coins (other coin can be mined by algorithm)

| Coin | Name | Algorithm |
| - | - | - |
| ETC | Ethereum Classic | Etchash |
| CLO | Callisto | Ethash |
| EXP | Expanse | Ethash |
| ETP | Metaverse | Ethash |
| UBQ | Ubiq | Ubqhash |
| FIRO | Firo | FiroPow |
| RVN | Ravencoin | KawPow |
| NEOX | Neoxa | KawPow |
| KAW | Kawkaw | KawPow |
| PRCO | Procyon | KawPow |
| SATO | Sato | KawPow |
| ARL | Arielcoin | KawPow |
| HVQ | Hivecoin | KawPow |
| TTM | Titanium | KawPow |
| MEOW | MeowCoin | KawPow |
| REDE | RedeCoin | KawPow |
| SERO | Super Zero | ProgPow |
| EPIC | Epic Cash | ProgPow |
| ZANO | Zano | ProgPowZ |
| EVOX | Evoultion | ProgPowZ |
| VBK | VeriBlock | vProgPow |
| VEIL | Veil | ProgPow(Veil) |
| RTM | Raptoreum | GhostRider |
| BTRM | Bitoreum | GhostRider |
| BUT | Butcoin | GhostRider |
| YERB | Yerbas | GhostRider |
| JGC | Jagoan | GhostRider |
| FITA | Theta | GhostRider |
| BBC | Babacoin | GhostRider |
| NAPI | Atanapicoin | GhostRider |
| THOON | Thooneum | GhostRider |
| VKAX | Vkax | Mike |




## Supported commandline option

#### Basic options
| Option | Information |
| - | - |
| -h [ --help, -? ] | Prints supported options and the commandline format. |
| -no-color [ -nocolor ] | Do not use any color in the screen output. |
| -no-ctrlc [ -noctrlc ] | Disables 'Ctrl-C' monitoring. |
| -no-hashrate [ -nohashrate ] | Do not send hashrate information to the pool. |


#### Algo options
| Option | Information |
| - | - |
| -a [ --algo ] arg | Defines the algorithm to use for the primary coin.<br/>Supported algos (values for 'arg'):<br/>ETHASH<br/>ETCHASH<br/>UBQHASH<br/>ProgPow<br/>ProgPowZ<br/>vProgPow<br/>FiroPow<br/>KawPow<br/>GhostRider<br/>Mike |
| -aalt [ --algoalt ] arg | Defines the algorithm to use for the alternte coin (primary coin must be 'EPIC'). |




#### Coin options
| Option | Information |
| - | - |
| -coin arg | Defines the primary coin to mine.<br/>Supported coins (values for 'arg'):<br/>ETC<br/>CLO<br/>EXP<br/>ETP<br/>UBQ<br/>SERO<br/>EPIC<br/>ZANO<br/>EVOX<br/>VBK<br/>VEIL<br/>FIRO<br/>RVN<br/>NEOX<br/>ARL<br/>KAW<br/>PRCO<br/>SATO<br/>HVQ<br/>TTM<br/>MEOW<br/>REDE<br/>RTM<br/>BTRM<br/>BUT<br/>YERB<br/>JGC<br/>FITA<br/>BBC<br/>NAPI<br/>THOON<br/>VKAX |
| -coinalt arg | Defines the alternate coin to mine (primary coin must be 'EPIC'). |




### Commandline samples
TT-Miner supports the -pool[-o], -user[-u], -pass[-p] notation as well as the more compact -P form. Please replace placeholder with your information:

| Placeholder | meaning |
| - | - |
| \<WALLET\> | Your wallet-id |
| \<WORKER\> | Your worker-id |
| \<USERNAME\> | Your username if reqired (check EPIC mining & solo mining to Qt-Wallet) |
| \<PASSWORD\> | Your password if reqired (check EPIC mining & solo mining to Qt-Wallet) |




### Mine ETC on 2miners (TCP-port) (-o,-u format)

| verion | commandline |
| - | - |
| TCP port, -P format | TT-Miner -coin ETC -P \<WALLET\>.\<WORKER\>@etc.2miners.com:1010 |
| TCP port, -o,-u format | TT-Miner -coin ETC -u \<WALLET\>.\<WORKER\> -o etc.2miners.com:1010 |
| SSL port, -P format | TT-Miner -coin ETC -P stratum+ssl://\<WALLET\>.\<WORKER\>@etc.2miners.com:11010 |
| SSL port, -o,-u format | TT-Miner -coin ETC -u \<WALLET\>.\<WORKER\> -o stratum+ssl://etc.2miners.com:11010 |






## Mining Solo to a Qt-Wallet
To use your Qt-Wallet for solo mining you need to create/configure a config file. The config file is a textfile that must contain following information:
You need \<USERNAME\> and \<PASSWORD\> in th commandline of TT-Miner to get access to the Qt-Wallet.
Please change rpcallowip to match your network configuration. It defines IPs that may connect to the wallet.<br/>

rem -- FILE START -- do not add this line to your config file!<br/>
automintoff=1<br/>
rpcuser=\<USERNAME\><br/>
rpcpassword=\<PASSWORD\><br/>
rpcbind=0.0.0.0<br/>
rpcallowip=192.168.41.0/24<br/>
server=1<br/>
listen=1<br/>
gen=1<br/>
miningaddress=\<WALLET\><br/>
rem -- FILE END -- do not add this line to your config file!<br/>


Then start your Qt-Wallet with the option to use this new configuration file:<br/>
##### neoxa-qt -conf=filename.conf<br/>


### Mine NEOX Solo to Qt-Wallet
Plase use the USERNAME and PASSWORD information from your config file that you use to start your wallet.<br/>
##### TT-Miner -coin neox -P http://\<USERNAME\>:\<PASSWORD\>@\<IP-TO-YOUR-QT-WALLET\>:9766




