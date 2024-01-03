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
export const app = initializeApp(firebaseConfig);



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

### create 2 state and value ------->

```js
//-------------------import element--------
import { createContext,useState} from "react";


//------create AuthContext--------
export const AuthContext = createContext(null);

const AuthProvider =({children}) =>{
 
           //-----state------
     const [user, setUser] = useState(null)
    const [loading, setLoading] = useState(true)

    const authInfo = {
        user,
        loading
        
    }

     return (
         <AuthContext.Provider value={authInfo}>
            {children}
        </AuthContext.Provider>
    );
}

export default AuthProvider;

```

### import `app` from `firebase.config` and `getAuth` from `from firebase/auth` ------->

```js
//-------------------import element--------
import { createContext,useState} from "react";
import { app } from '../firebase/firebase.config'
import {getAuth} from 'firebase/auth'

//------create AuthContext--------
export const AuthContext = createContext(null);
const auth = getAuth(app);

const AuthProvider =({children}) =>{
 
           //-----state------
     const [user, setUser] = useState(null)
    const [loading, setLoading] = useState(true)

    const authInfo = {
        user,
        loading
        
    }

     return (
         <AuthContext.Provider value={authInfo}>
            {children}
        </AuthContext.Provider>
    );
}

export default AuthProvider;

```

## Create a user with `emailAndPassword` ------->

## create a arrow function and import `createUserWithEmailAndPassword` from `firebase/auth` and 2 props `email,password` pass and `auth` . Then pass the function of value

```js
//-------------------import element--------
import { createContext,useState} from "react";
import { app } from '../firebase/firebase.config'
import {
    getAuth,
    createUserWithEmailAndPassword
    } from 'firebase/auth'

//------create AuthContext--------
export const AuthContext = createContext(null);
const auth = getAuth(app);

const AuthProvider =({children}) =>{
 
           //-----state------
     const [user, setUser] = useState(null)
    const [loading, setLoading] = useState(true)


     // createUser
    const createUser = (email, password) => {
        setLoading(true)
        return createUserWithEmailAndPassword(auth,email, password)
    }

    const authInfo = {
        user,
        loading,
        createUser
        
    }

     return (
         <AuthContext.Provider value={authInfo}>
            {children}
        </AuthContext.Provider>
    );
}

export default AuthProvider;

```