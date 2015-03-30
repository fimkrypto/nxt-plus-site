---
layout: post
title:  "RPC to existing API bridge"
date:   2015-03-30 21:00:00
---
The callAPIFunction RPC end point allows websocket RPC users to call methods in the existing server API.

The API server does not need to be started in order to call it's methods, calls are done in memory.

Until we have detailed documentation the source code is your friend.

<a target="_blank" href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/http/rpc/CallAPIFunction.java">src/java/nxt/http/rpc/CallAPIFunction.java</a>

See the sample below how to call the getBlocks API method over the RPC bridge from javascript. Click the Result tab to run the sample.

<iframe width="100%" height="300" src="//jsfiddle.net/dirkdiggler/5dorcz7t/embedded/js,html,result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>