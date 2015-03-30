---
layout: post
title:  "Asset price chart data"
date:   2015-03-30 20:00:00
---
Generating asset price charts has become a problem because of the large amount of trades, it is no longer possible to load all trades in the client and generate a chart from that.

If you for instance take the <a target="_blank" href="https://fimkrypto.github.io/mofo/launch.html#/assets/nxt/12465186738101000735/trade">nemstake</a> asset you'll see it has 5000+ trades this would lead to many megabytes of JSON you need to download in order to generate a price chart of all trades.

The current implementation is very rough since it only stores an average price per timeframe but room was made in the database backend for open, high, low and close prices to which would allow for creating candlestick charts.

<b>RPC call</b>

<a target="_blank" href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/http/rpc/GetAssetChartData.java">src/java/nxt/http/rpc/GetAssetChartData.java</a>

<b>Backend (needs work - help wanted)</b>

<a target="_blank" href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/MofoChart.java">src/java/nxt/MofoChart.java</a><br>
<a target="_blank" href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/MofoChartWindow.java">src/java/nxt/MofoChartWindow.java</a>

<b>Samples of assets with large no of trades</b>

<a target="_blank" href="https://fimkrypto.github.io/mofo/launch.html#/assets/nxt/4551058913252105307/trade">mgwbtc</a><br>
<a target="_blank" href="https://fimkrypto.github.io/mofo/launch.html#/assets/nxt/12071612744977229797/trade">supernet</a><br>
<a target="_blank" href="https://fimkrypto.github.io/mofo/launch.html#/assets/nxt/18128686802152832026/trade">nxtycoin</a>
