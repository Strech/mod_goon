Ejabberd mod_goon
=================

This is exactly the same as original ejabberd mod_ping, except one thing — now you can define your own delay for timeout_action

**Problem description:** http://jabber.996255.n3.nabble.com/mod-ping-and-32-second-respons-td23300.html

**Ejabberd mod_ping configuration:** https://git.process-one.net/ejabberd/mainline/blobs/raw/v2.1.11/doc/guide.html#htoc51

## Extended mod_goon configuration options:

`{action_delay, MilliSeconds}`

How many time to wait before trigger timeout_action callback.

## Example

This example enables Ping responses, configures the module to send pings to client connections that are inactive for 4 minutes, and if a client does not answer to the ping in less than 7 seconds, its connection is closed

```
{modules,
 [
  ...
  {mod_goon,  [{send_pings, true}, {ping_interval, 240}, {timeout_action, kill}, {action_delay, 7000}]},
  ...
 ]}.
```