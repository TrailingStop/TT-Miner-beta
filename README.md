# What's new in TT version 2023.2.0-beta12

- new support for ZIL (ZMP shardpool.io & stratum for crazypool.org ) TCP & SSL
- new support for Alephium (Blake3 algo)
- new support for SHA256D
- support for 3 alternating coins/algos at the same time. You can now mine ZIL, EPIC and a 3rd coin
- new parallel mining - not just alternating as used with ZIL & EPIC
- related commandline option are now warped into blocks with 'selectors' you choose
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
