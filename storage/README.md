# Strophe.storage.js

Strophe.storage.js implements XML Private Storage:
[XEP-0049](http://xmpp.org/extensions/xep-0049.html)

## Usage

Every stored object is represented by an XML element qualified by a namespace.
The object is stored with `set()` and retrieved with `get()`. Both methods
return Promise objects that resolve to the response stanzas.

    connection.storage.set('exodus', 'exodus:prefs')
      .c('defaultnick', {}, 'Hamlet');
      .send(timeout)
      .then(() => {
        console.log("Saved");
      });

    connection.storage.get('exodus', 'exodus:prefs', timeout)
      .then((stanza) => {
        const nick = stanza.querySelector('query exodus defaultnick').textContent;
        client.setNickName(nick);
        console.log("Loaded");
      })
