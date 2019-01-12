# Awesome Firebase JavaScript Snippets

```js
// Encode firebase key string to escape unsafe characters (.$[]#/).
// https://github.com/Firekit/awesome-firebase-snippets
const key = encodeURIComponent('https://github.com').replace(/\./g, '%2E');
```
[source](https://stackoverflow.com/a/19148116/1614237)

```js
// Check if a Firebase App is already initialized.
// https://github.com/Firekit/awesome-firebase-snippets
if (!firebase.apps.length) {
  firebase.initializeApp({});
}
```
[source](https://stackoverflow.com/a/41005100/1614237)
