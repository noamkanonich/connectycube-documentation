# ConnectyCube Documentation

## Initialize ConnectyCube App
Initialize framework with your ConnectyCube application credentials. <br /> 
You can access your application credentials in ConnectyCube Dashboard:

### Code
```javascript
const CREDENTIALS = {
  appId: 21,
  authKey: "hhf87hfushuiwef",
  authSecret: "jjsdf898hfsdfk",
};

ConnectyCube.init(CREDENTIALS);
```

### API

### Response


## Create a session
For using the ConnectyCube API, user needs a session token, which provides a secure access to ConnectyCube API. <br />
To create an application session use the following code::

### Create Application Session
```javascript
ConnectyCube.createSession()
  .then((session) => {})
  .catch((error) => {});
```

### Response
```javascript
{
  "application_id": 1,
  "created_at": "2018-10-01T10:47:01Z",
  "device_id": null,
  "id": 151,
  "nonce": 4214611091,
  "token": "5a7bc95d85c0eb2bf052be3d29d3df523081e80y",
  "ts": 1542560252,
  "updated_at": "2018-10-01T10:47:01Z",
  "user_id": null
}
```

### Create User Session
```javascript
const userCredentials = { login: "cubeuser", password: "awesomepwd" };

ConnectyCube.createSession(userCredentials)
  .then((session) => {})
  .catch((error) => {});
```

### Response
```javascript
{
  "id": 152,
  "user_id": 81,
  "application_id": 1,
  "nonce": 4214611091,
  "token": "83153a14fb2df777c2f866178902a4bb15000001",
  "ts": 1544010993,
  "created_at": "2018-12-05T11:58:02Z",
  "updated_at": "2018-12-05T11:58:02Z",
  "user": {
    "id": 81,
    "full_name": "John Smith",
    "email": "johnsmith@domain.com",
    "login": "john",
    "phone": "380665787842",
    "website": null,
    "created_at": "2018-06-15T14:20:54Z",
    "updated_at": "2018-12-05T11:58:02Z",
    "last_request_at": "2018-12-05T11:58:02Z",
    "external_user_id": null,
    "facebook_id": null,
    "twitter_id": null,
    "custom_data": "",
    "blob_id": null,
    "avatar": "",
    "user_tags": null
  }
```



## User Sign Up
User will sign up to connecty cube user list that connects with the our application

### Code
```javascript
const userProfile = {
  login: "marvin18",
  password: "supersecurepwd",
  email: "awesomeman@gmail.com",
  full_name: "Marvin Simon",
  phone: "47802323143",
  website: "https://dozensofdreams.com",
  tag_list: ["iphone", "apple"],
  custom_data: JSON.stringify({ middle_name: "Bartoleo" })
};

ConnectyCube.users
  .signup(userProfile)
  .then((user) => {})
  .catch((error) => {});
```

### API

### Response
```javascript
{
  "id": 81,
  "full_name": "Marvin Simon",
  "email": "awesomeman@gmail.com",
  "login": "marvin18",
  "phone": "47802323143",
  "website": "https://dozensofdreams.com",
  "created_at": "2018-06-15T14:20:54Z",
  "updated_at": "2018-12-05T11:58:02Z",
  "last_request_at": "2018-12-05T11:58:02Z",
  "external_user_id": null,
  "facebook_id": null,
  "twitter_id": null,
  "custom_data": "{\"middle_name\":\"Bartoleo\"}",
  "blob_id": null,
  "avatar": "",
  "user_tags": "iphone,apple"
}
```

## User Sign In (Login)
If you have an application session, you can upgrade it to a user session by calling login method. <br />
This login method will create a user session and make the user logged in.
If the user is not registered to connecty cube, it will be added to user list.


### Code
```javascript
const userCredentials = { login: "cubeuser", password: "awesomepwd" };
// const userCredentials = { email: 'cubeuser@gmail.com', password: 'awesomepwd' };
// const userCredentials = { provider: 'facebook', keys: {token: 'a876as7db...asg34dasd8wqe'} };

ConnectyCube.login(userCredentials)
  .then((user) => {})
  .catch((error) => {});
```

### API

### Response
```javascript
{
  "id": 47592,
  "full_name": "John Smith",
  "email": "johnsmith@gmail.com",
  "login": "johnsmith",
  "phone": null,
  "website": null,
  "created_at": "2018-11-23T09:42:36Z",
  "updated_at": "2018-12-06T07:56:26Z",
  "last_request_at": "2018-12-06T07:59:22Z",
  "external_user_id": null,
  "facebook_id": null,
  "twitter_id": null,
  "blob_id": null,
  "custom_data": null,
  "avatar": null,
  "user_tags": null
}
```
















