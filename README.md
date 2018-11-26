# LDAPjs

[!['Build status'][travis_image_url]][travis_page_url]
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FLiquidInCa%2Fnode-ldapjs.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2FLiquidInCa%2Fnode-ldapjs?ref=badge_shield)

[travis_image_url]: https://api.travis-ci.org/mcavage/node-ldapjs.svg
[travis_page_url]: https://travis-ci.org/mcavage/node-ldapjs

LDAPjs makes the LDAP protocol a first class citizen in Node.js.

## Usage

For full docs, head on over to <http://ldapjs.org>.

```javascript
var ldap = require('ldapjs');

var server = ldap.createServer();

server.search('dc=example', function(req, res, next) {
  var obj = {
    dn: req.dn.toString(),
    attributes: {
      objectclass: ['organization', 'top'],
      o: 'example'
    }
  };

  if (req.filter.matches(obj.attributes))
  res.send(obj);

  res.end();
});

server.listen(1389, function() {
  console.log('ldapjs listening at ' + server.url);
});
```

To run that, assuming you've got the [OpenLDAP](http://www.openldap.org/)
client on your system:

    ldapsearch -H ldap://localhost:1389 -x -b dc=example objectclass=*

## Installation

    npm install ldapjs

## License

MIT.


[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FLiquidInCa%2Fnode-ldapjs.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FLiquidInCa%2Fnode-ldapjs?ref=badge_large)

## Bugs

See <https://github.com/mcavage/node-ldapjs/issues>.