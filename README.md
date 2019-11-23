# Boilerplate app
## Description
This is a frontend development boilerplate project. It is based on:
1. React + Redux
2. Testing with Jest
3. DB connection using Firebase
4. Google authentication
5. SCSS styling
6. ...and a lot of configured settings, like @babel/polyfill, history, CSS normalization, extended ES6 features, etc.
## How to connect to the Firebase
1. Create 2 new applications in Firebase (test and development).
2. Turn on Google Authentication in each project.
3. Create a Realtime-Database with the following rules in each project:
```json
{
  "rules": {
    ".read": false,
    ".write": false,
    "users": {
      "$user_id": {
        ".read": "$user_id === auth.uid",
        ".write": "$user_id === auth.uid",
        /* Insert project specific fields validations here */
        "$other": {
          ".validate": false
        }
      }
    }
  }
}
```
4. Create 2 files in a root of a project with the following names:
    1. `.env.test` - contains database settings for automation tests purposes.
    2. `.env.development` - contains database settings for development purposes.

Example of `.env.*` file:
```bash
FIREBASE_API_KEY="some-key"
FIREBASE_AUTH_DOMAIN="project-id.firebaseapp.com"
FIREBASE_DATABASE_URL="https://project-id.firebaseio.com"
FIREBASE_PROJECT_ID="project-id"
FIREBASE_STORAGE_BUCKET="project-id.appspot.com"
FIREBASE_MESSAGING_SENDER_ID="1234567890"
FIREBASE_APP_ID="app-id"
FIREBASE_MEASUREMENT_ID="some-id"
```