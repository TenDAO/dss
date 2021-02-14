[![MCD-calls](https://user-images.githubusercontent.com/5028/58217074-3ec06880-7d55-11e9-91e2-c9bec7172bc4.png)](https://user-images.githubusercontent.com/5028/58217074-3ec06880-7d55-11e9-91e2-c9bec7172bc4.png)

## [Cat](https://github.com/makerdao/dss/blob/master/src/cat.sol) - Liquidator

* **Bite** - Trigger liquidation of an unsafe Cdp (vat.grab)

## [Dai](https://github.com/makerdao/dss/blob/master/src/vow.sol) - Token

* Mint - Mint to an address
* **Burn** - Burn at an address
* **Push** - Transfer
* **Pull** - Transfer From
* **Move** - Transfer From
* **Approve** - Allow pulls and moves 
* **Permit** - Approve by signature

## [End](https://github.com/makerdao/dss/blob/master/src/end.sol) - Global settlement

* **Cage** - Freeze user-facing actions. Tag Ilk prices.
* **Skim** - Settle a Cdp at the tagged price
* **Free** - Remove collateral from a settled Cdp
* **Thaw** - Fix outstanding Dai supply after all Skims
* **Flow** - Calculate final Ilk prices
* **Pack** - Lock Dai ahead of Cash
* **Cash** - Exchange packed Dai for collateral

## [Flipper](https://github.com/makerdao/dss/blob/master/src/flop.sol) - Collateral auctions

* **Kick** - Put up a new GEM `lot` for auction
* **Tick** - Bump the end date for an auction with no bids
* **Tend** - Submit a DAI bid (increasing `bid`)
* **Dent** - Submit a DAI bid (decreasing `lot`)
* **Deal** - Settle a completed auction

## [Flapper](https://github.com/makerdao/dss/blob/master/src/flap.sol) - Surplus auctions

* **Kick** - Put up a new DAI `lot` for auction
* **Tend** - Submit an MKR bid (increasing `bid`)
* **Deal** - Settle a completed auction

## [Flopper](https://github.com/makerdao/dss/blob/master/src/flop.sol) - Defecit auctions

* **Kick** - Put up a new MKR `bid` for auction 
* **Dent** - Submit a DAI bid (decreasing `lot`)
* **Deal** - Settle a completed auction

## [Join](https://github.com/makerdao/dss/blob/master/src/join.sol) - Token adapters

* **Join** - Deposit tokens to the system
* **Exit** - Remove tokens from the system

## [Jug](https://github.com/makerdao/dss/blob/master/src/jug.sol) - Stability fees

* **Drip** - Trigger stability fee accumulation (vat.fold)

## [Median](https://github.com/makerdao/median/blob/master/src/median.sol) - Price oracle

* **Read** - Get valid price or fail
* **Peek** - Get price and validity
* **Poke** - Set price from white-listed feed providers

## [OSM](https://github.com/makerdao/osm/blob/master/src/osm.sol) - Oracle security module

* Read - Get current valid price or fail
* Peek - Get current price and validity
* Peep - Get next price and validity
* **Poke** - Set next price if delay has elapsed

## [Pause](https://github.com/dapphub/ds-pause/blob/master/src/pause.sol) - System governance

* Plot - Schedule a plan
* **Exec** - Execute a plan
* Drop - Cancel a plan

## [Pot](https://github.com/makerdao/dss/blob/master/src/pot.sol) - Dai savings

* **Join** - Add Dai to the Pot
* **Exit** - Remove Dai from the Pot
* **Drip** - Trigger savings accumulation (vat.suck)

## [Spotter](https://github.com/makerdao/dss/blob/master/src/spot.sol) - Price relayer

* **Poke** - Update the spot price for a given Ilk (vat.file)

## [Vat](https://github.com/makerdao/dss/blob/master/src/vat.sol) - User balances

* **Hope** - Permit `flux` and `move` 
* **Nope** - Deny `flux` and `move` 
* Slip - Add and remove Gem
* **Move** - Transfer Dai
* **Flux** - Transfer Gem
* **Frob** - Cdp Management
* **Fork** - Transfer Cdp balances
* Grab - Seize Cdp balances 
* Heal - Balance system surplus/defecit
* Suck - Print Dai
* Fold - Apply rates across an Ilk

## [Vow](https://github.com/makerdao/dss/blob/master/src/vow.sol) - Liquidations manager

* Fess - Push bad debt to the auctions queue
* **Flog** - Release queued debt for auction
* **Heal** - Optimise debt buffer (vat.heal)
* **Kiss** - Release on-auction debt and Heal (vat.heal)
* **Flap** - Trigger a surplus auction (flapper.kick)
* **Flop** - Trigger a defecit auction (flopper.kick)