---
layout: post
title:  "Asynchronous RPC interface"
date:   2015-03-30 22:00:00
---
Where the existing NXT API is synchronous the NXT-PLUS RPC interface is asynchronous. Calling any RPC method will not immediately give back a result, instead you provide a call identifier and register an event listener with the WebSocket.

Since RPC calls happen over already establised WebSocket connections they are much faster than using the existing NXT API server.

For an overview of available RPC calls see <a href="https://github.com/fimkrypto/nxt-plus/tree/master/src/java/nxt/http/rpc">https://github.com/fimkrypto/nxt-plus/tree/master/src/java/nxt/http/rpc</a> a formal description is highly desired but unfortunately not ready.

See our blog post for background information <a href="http://fimkchat.com/2015/03/connecting-to-fimk-websockets/">http://fimkchat.com/2015/03/connecting-to-fimk-websockets/</a>. The samples in the blog are for FIMK but apply equally to NXT-PLUS.