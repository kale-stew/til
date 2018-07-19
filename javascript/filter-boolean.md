# Filtering Arrays in a Readable Way

Have you ever found yourself writing out one of these if / else statements to assemble an array of calculated values?

```js
const isAdmin = readRoles.isAdmin(req);
const WHITELIST = [okFlag, anotherOkFlag];

if (isAdmin) {
  WHITELIST.push(sensitiveFlag, otherSensitiveFlag);
} else {
  WHITELIST.push(customerOnlyFlag);
}
```

> _There's gotta be a better way!_

Using `.filter(Boolean)`, you can drill down to constants that only resolve to a defined value, shaking out all `null` and `undefined`s.

```js
const WHITELIST = [
  // add flags that only an admin should be able to update
  isAdmin ? sensitiveFlag : null,
  isAdmin ? otherSensitiveFlag : null,

  // add flags that are always accessible
  okFlag,
  anotherOkFlag,

  // add flags that only a customer should be able to update
  !isAdmin ? customerOnlyFlag : null
].filter(Boolean); // <-- get rid of the null values!
```

And there it is! Shoutout to [Kent C. Dodds](https://medium.com/@kentcdodds) for [tweeting](https://twitter.com/kentcdodds/status/1009918457394225152) this handy tip out and making my life a little easier.
