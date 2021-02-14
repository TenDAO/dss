## Urn - Cdp state

`Urn` records hold current Cdp state for a given user (`address`) and collateral type (`Ilk`)

* **ink** - Locked collateral (Gem)
* **art** - Debt on issue (Dai)

```
Vat.urns[ilk][user] 
```

## Gem - Available collateral

User balances for collateral tokens added to the system via `join` are accounted for in the `Vat` as `Gem` according to collateral type `Ilk`. 

```
Vat.gem[ilk][user]    // Free collateral (Gem)
```

## Dai - Collateral-backed debt

Cdp debt balances are accounted for in the `Vat` as `Dai`.

```
Vat.dai[user]         // Dai balance for a given user (Dai)
```

## Pie - Savings Dai

User balances for Dai which has been allocated to savings is accounted for in the `Pot` as `Pie`.

```
Pot.pie[user]         // Savings Dai balance for a given user 
```

## Sin - Bad debt

Un-backed debt i.e. debt seized from liquidated Cdps is accounted for in the `Vat` as `Sin`. (In practice, the `Vow` is the only user with a non-zero Sin balance.)

```
Vat.sin[user]         // Bad debt (Sin) 
```