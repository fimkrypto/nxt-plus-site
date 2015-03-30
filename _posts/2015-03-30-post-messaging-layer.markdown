---
layout: post
title:  "Post/Blog meta layer"
date:   2015-03-30 18:00:00
---
Similar to how Counterparty is a protocol on-top of the bitcoin blockchain so is the post layer a protocol on top of the NXT blockchain.

Specially formatted AM messages trigger actions in the server core. Based on a message prefix messages are stored and indexed in special database tables to be accessible and searchable later.

Posts are linked to an account, asset, currency (not yet enabled) or goods (not yet enabled). Then when you visit that account or asset in the client you are shown the posts made by the owner of that account.

Looking up posts for an account is optimized by database indexes and client/server communication is improved by use of index based pagination.

<b>Examples of posts on the FIMK chain</b>

<a href="https://fimkrypto.github.io/mofo/launch.html#/accounts/FIM-5PGB-BFNZ-KCSF-9XJWB/pulse/latest">ACCOUNT POST EXAMPLE</a><br>
<a href="https://fimkrypto.github.io/mofo/launch.html#/assets/fim/13664938383416975974/pulse">ASSET POST EXAMPLE</a>

<b>WebSocket RPC</b>

Until we get better documentation the source code is your friend.

<a href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/http/rpc/GetAccountPosts.java">src/java/nxt/http/rpc/GetAccountPosts.java</a><br>
<a href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/http/rpc/GetAssetPosts.java">src/java/nxt/http/rpc/GetAssetPosts.java</a>

<b>Blockchain Listener</b>

<a href="https://github.com/fimkrypto/nxt-plus/blob/master/src/java/nxt/MofoMessaging.java">nxt/MofoMessaging.java</a>

<b>Protocol (not entirely accurate)</b>

<pre>/** 
 * MofoMessaging is a layer on top of Arbitrary Messages, if arbitrary messages
 * are prepended with a specific header they will count as MofoMessaging 
 * headers.
 * 
 * There are two types of MofoMessaging messages:
 * 
 *  1. posts
 *  2. comments
 *  
 * Posts defined.
 * 
 * A post is a message that has the same sender and recipient (message send to 
 * self) and which starts with the text 'post' followed by a single byte folowed 
 * by a ':' followed by an optional second identifier or followed by the post 
 * contents.
 * 
 * A so called ACCOUNT_POST has the following signature.
 * 
 * ['post']['1'][':'][.+]
 * 
 * While an ASSET_POST or CURRENCY_POST has an extra identifier for the asset or 
 * currency.
 * 
 * ['post']['2'-'127'][':'][asset or currency id][':'][.+] 
 * 
 * Comments defined.
 * 
 * A comment is a public message send to a post author and in direct reply to a 
 * post.
 * On disk a comment looks like 'comm' followed by a post id (transaction id)
 * followed by a ':' followed by the comment contents.
 * 
 * ['comm'][transaction id][':'][.+]
 */</pre>

 <b>Tests (pretty accurate)</b>

 <a href="https://github.com/fimkrypto/nxt-plus/blob/master/src/hack/nxt/PostAndCommentParserTest.java">hack/nxt/PostAndCommentParserTest.java</a>