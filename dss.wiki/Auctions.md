# Auctions

There are three auction types in the dai system, the _collateral auction_ (`flip`-auction), the _debt auction_ (`flop`-auction) and the surplus auction (`flap`-auction). Flap and Flop auctions are initiated by the [Vow](https://github.com/makerdao/dss/wiki/Vow). Collateral auctions are initiated by the [Cat](https://github.com/makerdao/dss/wiki/Cat).

Risk parameters:

* `beg` - minimum bid increase
* `ttl` - bid duration
* `tau` - auction duration

Bid parameters

* `lot` - amount for sale
* `bid` - amount paid
* `guy` - highest bidder
* `tic` - bid expiry
* `end` - auction expiry

## Flap - surplus auction

Flap is the simplest of the auctions, where surplus Dai is sold for MKR. Bidders complete for a fixed `lot` amount of Dai (`bump`) with increasing `bid` amounts of MKR.

[![Flap](https://user-images.githubusercontent.com/5028/45409672-f465f280-b6c3-11e8-910a-5316a2b39309.png)](https://user-images.githubusercontent.com/5028/45409672-f465f280-b6c3-11e8-910a-5316a2b39309.png)

## Flop - debt auction

Bidders complete with decreasing `lot` amounts of MKR for a fixed `bid` amount of Dai. On `kick` the `bid` is set to the flop auction lot size (`sump`) and `lot` is set to the largest uint (2^256).

[![Flop](https://user-images.githubusercontent.com/5028/45409906-94bc1700-b6c4-11e8-9c11-06522211cc02.png)](https://user-images.githubusercontent.com/5028/45409906-94bc1700-b6c4-11e8-9c11-06522211cc02.png)

## Flip - collateral auction

In the `tend`-phase bidders compete for increasing `bid` amounts of Gem. Once `tab` amount of Dai has been raised the auction moves to the `dent`-phase. 

During the `dent`-phase bidders can compete for decreasing `lot` amounts of Gem for `tab` amount of Dai. Forfeited Gem is returned to the liquidated Urn.

[![Flip](https://user-images.githubusercontent.com/5028/45414249-04cf9a80-b6cf-11e8-8a30-9c55a74ed178.png)](https://user-images.githubusercontent.com/5028/45414249-04cf9a80-b6cf-11e8-8a30-9c55a74ed178.png)