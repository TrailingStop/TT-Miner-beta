# TT-Miner 2022.3 - beta13


- Uses longpoll for solo mining against a Qt-Wallet instead of polling to save protocol/communication overhead and for a faster switch to a new block (avoiding stalled solution)
- Ghostrider/Mike algos are disabled in this beta
- DagSwap for Epic/Alternate mining is disabled in this beta



## Mining fees
| Mining | fee |
| - | - |
| Epic Cash | 2.0% |
| Solo to Qt-Wallet | 2.0% |
| all other | 1.0% |





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
| -a [ --algo ] arg | Defines the algorithm to use for thwe primary coin.<br/>Supported algos (values for 'arg'):<br/>ETHASH<br/>ETCHASH<br/>UBQHASH<br/>ProgPow<br/>ProgPowZ<br/>vProgPow<br/>FiroPow<br/>KawPow |
| -aalt [ --algoalt ] arg | Defines the algorithm to use for the alternte coin (primary coin must be 'EPIC'). |




#### Coin options
| Option | Information |
| - | - |
| -coin arg | Defines the primary coin to mine.<br/>Supported coins (values for 'arg'):<br/>ETC<br/>CLO<br/>EXP<br/>ETP<br/>UBQ<br/>SERO<br/>EPIC<br/>ZANO<br/>EVOX<br/>VBK<br/>VEIL<br/>FIRO<br/>RVN<br/>NEOX<br/>ARL<br/>KAW<br/>PRCO<br/>SATO<br/>HVQ<br/>TTM<br/>MEOW<br/>REDE |
| -coinalt arg | Defines the alternate coin to mine (primary coin must be 'EPIC'). |
