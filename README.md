# Contact Keeper API

This project was built as part of [@bradtraversy](https://github.com/bradtraversy)'s Modern React Front to Back course on Udemy.

This is a Node/Express/MongoDB REST API for contacts that uses JWT authentication. All contact endpoints are protected and each registered user has their own contacts.

## Getting started

Open the config/default.json file and add your mongoURI and jwtSecret.

### `npm install`

Installs dependencies in local node_modules folder.

### `npm run server`

Runs the app in the development mode on [http://localhost:3000](http://localhost:5000).

## API Usage and Endpoints

### Register a user [POST /api/users]

**Request**: Add user and request JWT
Headers:

```bash
Content-type: application/json
```

Body:

```bash
    {
      "name": "Jack Sparrow",
      "email": "jack@test.com",
      "password": "123456"
    }
```

**Response**: 200 (application/json)
Body:

```bash
    {
      "token": ""
    }
```

### Login a user [POST /api/auth]

**Request**: Login user and receive JWT
Headers:

```bash
Content-type: application/json
```

Body:

```bash
    {
      "email": "jack@test.com",
      "password": "123456"
    }
```

**Response**: 200 (application/json)
Body:

```bash
    {
      "token": ""
    }
```

### Get contacts for a user [GET /api/contacts]

**Request**: Get contacts for logged in user
Headers:

```bash
x-auth-token: USER_JWT
```

**Response**: 200 (application/json)
Body:

```bash
    {
      "contacts": []
    }
```

### Add a new contact [POST /api/contacts]

**Request**: Add a new contact
Headers:

```bash
Content-type: application/json
x-auth-token: USER_JWT
```

Body:

```bash
    {
      "name": "Anne Bonny",
      "email": "abonny@test.com",
      "phone": "",
      "type": "" (personal or professional)
    }
```

**Response**: 200 (application/json)
Body:

```bash
    {
      "contact": {}
    }
```

### Update a contact [PUT /api/contacts/:id]

**Request**: Update an existing contact
Parameters:

```bash
id: 123 (unique id of the contact)
```

Headers:

```bash
Content-type: application/json
x-auth-token: USER_JWT
```

Body:

```bash
    {
      "name": "",
      "email": "",
      "phone": "",
      "type": "" (personal or professional)
    }
```

**Response**: 200 (application/json)
Body:

```bash
    {
      "contact": {}
    }
```

### Delete a contact [DELETE /api/contacts/:id]

**Request**: Delete an existing contact

Parameters:

```bash
id: 123 (unique id of the contact)
```

Headers:

```bash
x-auth-token: USER_JWT
```

**Response**: 200 (application/json)
Body:

```bash
    {
      "msg": "Contact deleted
    }
```

## Technologies

- [NodeJS](https://nodejs.org)
- [MongDB Atlas](https://www.mongodb.com/cloud/atlas) - Cloud database service
- [Express](https://expressjs.com/) - Web framework
- [Postman](https://www.getpostman.com) - For testing API endpoints
- Dependencies:
  - bcryptjs - For hashing passwords
  - jsonwebtoken - For authentication using JWTs
  - config - For global variables
  - express-validator - For data validation
  - mongoose - Abstraction layer, model creation
  - nodemon - Dev server monitoring utility
  - concurrently - Run front and back end servers concurrently
