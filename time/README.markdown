# Strophe.time.js

Strophe.time.js is a plugin to provide Entity Time
( [ XEP-0202 ]( http://xmpp.org/extensions/xep-0202.html ) ).

## Requirements

This plugin uses the Moment.js library (http://momentjs.com/).

## Usage

Request the local time from another client or server:

    connection.time.getTime( "serviceJID@server.org", timeout );

This returns a Promise that will resolve to the response stanza.

You can also add a handler to respond to time requests:

    connection.time.addTimeHandler( handler );

The sendTime() function will send the appropriate response to a time request.

    handler = function( request ){
      ...
      connection.time.sendTime( request );
      ...
	  return true;
    }
