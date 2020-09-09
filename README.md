# @dwebswarm/dwebsign

Utility methods related to public key cryptography to be used with distributed mutable storage.

```
npm install @dwebswarm/dwebsign
```

## API

#### `const { keypair, salt, sign, signable } = dwebsign()`

Call the exported function to get dwebsign instance.

There is also a class `dwebsign.DWebSign` which can be
extended.

#### `keypair()`

Use this method to generate an assymetric keypair.
Returns an object with `{publicKey, secretKey}`. `publicKey` holds a public key buffer, `secretKey` holds a private key buffer.

#### `salt([str, ]size = 32)`

Utility method for creating a random or hashed salt value.

If called with a string the string will be hashed, to a
generic hash of `size` length.

If called without any inputs, or with a number, random 
butes of `size` length will be generated.

#### `sign(value, options)`

Utility method which can be used to create a `sig`.

Options:

* `keypair` – REQUIRED, use `keypair` to generate this.
* `salt` - OPTIONAL - default `undefined`, a buffer >= 16 and <= 64 bytes. If supplied it will salt the signature used to verify mutable values.

#### `signable(value, options)`

Utility method which returns the exact buffer that would be signed in by `sign`. This is only needed when using a salt, otherwise it will return the same `value` passed in. This method is to facilitate out-of-band signing (e.g. hardware signing), do not pass the returned signable value into `sign`, it already uses `signable`.

Options:

* `salt` - OPTIONAL - default `undefined`, a buffer >= 16 and <= 64 bytes. If supplied it will salt the signature used to verify mutable values.

## License

MIT
