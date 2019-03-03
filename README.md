# swtc-x-address-codec

# Alphabet Soup

We currently serve these alphabets. Make a pull request if you'd like to add one
to the menu.

* ripple
* tipple
* bitcoin
* jingtum 
* bizain
* stellar

# API

```js
> var createHash = require('create-hash');
> var apiFactory = require('swtc-x-address-codec')
> var api = apiFactory({
... defaultAlphabet: 'jingtum',
... sha256: function(bytes) {
.....     return createHash('sha256').update(new Buffer(bytes)).digest();
.....   },
... codecMethods : {
.....     // public keys
.....     AccountID : {version: 0x00},
.....     // secrets
.....     Seed: {version: 0x21}
.....   },
...   // Why the hell don't we just export these versions too?
...   // Err.. Shutup :) We're getting to it.
... });
> var buf = new Buffer("00000000000000000000000000000000", 'hex');
> ar encoded = api.encodeSeed(buf);
> var encoded = api.encodeSeed(buf);
> var decoded = api.decodeSeed(encoded);
> var reencoded = api.encodeSeed(decoded)
> console.log(encoded)
sp6JS7f14BuwFY8Mw6bTtLKWauoUs
> console.log(reencoded);
sp6JS7f14BuwFY8Mw6bTtLKWauoUs
> console.log(decoded)
[ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ]
> console.log(api)
{ Codec: [Function: AddressCodec],
  codecs:
   { bitcoin:
      AddressCodec {
        alphabet: '123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz',
        codec: [Object],
        base: 58 },
     ripple:
      AddressCodec {
        alphabet: 'rpshnaf39wBUDNEGHJKLM4PQRST7VWXYZ2bcdeCg65jkm8oFqi1tuvAxyz',
        codec: [Object],
        base: 58 },
     tipple:
      AddressCodec {
        alphabet: 'RPShNAF39wBUDnEGHJKLM4pQrsT7VWXYZ2bcdeCg65jkm8ofqi1tuvaxyz',
        codec: [Object],
        base: 58 },
     jingtum:
      AddressCodec {
        alphabet: 'jpshnaf39wBUDNEGHJKLM4PQRST7VWXYZ2bcdeCg65rkm8oFqi1tuvAxyz',
        codec: [Object],
        base: 58 },
     bizain:
      AddressCodec {
        alphabet: 'bpshnaf39wBUDNEGHJKLM4PQRST7VWXYZ2jcdeCg65rkm8oFqi1tuvAxyz',
        codec: [Object],
        base: 58 },
     stellar:
      AddressCodec {
        alphabet: 'gsphnaf39wBUDNEGHJKLM4PQRST7VWXYZ2bcdeCr65jkm8oFqi1tuvAxyz',
        codec: [Object],
        base: 58 } },
  decode: [Function: decode],
  encode: [Function: encode],
  decodeAccountID: [Function],
  encodeAccountID: [Function],
  isValidAccountID: [Function],
  decodeSeed: [Function],
  encodeSeed: [Function],
  isValidSeed: [Function] }
```
