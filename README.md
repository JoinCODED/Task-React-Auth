Here's a starting point with a signin and signup modals ready for you to use and implement authentication

Fork and clone [this](https://github.com/JoinCODED/Task-React-Auth)

# Signup

1- Create a new store that will be responsible for authentication. Let's call it `authStore.js`.

2- In your `AuthStore` class, create a method called `signup`. This method takes the `userData` as an argument and sends a request to the `/signup` endpoint and passes `userData` in the `body` of the request.

3- Back to `SignupModal`. Create a `handleSubmit` method that calls `authStore.signup` and pass it `user` as an argument.

4- Pass `handleSubmit` to the `form`'s `onSubmit` event.

# Signin

1- In your `authStore` class, create a method called `signin`. This method takes the `userData` as an argument and sends a request to the `/signin` endpoint and passes `userData` in the body of the request. When logging in, we expect the token as a response. Let's console log it for now.

2- Back to `SigninModal`. Change the `handleSubmit` method to call `authStore.signin` and pass it `user` as an argument.

3- Try logging in and check your console.

4- Install `jwt-decode` which is a library that can decode tokens.

5- Import `decode` from `jwt-decode` which is a function that takes a token as an argument and returns the decoded object.

6- Pass the token in `res.data` to `jwt-decode` and let's console log it.

7- create a new property in our store called `user`. `user`'s initial value is `null`, which basically mean that no user is logged in.

8- In `signin`, we will save the decoded token in `this.user`.

# Signin After Signup

1- In `authStore`'s `signup` method, save the response, and pass the token the `decode` method, and save the return value in `this.user`.

# Pass The Token

1- In `authStore`'s `signin` method, after receiving the token in the response, we will save it in our `axios`'s instance.

2- Do the same thing in `signup`.

3- The code is becoming very repeated, create a function called `setUser` in `AuthStore` that takes a `token` as an argument, saves it in the headers, decodes it and saves the decoded object in `this.user`.

4- Call this method in `signin` and `signup` methods and pass it the token.

# Logout

1- You have a component called `LogoutButton.js` , render it under the `NavBar` so that it will only show if the user is logged in.

2- In `authStore`, create a `signout` method. But how can you logout the user? By setting `this.user` to `null` and deleting the token from the `instance` headers.

3- In the button's `onClick` event, call the `signout` method.

# Persistent Login

1- In your `setUser` method save your token in the `localStorage` using the `setItem` method.

2- Create a method called `checkForToken` in `authStore`, where you will fetch the token from the local storage.

3- Call this function right after creating your store.

4- Back to the `checkForToken` method, check if the token exists, if it does, make sure it's not expired. If it's not,pass the token to `this.setUser` else, call `this.signout`.

5- If the token is expired you must delete it from our local storage. In `signout`, remove the token from the local storage.
