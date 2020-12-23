---
  indexable: false
---

# Advanced Payments
## Introduction

Advanced Payments is an API that allows processing payments with additional functionalities to the regular [API of Payments](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/en/guides/online-payments/checkout-api/introduction). It currently allows to make Marketplace split payments.

#### Marketplace split payments

The Split Payment functionality provides a solution for Marketplace payments where the business model requires splitting money among multiple Sellers.

> NOTE
>
> Note
>
> For more information, please view the [Marketplaces](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/en/guides/online-payments/marketplace/checkout-api/introduction) documentation.

#### Payment division

* A payment made by a Buyer that corresponds to a Marketplace, is divided among multiple Sellers.
* The division is made at the time of payment approval.
* There is no limit of Sellers to divide the money and the Marketplace gets a commission for each sale made.
* You can configure who pays the Mercado Pago commission.

#### Flexibility to apply commission

* The Marketplace retains part of the sale amount as commission.
* The commission charged by the Marketplace applies to each payment.
* This allows having different commissions for different Sellers and in turn different commissions according to the type or category of the product offered by a Seller.

#### Sellers Money Release


* The money of your Sellers will be released in 30 days by default.

[Start using split payments in Marketplace](https://www.mercadopago[FAKER][URL][DOMAIN]/developers/en/guides/online-payments/marketplace/advanced-payments/receive-split-payments).
