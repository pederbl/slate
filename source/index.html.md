---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - users

search: true
---

# Welcome to The Customize Your Demo API!

The Customize Your Demo API is organized around REST. Our API has predictable resource-oriented URLs, accepts JSON-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

We have language bindings in Shell and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# Fetch the JWT-TOKEN
curl "https://api.customizeyourdemo.com/sign_in"
  -H "Content-Type: application/json"
  -d '{ "authentication": { "email": YOUR_EMAIL_HERE, "password": YOUR_PASSWORD_HERE }}'

# Pass the correct header with each request
curl "https://api.customizeyourdemo.com/API_ENDPOINT_HERE"
  -H "Content-Type: application/json"
  -H "Authorization: Bearer <THE RETURNED JWT-TOKEN>"
```

```javascript
const cydemo = require('customizeyourdemo');

let jwt_token = cydemo.get_jwt_token(email, password);

cydemo.<api_call_here>(jwt_token);
```

The Customize Your Demo API uses JSON Web Tokens (JWT) to authenticate requests. The JWT token is fetched with a sign-in request with the email and password for the user requesting access. The JWT token must be supplied as a bearer in the Authorization header of each API request. Use -H "Authorization: Bearer YOUR_JWT_TOKEN_HERE". 

The JWT token remains valid over time unless: the reject_tokens_issued_before setting for the user is set to a later time than the JWT token was issued at.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail. Users that have not verified their mobile_phone or email are not authorized any other access. 

