# firebase-authentication-short-node

## Projects Setting----->

### install firebase

```js

npm install firebase

```

### Create a file `firebase.config.js` and export `auth`--->


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

export const auth = getAuth(app);

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

# Authentication---->

### Create a file `AuthProvider.jsx`------->

```js

const AuthProvider =() =>{
     return (
        <div>
          
        </div>
    );
}

export default AuthProvider;

```

### create `AuthContext` and `children` props ------->

```js
//-------------------import element--------
import { createContext} from "react";


//------create AuthContext--------
export const AuthContext = createContext(null);

const AuthProvider =({children}) =>{
     return (
         <AuthContext.Provider>
            {children}
        </AuthContext.Provider>
    );
}

export default AuthProvider;

```