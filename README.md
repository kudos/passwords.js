# Passwords

Passwords is a standard and simple interface to cryptographic hashing for secure password storage.

It runs on node.js and io.js and is transparently compatible with traditional callbacks, promises and generators.

There is a companion library [written in Python](/kudos/passwords) which is compatible with the PBKDF2 hashes produced by this library.

## Why?

This is an attempt to make it easier for developers to find and use a cryptographic library suitable for password storage.

## Installation

Just `npm install passwords`.

If you want to run the tests, use `npm install passwords --development` and then run `npm test`.

If you're running non-harmony node.js, you'll need to `npm install bluebird` ot support promises, otherwise it will use the native `Promise` implementation.

## Usage

### Callbacks

    passwords.crypt('password', function (err, hash) {
      passwords.verify('password', hash, function (err, good) {
        assert(good);
      });
    });
    
### Promises

    return passwords.crypt('password').then(function (hash) {
      return passwords.verify('password', hash);
    }).then(function (good) {
      assert(good);
    });

### Generators
    
    const hash = passwords.crypt('password');
    assert(yield passwords.verify('password', hash));
