# Strophe.storage.js

Strophe.storage.js implements XML Private Storage:
[XEP-0049](http://xmpp.org/extensions/xep-0049.html)

## Usage

Every stored object is represented by an XML element qualified by a namespace.
The object is stored with `set()` and retrieved with `get()`. Both methods
return Promise objects that resolve to the response stanzas.

    const data = $build('exodus', {xmlns: 'exodus:prefs'})
      .c('defaultnick', {}, 'Hamlet');
    connection.storage.set(data);

    connection.storage.get('exodus', 'exodus:prefs').then((stanza) => {
      const nick = stanza.querySelector('query exodus defaultnick').textContent;
      client.setNickName(nick);
    })
