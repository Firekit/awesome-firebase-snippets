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

- [Multi-Tab Offline Support in Cloud Firestore](https://firebase.googleblog.com/2018/09/multi-tab-offline-support-in-cloud.html)
