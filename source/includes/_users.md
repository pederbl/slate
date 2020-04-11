# Users

## List users

> To list users, use this code:

```shell
curl "https://api.customizeyourdemo.com/v1/users"
  -H "Content-Type: application/json"
  -H "Authorization: Bearer YOUR_JWT_TOKEN_HERE"
  -d '{ "users": { "limit": 3 }}'
```

```javascript
const cydemo = require('customizeyourdemo')(YOUR_JWT_TOKEN_HERE);

cydemo.users.list({
    limit: 3
  }, (err, data) => {
    // YOUR CODE HERE
});

```

> The response data is JSON structured like this:

```json
{
  "object": "list",
  "has_more": false,
  "data": [
    {
      "id": 1,
      "first_name": "Joe",
      "last_name": "Smith",
      "mobile_phone": "+1.555.555555",
      "email": "joe@example.com", 
      "mobile_phone_verified": true, 
      "email_verified": false 
    },
    { ... },
    { ... }
  ]
}
```

Retrievs a list of users. 

Only users that are members of organizations that the authenticated user is member of will be retrieved.  

### HTTP Request

`GET https://api.customizeyourdemo.com/v1/users`

### Query Parameters

Parameter | Type | Required | Default | Description
--------- | ---- |-------- | ------- | ------
filter.ids | array of integers | No | null | Only return users with the given IDs.
filter.member_of | array of integers |  No | null | Only return users that are members of the organizations with one of the specified IDs.
paginate.limit | integer |  No | 10 | A limit on the number of objects to be returned. Limit can range between 1 and 100.
paginate.ending_before | integer |  No | null | A cursor for use in pagination. `ending_before` is an object ID that defines your place in the list. For instance, if you make a list request and receive 100 objects, starting with `obj_bar`, your subsequent call can include `paginate.ending_before=obj_bar.id` in order to fetch the previous page of the list.
paginate.starting_before | integer |  No | null | A cursor for use in pagination. `starting_after` is an object ID that defines your place in the list. For instance, if you make a list request and receive 100 objects, ending with `obj_foo`, your subsequent call can include `starting_after=obj_foo.id` in order to fetch the next page of the list.


## Retrieve a user

```shell
curl "https://api.customizeyourdemo.com/v1/users/1"
  -H "Content-Type: application/json"
  -H "Authorization: Bearer YOUR_JWT_TOKEN_HERE"
```

```javascript
const cydemo = require('customizeyourdemo')(YOUR_JWT_TOKEN_HERE);

cydemo.users.retrieve(1, (err, data) => {
    // YOUR CODE HERE
});
```

> The response data is JSON structured like this:

```json
{
  "object": "user",
  "data": {
    "id": 1,
    "first_name": "Joe",
    "last_name": "Smith",
    "mobile_phone": "+1.555.555555",
    "email": "joe@example.com", 
    "mobile_phone_verified": true, 
    "email_verified": false 
  }
}
```

Retrieves the details of the user with the specified ID.

### HTTP Request

`GET https://api.customizeyourdemo.com/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve.

## Update a user

```shell
curl "https://api.customizeyourdemo.com/users/1"
  -X PUT  
  -H "Content-Type: application/json"
  -H "Authorization: Bearer YOUR_JWT_TOKEN_HERE"
```

```javascript
const cydemo = require('customizeyourdemo')(YOUR_JWT_TOKEN_HERE);

cydemo.users.update({
  first_name: "Joey",
  last_name: "Smith"  
}, (err, data) => {
    // YOUR CODE HERE
});
```

> The above command returns JSON structured like this:

```json
{
  "object": "user",
  "data": {
    "id": 1,
    "first_name": "Joey",
    "last_name": "Smith",
    "mobile_phone": "+1.555.555555",
    "email": "joe@example.com", 
    "mobile_phone_verified": true, 
    "email_verified": false 
  }
}
```

Updates the user with the specified ID.

### HTTP Request

`PUT https://api.customizeyourdemo.com/v1/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to update.

### Query Parameters

Parameter | Type | Required | Default | Description
--------- | ---- |-------- | ------- | ------
first_name | string | No | null | The new value for this field.
last_name | string | No | null | The new value for this field.
