---
#
# By default, content added below the "---" mark will appear in the home page
# between the top bar and the list of recent posts.
# To change the home page layout, edit the _layouts/home.html file.
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
#
layout: home
---


SPX 0DTE strategy means trading SPX weekly options (`SPXW`) that expires the same day (a.k.a 0 days to expiration)

Usually, I open credit spread positions between `9:50 - 12:00 A.M EST` (`6:50 - 9:00 A.M PST`) and close them before the market closes the same day around `4:00 P.M EST`.

**NOTE**: SPX option is different than SPX weekly option

- SPX options are `AM-settled` options that expire monthly on the third Friday.
- SPX weekly options are `PM-settled` that expire daily after market close.

The `0dte` strategy only applies to SPX weekly options.

## **Why SPX 0DTE strategy?**

- SPX weekly options expire every day. It means you can trade every day.
- SPX weekly options is highly liquid, you can often execute trades at the prices you want.
- SPX weekly options uses the SPX price when the market closes at `4:00 P.M EST` to settle. This is very different than stock options, which bears overnight risk (e.g. after hour price movement could lead to options assignment)
- SPX weekly options is cash settled, meaning no risk of getting assigned with stocks
- Tax benefit: any gains/losses are subject to different tax treatment–60% long-term and 40% short-term.
- Well-defined risk exposure. Never worry about “blowing up” when the market makes a huge move (assuming appropriate position size)
- Small account size. You can start to trade this strategy with only $500

## Strategy deep dive

### Credit spread

A `credit spread` means you simultaneously sell one option and buy another option on the `same underlying asset` with the `same expiration date` but `different strike prices`.

The option sold typically has a higher premium (credit) than the option bought, resulting in a net credit/debit.

You can either:

1. `sell to open`a credit spread, resulting in a net **credit**
2. `buy to open` a credit spread, resulting in a net **debit**


### Entry rules

#### Sell to open credit spread

In this strategy, it only uses `sell to open` to enter positions to collect credits.

It can either be `sell to open` `put` credit spread or `call` credit spread.

E.g. `sell to open` put, the following example results in `$0.50` net credit:

| Qty | Strike   | Exp        | Price |
|-----|----------|------------|-------|
| +1  | 5040 Put | 2024-02-29 | 1.2   |
| -1  | 5045 Put | 2024-02-29 | 1.7   |


**Note**: In this strategy, `$5` strike price difference is chosen to limit the max loss.

#### Time

I try to enter positions between `9:50 - 12:00 A.M EST` (`6:50 - 9:00 A.M PST`), since it is volatile right after the market open. Also I don't want to open positions too late as the time value of credit spread decays.

#### Select strike price

I select the strike price with ~20% probability ITM (or Delta value)

#### Pricing

I seek to open positions with at least `$0.75` credit.

#### Days to avoid trade

I usually avoid trading when there is a FOMC meeting or CPI day as the market can be very volatile.

### Exit rules

#### Take profit early

The market can swing the day, making a position with profit to loss. Therefore, I always close positions early without holding until the market close, when it reaches the profit target.

My target profit is `60%` of the credit received or `$55` profit per position.

I find that lots of time the price of a credit spread is around `$0.25` but I have to wait several hours until market close. I don't want to take the risk of turning a position with profit to loss. Therefore, I will close it early.

#### Stop loss

It is **vital** to set up stop loss. I have made mistakes not enforcing stop loss strictly, leading to large losses. Usually, it takes a few days to recover from a large loss.

For example, you open a credit spread with `$0.80` credit. If the market goes against you, the position becomes ITM, leading to `$4.20` loss (with `$5` strike price difference). You will need **8** successful trades (e.g. with `$55` profit each trade) to recover this loss. However, If you stop loss at `$3.0` (i.e `$2.20` loss), you only needs around **4** successful trades to recover.


## Lessons Learnt

***CONSISTENCY: THE KEY TO SUCCESS***

**Remember: one bad trade could wipe out a few good trades**

**.**
