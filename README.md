# What's new in TT version 2024.2.1 Beta 3

- fixed bug in Ctrl-C handling
- auto detect CPU device for FLEX algo
- fixed bug in ProgPoW algo
- fixed time display
- improved performance for GHOSTRIDERE algo
- support of GPU & CPU mining of GHOSTRIDER at the same time




# What's new in TT version 2024.2.1 Beta2

- new algo: FLEX
- minor bugfixes

complete beta release notes will follow soon. Since FLEX is a CPU only algo you need to know the ID of the CPU in your system. please run TT with the 'list' option first to find out which ID you CPU got:
Windows: TT-Miner -l
Linux: ./TT-Miner -l

look for the CPU device that TT listed - in this case it is the id: 4:

********* CPU/Core information<br/>
CPU/Core devices:   1<br/>
04                     GenuineIntel Intel(R) Core(TM) i9-9900K CPU @ 3.60GHz   CPUs/Cores: 1/16<br/>



the command line for kylacoin mining would then look like this:<br/>
### TT-Miner -d 4 -a FLEX -P ssl:\/\/KYLA-Wallet.WORKER:PASSWORD@eu.mpool.live:6486

Per default TT uses all but 2 cores to make sure the sdystem stays responsive. If you wish to add more cores you can use the -t commandline option. If you want to use 16 core please this command line:
### TT-Miner -d 4 -t 16 -a FLEX -P ssl:\/\/KYLA-Wallet.WORKER:PASSWORD@eu.mpool.live:6486


To run the FLEX algo you need at least a SKYLAKE CPU - or better. Unforunatley I could not run a test on hive since I do not have a CPU that is SKYLAKE class. AMD is also not tested. I got already an information that home ryzen5 works.



Please note that this beta is not well tested - let me know if you have any issues.





# What's new in TT version 2023.4.0-beta1

- new ALGO EthashB3 - Rethereum(RTH)
- new ALGO Sha3D - Kylacoin (KCN)
- support for KiiroCoin (KIIRO)
- support for integrated GPUs (iGPU/ APU) - please use commandline option -igpu
- support for CPU mining - please use commandline option -cpu
- improved hashrate for Sha512256D - Radiant RXD


## using iGPU
You can now use the integrated GPU to mine. To use it just add -igpu to your command line. This will check for a iGPU and enable it if one is found. In this version TT does not support any Algo that requires a lot of memory (Ethash, ProgPow, KawPoW, GhostRider...)

## using CPU
You can now use the CPU to mine. To use it just add -cpu to your command line. This will check for is the CPU is supported and enable it. In this version TT does not support any Algo that requires a lot of memory (Ethash, ProgPow, KawPoW, GhostRider...) - so the same limitation as for iGPU applies. Also TT uses all cores in this version for mining. This will have a bad impact on the overall performance of the system. I will fir this and use fewer cores in a later release.




# What's new in TT version 2023.2.0-beta12

- new support for ZIL (ZMP shardpool.io & stratum for crazypool.org ) TCP & SSL
- new support for Alephium (Blake3 algo)
- new support for SHA256D
- support for 3 alternating coins/algos at the same time. You can now mine ZIL, EPIC and a 3rd coin
- new parallel mining - not just alternating as used with ZIL & EPIC
- related commandline option are now wraped into blocks with 'selectors' you choose
- new function 'lottery' to spend a very low hashes to a solo BTC or BCH mining

## wrapping commandline option into a block
Let assume you want to mine EPIC, RXD and ZIL (alternating - just one of them at a time). First we chose the pattern we want to use:

for EPIC we use "EP"
for RXD we use "RX"
for ZIL we use "Z"
For each coin we need the -c (for coin) and the -P (required information to connect to an pool) option. We append our pattern and that wraps the information for the 3 algos/coin:
TT-Miner -cEP EPIC -PEP .:@: -cRX RXD -PRX .:@: -cZ ZIL -PZ .:@:

Now that you have the alternating mining enabled you might think that it would be nice to have EPIC mined parallel with Alephium. That is now possible.

## parallel mining
You need to add the wrapped information for Alephium and tell TT that it should mine this coin when EPIC is active as well. As selector for ALPH we use the pattern "ALP". The required information for -c and -P would look like this:

-cALP ALPH -PALP .:@:

To tell TT to join EPIC and ALPH we append the -j commandline option - again with the pattern for ALPH to make sure TT combines ALP and EP:
-jALP EP

Now TT mines ZIL, EPIC & ALPH in parallel and RXD.


## using the BTC/BCH lottery
To join the Bitcoin or BitcoinCash lottery you just need to add the
-lottery
commandline option. A sample for Bitcoin looks like this:
-lottery BTC

That's all. TT will print a link to the solo pool that holds your stats together with the regular mining statistics. You can also run TT with just the lottery enabled and you can continue to use you PC without any big impact.

If you have any questions or need some assistance to get TT working in the configuration you want please let me know - I'm happy to help.
