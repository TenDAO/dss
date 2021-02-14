Dai Glossary
============

## General

- `guy`, `usr`: some address
- `wad`: some quantity of tokens, usually as a fixed point integer with 10^18 decimal places.
- `ray`: a fixed point integer, with 10^27 decimal places.
- `rad`: a fixed point integer, with 10^45 decimal places.
- `file`: administer some configuration value

### Auth

- `auth`: check whether an address can call this method
- `ward`: an address that is allowed to call authed methods
- `rely`: allow an address to call authed methods
- `deny`: disallow an address from calling authed methods

## CDP Engine - Vat

- `CDP`: Collateralised Debt Position
- `gem`: collateral tokens
- `dai`: stablecoin tokens
- `sin`: anticoin tokens (system debt, not belonging to any `urn`)

- `ilk`: a collateral type
  - `rate`: stablecoin debt multiplier (accumulated stability fees)
  - `take`: collateral balance multiplier
  - `Ink`: total collateral balance
  - `Art`: total stablecoin debt

- `init`: create a new collateral type

- `urn`: a specific CDP
  - `ink`: collateral balance
  - `art`: outstanding stablecoin debt

- `debt`: the total quantity of stablecoin issued
- `vice`: the total quantity of system debt

- `slip`: modify a user's collateral balance
- `flux`: transfer collateral between users
- `move`: transfer stablecoin between users

- `grab`: liquidate a CDP

- `heal`: create / destroy equal quantities of stablecoin and system debt (`vice`)

- `fold`: modify the debt multiplier, creating / destroying corresponding debt
- `toll`: modify the collateral multiplier, creating / destroying
        corresponding collateral

- `suck`: mint unbacked stablecoin (accounted for with `vice`)

- `spot`: collateral price with safety margin, i.e. the maximum stablecoin
          allowed per unit of collateral
- `line`: the debt ceiling for a specific collateral type
- `Line`: the total debt ceiling for all collateral types
- `dust`: the minimum possible debt of a CDP

- `frob`: modify a CDP
  - `lock`: transfer collateral into a CDP
  - `free`: transfer collateral from a CDP
  - `draw`: increase CDP debt, creating Dai
  - `wipe`: decrease CDP debt, destroying Dai
  - `dink`: change in collateral
  - `dart`: change in debt
  - `calm`: true when the CDP remains under both collateral and total debt
          ceilings
  - `cool`: true when the stablecoin debt does not increase
  - `firm`: true when the collateral balance does not decrease
  - `safe`: true when the CDP's ratio of collateral to debt is above the collateral's liquidation ratio

- `fork`: split a CDP - binary approval or splitting/merging CDP's
  - `dink`: amount of collateral to exchange
  - `dart`: amount of stablecoin debt to exchange

- `wish`: check whether an address is allowed to modify another address's gem or dai balance
  - `hope`: enable `wish` for a pair of addresses
  - `nope`: disable `wish` for a pair of addresses

## Stability Fees - Jug

- `duty`: the stability fee
- `base`: global stability fee
- `rho`: when this collateral type was last collected from

- `drip`: determine the increase 

## Liquidations - Cat

- `mat`: the liquidation ratio
- `chop`: the liquidation penalty
- `dunk`: the liquidation quantity, i.e. the fixed debt quantity to be
          covered by any one liquidation event
- `box`: an upper limit on the total DAI needed to cover the debt and penalty fees on all active auctions

- `bite`: initiate liquidation of a CDP
- `flip`: liquidate collateral from a CDP to cover a fixed quantity of debt


## Settlement - Vow

- `sin`: the debt queue
- `Sin`: the total debt in the queue
- `Woe`: the total non-queued non-auction debt 
- `Ash`: the total on-auction debt
- `Awe`: the total debt
- `Joy`: the total surplus

- `fess`: add debt to the queue
- `flog`: realise debt from the queue
- `wait`: length of the queue

- `heal`: cancel out surplus and debt
- `kiss`: cancel out surplus and on-auction debt

- `sump`: debt auction lot size, i.e. the fixed debt quantity to be covered by any one debt auction
- `bump`: surplus auction lot size, i.e. the fixed surplus quantity to be sold by any one surplus auction
- `hump`: surplus buffer, must be exceeded before surplus auctions are possible


## Auctions - Flipper,Flopper,Flapper

- `flip`: collateral auction (selling collateral for stablecoins)
- `flop`: debt auction (covering debt by inflating MKR and selling for stablecoins)
- `flap`: surplus auction (selling stablecoins for MKR)

- `lot`: quantity up for auction
- `bid`: quantity being offered for the `lot`
- `tab`: total dai to be raised (in `flip` auction)
- `guy`: high bidder
- `gal`: recipient of auction income
- `ttl`: bid lifetime
- `beg`: minimum bid increase
- `tau`: maximum auction duration
- `claw`: reduces the amount of litter in the Cat's box
- `end`: when the auction will finish

- `kick`: start an auction
- `tick`: restart an auction
- `tend`: make a bid, increasing the bid size
- `dent`: make a bid, decreaseing the lot size
- `deal`: claim a winning bid


## Global Settlement - End
- `when`: the time of settlement
- `wait`: the length of processing cooldown (allowing undercollateralised CDPs to be `skim`med)
- `debt`: outstanding stablecoin supply, after system surplus/deficit has been absorbed
- `tag`: price per collateral type at time of settlement
- `gap`: shortfall per collateral considering undercollateralised CDPs
- `fix`: the cash price for an `ilk` (amount per stablecoin)
- `bag`: untransferrable stablecoins ready to exchange for collateral
- `out`: the amount of already exchanged stablecoin for a given address

- `cage`: freeze system, cancel `flip`/`flop` auctions, start the cooldown period
- `cage(ilk)`: sets the settlement price for an ilk
- `skim`: cancels CDP debt, taking backing collateral but leaving excess
- `skip`: optionally cancel live auctions
- `free`: remove collateral from CDP
- `thaw`: fixes the total outstanding supply of stablecoin
- `flow`: calculates the `fix` price for an ilk, possibly adjusting `cage` price with surplus/deficit
- `pack`: put some stablecoin into a `bag` in preparation for `cash`
- `cash`: exchange some stablecoin from `bag` for a given `gem`, share proportional to `bag` size