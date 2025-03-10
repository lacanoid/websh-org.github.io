[websh.org](/) / [packages](..) / **remote-slave-port**

# @websh/remote-slave-port

**[https://github.com/websh-org/remote-slave-port](https://github.com/websh-org/remote-slave-port)**

Slave port for async cross-iframe messaging. Load this in an iframe.

See [remote-master-port](remote-master-port) for the other side of the channel (in the parent window).

The master port must innitiate the connection. 

- [Synopsis](#synopsis)
- [Methods](#methods)
  - [`.manifest( Object manifest )`](#manifest-object-manifest-)
  - [`.command( String command, Function( Object args ) fn )`](#command-string-command-function-object-args--fn-)
  - [`.on( String event, Function( Object data ) fn )`](#on-string-event-function-object-data--fn-)
  - [`.trigger( String event, Object data )`](#trigger-string-event-object-data-)
- [TODO: Events](#todo-events)
  - [`connected`](#connected)
  - [`disconnected`](#disconnected)
  - [`timeout`](#timeout)

## Synopsis
````bash
$ npm install @websh/remote-slave-port
````

````js
import { RemoteSlavePort } from "@websh/remote-slave-port";

// the master port in the parent window must use 
// the same channelId to establish a channel
const channelId = "my-channel"; 

const mySlavePort = new RemoteSlavePort(channelId);
````

## Methods

All methods return the MasterSlavePort object, so you can chain method calls.

### `.manifest( Object manifest )`
Register the slave's manifest. This will be sent to the master
on connection.

### `.command( String command, Function( Object args ) fn )`
Register a command to be called from the master port.
Any value returned from the function will be sent back to the master port.
The function can be async.

### `.on( String event, Function( Object data ) fn )`

Handle an event on the slave port. See Events.

### `.trigger( String event, Object data )`
Trigger an event that will be sent to the master port

## TODO: Events
### `connected`
Triggered when connected.
### `disconnected`
Triggered when disconnected.
### `timeout`
Triggered when no connection request was received from the master.
