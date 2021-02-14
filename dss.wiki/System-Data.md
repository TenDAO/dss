## System config

System level configuration is set per-module and updatable via `file` actions, which are authed to `DSPause`. 

```
End.when       Time of cage
End.wait       Processing cooldown length
End.debt       Total outstanding Dai following processing [rad]

Fl*pper.beg    Minimum bid increase e.g. 5%
Fl*pper.ttl    Bid duration              3 hours
Fl*pper.tau    Auction length            3 days

Jug.base       Base rate

Pot.dsr        The Dai Savings Rate
Pot.chi        The Rate Accumulator

Spotter.par    Ref per Dai

Vat.Line       System Debt Ceiling  [wad]

Vow.wait       Flop delay           [rad]
Vow.sump       Flop fixed lot size  [rad]
Vow.bump       Flap fixed lot size  [rad]
Vow.hump       Surplus buffer       [rad]
```
## Collateral types

`Ilk` records store configuration parameters, latest spot price, and total debt issued for any given collateral type (e.g. `ETH-A`). 

* **Art**  - Total debt backed by this `Ilk` (DAI)
* **rate** - Gem Dai exchange rate
* **spot** - Current Gem price with safety mat (USD)
* **line** - `Ilk` debt ceiling (DAI)
* **dust** - `Ilk` debt floor (DAI)
* **flip** - Flip auction contract address
* **lump** - Flip auction lot size
* **chop** - Liquidation penalty
* **duty** - `Ilk` stability fee
* **rho**  - Last drip timestamp
* **pip**  - Price oracle contract address
* **mat**  - `Ilk` liquidation ratio

```
Vat.ilks[identifier] e.g ETH-A
```

In practice, `Ilk` storage is split across the `Vat`, `Jug`, `Pot` and `Vow` modules. `Ilk` configuration parameters can be updated via `file` actions, which are authed to DSPause.

## Sin queue

Upon Cdp liquidation, seized debt is queued for auction in the `Vow` at the block timestamp of the `bite` action. It can be released for auction via `flog` once the alloted `Vow.wait` time has expired.

```
Vow.sin[era] e.g 1559522180
```

## System totals

```
Vat.debt     Total Dai Issued           [rad]
Vat.vice     Total Unbacked Dai         [rad]
Pot.Pie      Total Savings Dai
Vow.Sin      Total queued debt          [rad]
Vow.Ash      Total on-auction debt      [rad]
```