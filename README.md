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

```html
<!-- Resource Hints -->
<!-- https://github.com/Firekit/awesome-firebase-snippets -->
<!-- Preconnect for FirebaseUI. -->
<link rel="preconnect" href="https://PROJECT_ID.firebaseapp.com">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://www.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com">
<link rel="preconnect" href="https://www.gstatic.com">
<link rel="preconnect" href="https://apis.google.com">
<!-- Preconnect for Facebook Login. -->
<link rel="preconnect" href="https://platform-lookaside.fbsbx.com">
<!-- Preconnect for user photos. -->
<link rel="preconnect" href="https://lh1.googleusercontent.com">
<link rel="preconnect" href="https://lh2.googleusercontent.com">
<link rel="preconnect" href="https://lh3.googleusercontent.com">
<link rel="preconnect" href="https://lh4.googleusercontent.com">
<link rel="preconnect" href="https://lh5.googleusercontent.com">
<link rel="preconnect" href="https://lh6.googleusercontent.com">
<link rel="preconnect" href="https://lh7.googleusercontent.com">
<link rel="preconnect" href="https://lh8.googleusercontent.com">
<link rel="preconnect" href="https://lh9.googleusercontent.com">
<!-- Preconnect for Firebase Storage. -->
<link rel="preconnect" href="https://firebasestorage.googleapis.com">
```
[source](https://github.com/firebase/friendlypix-web/blob/master/src/index.html)

```js
// Firebase Push ID generator
// via https://gist.github.com/mikelehen/3596a30bd69384624c11
export const generatePushID = (() => {
  // Modeled after base64 web-safe chars, but ordered by ASCII.
  const PUSH_CHARS =
    '-0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ_abcdefghijklmnopqrstuvwxyz';

  // Timestamp of last push, used to prevent local collisions if you push twice in one ms.
  let lastPushTime = 0;

  // We generate 72-bits of randomness which get turned into 12 characters and appended to the
  // timestamp to prevent collisions with other clients.  We store the last characters we
  // generated because in the event of a collision, we'll use those same characters except
  // "incremented" by one.
  const lastRandChars = [];

  return () => {
    let now = new Date().getTime();
    const duplicateTime = now === lastPushTime;
    lastPushTime = now;

    const timeStampChars = new Array(8);
    let i;
    for (i = 7; i >= 0; i -= 1) {
      timeStampChars[i] = PUSH_CHARS.charAt(now % 64);
      // NOTE: Can't use << here because javascript will convert to int and lose the upper bits.
      now = Math.floor(now / 64);
    }
    if (now !== 0)
      throw new Error('We should have converted the entire timestamp.');

    let id = timeStampChars.join('');

    if (!duplicateTime) {
      for (i = 0; i < 12; i += 1) {
        lastRandChars[i] = Math.floor(Math.random() * 64);
      }
    } else {
      // If the timestamp hasn't changed since last push, use the same random number, except incremented by 1.
      for (i = 11; i >= 0 && lastRandChars[i] === 63; i -= 1) {
        lastRandChars[i] = 0;
      }
      lastRandChars[i] += 1;
    }
    for (i = 0; i < 12; i += 1) {
      id += PUSH_CHARS.charAt(lastRandChars[i]);
    }
    if (id.length !== 20) throw new Error('Length should be 20.');

    return id;
  };
})();
```

- [Multi-Tab Offline Support in Cloud Firestore](https://firebase.googleblog.com/2018/09/multi-tab-offline-support-in-cloud.html)
- [How to improve performance of a Firebase web app](https://github.com/hsubox76/fireconf-demo)
