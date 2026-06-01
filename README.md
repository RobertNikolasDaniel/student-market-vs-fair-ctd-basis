# student-market-vs-fair-ctd-basis

A simple educational fixed income project exploring the relationship between:

* Treasury futures
* carry
* financing
* invoice pricing
* basis
* fair value vs market value

The goal of this project is NOT production-grade pricing.

The goal is transparent conceptual understanding of how Treasury futures and CTD mechanics interact through financing and delivery economics.

---

# Main Idea

Treasury futures can trade:

* rich
* cheap
* near fair value

relative to financing-adjusted theoretical futures pricing.

This project visualizes that relationship using:

* fair value futures
* market futures
* invoice pricing
* gross basis
* net basis
* rich vs cheap spread analysis

---

# Inputs

| Input                | Description                 |
| -------------------- | --------------------------- |
| CTD Par              | Bond par value              |
| CTD Clean            | Clean bond price            |
| CTD Rate             | Coupon rate                 |
| CTD Frequency        | Coupon frequency            |
| CTD In               | Days in coupon period       |
| CTD Since            | Days since last coupon      |
| CTD CF               | Conversion factor           |
| Market Futures Price | Actual traded futures price |
| Days To Delivery     | Days until futures delivery |
| Repo Rate            | Financing rate              |

---

# Outputs

| Output                                    | Description                              |
| ----------------------------------------- | ---------------------------------------- |
| CTD Coup Pay                              | Coupon payment                           |
| CTD Acc Int                               | Current accrued interest                 |
| CTD Dirty Price                           | Dirty bond price                         |
| Proj Fut Acc Int                          | Projected accrued interest at delivery   |
| Ideal FV Fut                              | Theoretical fair value futures           |
| Convert FV Fut                            | Fair futures converted into cash space   |
| Convert Mrkt Fut                          | Market futures converted into cash space |
| FV Invoice                                | Invoice using fair futures               |
| Mrkt Invoice                              | Invoice using market futures             |
| FV Gross Basis                            | Dirty - converted fair futures           |
| FV Net Basis                              | Dirty - fair invoice                     |
| Mrkt Gross Basis                          | Dirty - converted market futures         |
| Mrkt Net Basis                            | Dirty - market invoice                   |
| Mrkt To Ideal Unconverted Fut Price Basis | Market futures - fair futures            |
| Mrkt To Ideal Converted Price Basis       | Converted market - converted fair        |
| Mrkt To Ideal Invoice Price Basis         | Market invoice - fair invoice            |

---

# Core Formulas

## Coupon Payment

```text id="j5m2ra"
Coupon Payment =
(Coupon Rate × Par) / Frequency
```

---

## Accrued Interest

```text id="u7v5ye"
Accrued Interest =
(Days Since Coupon / Days In Coupon Period)
× Coupon Payment
```

---

## Dirty Price

```text id="p1k8wp"
Dirty Price =
Clean Price + Accrued Interest
```

---

## Projected Accrued Interest

```text id="m9q3xc"
Projected Accrued =
Accrued Interest
+
(
Days To Delivery / Days In Coupon Period
× Coupon Payment
)
```

---

## Fair Value Futures

```text id="d2v7lu"
Fair Value Futures =
(
Dirty Price
+
(
Dirty Price × Repo × (DTD / 360)
)
-
Projected Accrued
)
/ Conversion Factor
```

---

## Converted Futures Price

```text id="x6m1qt"
Converted Futures =
Futures × Conversion Factor
```

---

## Invoice Price

```text id="q3v8ra"
Invoice =
Converted Futures + Projected Accrued
```

---

## Gross Basis

```text id="n7p4ye"
Gross Basis =
Dirty - Converted Futures
```

---

## Net Basis

```text id="g8m2ra"
Net Basis =
Dirty - Invoice
```

More negative net basis:
→ cheaper delivery economics.

---

# Rich vs Cheap Logic

## Unconverted Futures Basis

```text id="u4v7ye"
Market Futures - Fair Futures
```

Positive:
→ market futures rich.

Negative:
→ market futures cheap.

---

## Converted Price Basis

```text id="p1k8wp"
Converted Market Futures
-
Converted Fair Futures
```

---

## Invoice Basis

```text id="m9q3xc"
Market Invoice
-
Fair Invoice
```

---

# How To Learn From This Project

This project is useful because every variable has mechanical meaning.

Instead of memorizing formulas, the goal is to understand relationships.

For example:

```text id="d2v7lu"
Higher repo
→ higher financing burden
→ higher fair futures value
→ higher invoice
→ more negative net basis
```

Or:

```text id="x6m1qt"
Market futures above fair value
→ rich futures
→ richer invoice
→ cheaper delivery economics
```

The purpose is to visually understand:

* financing
* carry
* invoice mechanics
* basis relationships
* relative value intuition

through transparent spreadsheet mechanics.

---

# Educational Value

This framework helps students think about Treasury futures in terms of:

* financing
* carry
* relative value
* delivery economics

instead of treating futures pricing as a black box.

The project is intentionally:

* simple
* visual
* transparent
* mechanically coherent

---

# Important Limitations

This is a simplified educational framework.

The model does NOT include:

* yield curve shifts
* duration/convexity
* implied repo calculations
* delivery options
* special repo
* liquidity effects
* term structure modeling
* actual CME delivery optimization
* stochastic rate behavior
* market microstructure

This project should NOT be used for trading or valuation purposes.

---

# Main Takeaway

Treasury futures are fundamentally connected to:

```text id="q3v8ra"
cash bonds
+
financing
+
carry
+
invoice pricing
+
relative value
```

This project attempts to make those relationships easier to visualize and study.
