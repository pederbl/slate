# Authentication

TESTING

The Customize Your Demo API uses JSON Web Tokens (JWT) to authenticate requests. The JWT token is fetched with a `get_jwt_token` request (see the Authentication section) with the email and password for the user requesting access. The JWT token must be supplied as a bearer in the Authorization header of each API request. Use `-H "Authorization: Bearer YOUR_JWT_TOKEN_HERE"`. 

The JWT token remains valid over time unless the invalidate_all_access_tokens action is called for a user. 

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail. Users that have not verified their mobile_phone or email are not authorized any other access. 

## Get JWT token

> To authenticate, use this code:

```shell
# Fetch the JWT-TOKEN
curl "https://api.customizeyourdemo.com/v1/authentication/get_jwt_token"
  -H "Content-Type: application/json"
  -d '{ "authentication": { "email": YOUR_EMAIL_HERE, "password": YOUR_PASSWORD_HERE }}'

# Pass the correct header with each request
curl "https://api.customizeyourdemo.com/v1/API_ENDPOINT_HERE"
  -H "Content-Type: application/json"
  -H "Authorization: Bearer THE_RETURNED_JWT_TOKEN_HERE>"
```

```javascript
const cydemo = require('customizeyourdemo');

cydemo.authentication.get_jwt_token({
    email: YOUR_EMAIL_HERE, 
    password: YOUR_PASSWORD_HERE
  }, (err, jwt_token) => {
    YOUR_CODE_HERE
});

```

Gets a JWT token for the specified user. 

### Query Parameters

Parameter | Type | Required | Description
--------- | ---- |-------- | ------
email | string | Yes | The email address of the user to fetch the JWT token for.
password | string | Yes | The password of the user to fetch the JWT token for.

### Error codes

Error | Description
----- | -----------
