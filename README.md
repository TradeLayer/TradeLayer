TradeLayer v0.1.0
================

v0.1.0 is the first version of TradeLayer protocol. Is based on Omnicore-lite (credits to https://github.com/zathras-crypto) working on top of Litecoin Core (v0.16.3).


Table of contents
=================

- [TradeLayer v0.1.0](#tradelayer-v0.1.0)
- [Compatibility with Litecoin Core](#compatibility-with-litecoin-core)
- [Notable changes](#notable-changes)
  - [Contract DEx](#contract-dex)
  - [Pegged Currency](#pegged-currency)
  - [DEx improvements](#dex-improvements)
  - [MetaDex](#metadex)
  - [RPCs](#rpcs)
  - [Settlement Algorithm](#settlement-algorithm)
  - [Unit Testing](#unit-testing)
- [Credits](#credits)


Compatibility with Litecoin Core
-------------------------------

TradeLayer can be used as replacement for Litecoin Core v0.16.3 because it's an enhancement. In inheritance, Tradelayer has all the notables improvements of this Litecoin version.

Notable changes
===============

Contract DEx
-----------------------------------------
One of the major features of TradeLayer is the Decentralized Exchange for Futures Contracts. For now it's contains four contracts (ALL/dUSD, LTC/ALL)  for weekly and montly expiration. Also we integrate the ALL token, which is TradeLayer's token used for contract's colateralization.
Most of the development was made in x_Trade function. Changes related with the updating process for balances, trade amount and amount still for sale that is added in the order book with the respective address if was not found a match. New status for the buyer and seller depending on the updated balance after a trade. A new function for loop bidirectionals was built in order to look for matchs in the order book in different directions regarding of trading action (SELL or BUY).


Pegged Currency
-----------------------------------------------------
Other mayor feature of TradeLayer is pegged currency. The basis for pegged currency are related with the possibility to create a Hedge position in futures contracts and have an stable value equivalent. That equivalent value is represented as a new token (the pegged currency) but covered with the hedge.


DEx improvements
-----------------------------------------------------
Omni Layer's DEx is used now to sell/buy Litecoins in exchange for metacoins (like ALLs) who lives in TradeLayer Protocol. Old version of DEx makes possible the sell token offer, that later gets accepted by takers who want to buy them. The most important improvement for DEx is that is possible post a buying token offer.


MetaDEx
-----------------------------------------------------
Omni Layer's MetaDex is now ported into Tradelayer for trade all kinds of metacoins including the ALL token, and pegged currencies.


RPCs
-----------------------------------------------------
New RPCs are added in order to make Contract DEx trade, and retrieve different kind of data related.
Slight modifications were made to the existing RPC calls in order to have them
working with Litecoin Core v0.16.3 and some another news needed to the logic of Futures Contracts were added.


Settlement Algorithm
-----------------------------------------------------
This algorithm consider like source edges from every match line of the
vector of vector of maps built in recordMatchedTrade having two nodes opening or increasing
his positions two of them. We look for matched events for this two addresses using FIF and
also for those nodes opening or increasing position while the process. When the
FIFO algorithm finishes opened contracts are added as ghost nodes in a graph structure, that builds paths
following netting events with source being the new contracts created. By using a piecewise
function obtained by solving some equation we compute the respective exit price
required to have a global difference between PNL for long and short positions equal to zero.


Unit Testing
-----------------------------------------------------
Inside the repo src/ some shell scripts to test the project were built and unit tests based
in some usual Boost libraries inside src/omnicore/test/.


Credits
=======
Thanks to everyone who contributed to this release, and especially the Litecoin Core developers and Omni Core developers for providing the foundation for TradeLayer Protocol.


What is Omni Layer?
----------------
The Omni Layer is a communications protocol that uses the Bitcoin block chain to enable features such as smart contracts, user currencies and decentralized peer-to-peer exchanges. A common analogy that is used to describe the relation of the Omni Layer to Bitcoin is that of HTTP to TCP/IP: HTTP, like the Omni Layer, is the application layer to the more fundamental transport and internet layer of TCP/IP, like Bitcoin.

http://www.omnilayer.org


What is Litecoin?
----------------
Litecoin is an experimental digital currency that enables instant payments to
anyone, anywhere in the world. Litecoin uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. Litecoin Core is the name of open source
software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of
the Litecoin Core software, see [https://litecoin.org](https://litecoin.org).
to Litecoin periodically.
