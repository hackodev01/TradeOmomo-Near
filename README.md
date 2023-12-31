# Leverage trading over concentrated liquidity
# NEAR 2023
Omomo leverage trading is a leverage trading protocol which utilizes feature of [concentrated liquidty](https://docs.uniswap.org/protocol/concepts/V3-overview/concentrated-liquidity) from [ref.finance](https://ref-finance.medium.com/ref-v2-unlock-concentrated-liquidity-for-better-capital-efficiency-8a63e3c33f5b) and lending borrowing feature of [Omomo lending](https://omomo.gitbook.io/omomo/product/borrow).


## How it works

### Buy/sell order
First step is Deposit
<details>
<summary>Diagramm</summary>
  
![Omomo - Deposit flow](https://user-images.githubusercontent.com/91728093/202552957-18ba9937-84ea-4e12-a034-202520461b9b.jpg)

</details>
  
Once user have deposited `Sell token` it may borrow required assets, if it chooses to trade with leverage, and create limit order to buy exact amount of `Buy token` at current market price. That where we interact with ref.finance V2 concentrated liquidity feature. It allow us to provide liquidity to the pool at concrete range and wait until market croses that range so whole liquidity is converted from `Sell token` to `Buy token` without paying `Swap fee` and rely on `Slippage tolerance`. Furthermore any operations over our liquidity provides us with additional income equal to pool fee.
<details>
<summary>NOTE</summary>

Right now everything done in one call executed by `open position`

</details>

Once order is created you should see it listed under trading view

<details>
<summary>Diagramm</summary>
  
![Omomo - Create order flow](https://user-images.githubusercontent.com/91728093/202553444-06ac762c-47db-4c7a-8f8f-fb8e33c566f4.jpg)

</details>

### Execute position & Close position

Once order is created it coud be automatically handled by `Executor` when the order is fulfilled. Once order is executed you now may either create `Take profit order` or `Cancel` the position. 

* [not yet implemented] `Take profit order` is counterpart action to opening position, Leverage trading will create limit order at desired price which will be fulfilled once market hit this price and proccessed by executor the same way as open position
* `Cancel` position allows you to immediately swap your `Sell token` at the current market price and could by used to prevent loss or take profit once you satisfied with the PnL

<details>
<summary>Diagramm</summary>
  
![Omomo - Execute order flow](https://user-images.githubusercontent.com/91728093/202554598-6102cc9b-f059-4f9e-b57d-4dd37efa196d.jpg)
![Omomo - Cancel order flow](https://user-images.githubusercontent.com/91728093/202560845-6a3e2781-56a3-4192-946c-45eb7d0bb06a.jpg)
![Omomo - Take profit order flow](https://user-images.githubusercontent.com/91728093/202560868-34de50da-3ea2-42e9-8057-acc834c9caed.jpg)

  
</details>

### Liquidate position 

<details>
<summary>Diagramm</summary>

![Omomo - Liquidate order flow](https://user-images.githubusercontent.com/91728093/202560985-05edd4f9-3c30-44de-97be-e00a22a80d48.jpg)
  
</details>

# Roadmap
