---
title: Modchannels
aliases:
- /Modchannels
---

# Modchannels
Allows server side mods (SSMs) communication to client side mods (CSMs) and vice versa.

## Server Side API

### Functions

#### `core.mod_channel_join(channel_name)`
* `channel_name`: string, modchannel name

Returns an object for use with [Methods](#methods). Creates the channel if it does not exist and joins the channel.

#### `core.register_on_modchannel_message(function(channel_name, sender, message))`
* `channel_name`: string, modchannel name (already joined)
* `sender`: string, empty if from a SSM, player name if from a client
* `message`: string, message

Used for handling messages received from the client.

### Methods
{{< notice note >}}
`channel` here means the object returned by `core.mod_channel_join`.
{{< /notice >}}

#### `channel:leave()`
The server will leave the channel, meaning no more messages from this channel on `core.register_on_modchannel_message`

{{< notice tip >}}
Set the channel to `nil` afterwards to free resources
{{< /notice >}}

#### `channel:is_writeable()`
* Returns `bool`: `true` true if the channel is writeable, `false` if it's not.

#### `channel:send_all(message)`
* `message`: string, limited to 65535 bytes

Sends to all SSMs and CSMs on the channel.

{{< notice info >}}
The message will not if channel is not writable or invalid.
{{< /notice >}}

## Client Side API

### Functions

#### `core.mod_channel_join(channel_name)`
* `channel_name`: string, modchannel name

Returns an object for use with [Methods](#methods-1). Creates the channel if it does not exist and joins the channel. Is equivalent to the the server side function.

#### `core.register_on_modchannel_message(function(channel_name, sender, message))`
* `channel_name`: string, modchannel name (already joined and received acknowledgement)
* `sender`: string, empty if from a SSM, player name if from a client
* `message`: string, message

Used for handling messages received from the client. Is equivalent to the the server side function.

#### `core.register_on_modchannel_signal(function(channel_name, signal))`
* `channel_name`: string, channel name that the signal has come in on
* `signal`: integer, 0 - 5

	0. `join_ok`
	1. `join_failed`
	2. `leave_ok`
	3. `leave_failed`
	4. `event_on_not_joined_channel`
	5. `state_changed`

Used to handle signals generated by the mod channel system.

### Methods
{{< notice note >}}
`channel` here means the object returned by `core.mod_channel_join`.
{{< /notice >}}

#### `channel:leave()`
The client will leave the channel, meaning no more messages from this channel on `core.register_on_modchannel_message`

{{< notice tip >}}
Set the channel to `nil` afterwards to free resources
{{< /notice >}}

#### `channel:is_writeable()`
* Returns `bool`: `true` true if the channel is writeable, `false` if it's not.

#### `channel:send_all(message)`
* `message`: string, limited to 65535 bytes

Sends to all SSMs and CSMs on the channel.

{{< notice info >}}
The message will not if channel is not writable or invalid.
{{< /notice >}}