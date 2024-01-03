# firebase-authentication-short-node

## Projects Setting----->

### install firebase

```js

npm install firebase

```

### Create a file `firebase.config.js`--->


```js

// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: import.meta.env.VITE_APIKEY,
  authDomain: import.meta.env.VITE_AUTHDOMAIN,
  projectId: import.meta.env.VITE_PROJECTID,
  storageBucket: import.meta.env.VITE_STORAGEBUCKET,
  messagingSenderId: import.meta.env.VITE_MESSAGINGSENDERID,
  appId: import.meta.env.VITE_APPID
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);

```

### Create a file `.env.local`--->

```js

VITE_APIKEY="firebase_config"
VITE_AUTHDOMAIN="firebase_config"
VITE_PROJECTID="firebase_config"
VITE_STORAGEBUCKET="firebase_config"
VITE_MESSAGINGSENDERID="firebase_config"
VITE_APPID="firebase_config"

```