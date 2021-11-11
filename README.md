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


## Authentication via external identity provider



### Code
```javascript

```

### API

### Response
```javascript

```



## Delete User
A user can delete himself from the platform:


### Code
```javascript
ConnectyCube.users
  .delete()
  .then((result) => {})
  .catch((error) => {});
```

### API

### Response
```javascript

```


## Connect To Chat
In order for user to use the connectycube chat api, you need to setup real-time connection with ConnectyCube Chat server and use it to exchange data.

### Code
```javascript
const userCredentials = {
  userId: 4448514,
  password: "awesomepwd",
};

ConnectyCube.chat
  .connect(userCredentials)
  .then(() => {
    // connected
  })
  .catch((error) => {});
```

### API

### Response
```javascript
```

## Create Dialog (Group Chat)
You need to pass type: 2 and ids of opponents you want to create a chat with:

### Code
```javascript
const params = {
  type: 2,
  name: "Friday party",
  occupants_ids: [29085, 29086, 29087],
  description: "lets dance the night away",
  photo: "party.jpg",
};

ConnectyCube.chat.dialog
  .create(params)
  .then((dialog) => {})
  .catch((error) => {});
```

### Endpoint
POST https://api.connectycube.com/chat/Dialog

### Request Example
```javascript
curl -X POST \
-H "Content-Type: application/json" \
-H "CB-Token: <TOKEN>" \
-d '{"type":2,"name":"Friday party","occupants_ids":"29085,29086,29087","description":"lets dance the night away","photo":"party.jpg"}' \
https://api.connectycube.com/chat/Dialog
```

### Response
```javascript
{
  "_id": "5c091060e588ce59fdf873dc",
  "admins_ids": [],
  "created_at": "2018-12-06T12:04:48Z",
  "description": "lets dance the night away",
  "last_message": null,
  "last_message_date_sent": null,
  "last_message_id": null,
  "last_message_user_id": null,
  "name": "Friday party",
  "occupants_ids": [29085, 29086, 29087],
  "photo": "party.jpg",
  "pinned_messages_ids": [],
  "type": 2,
  "updated_at": "2018-12-06T12:04:48Z",
  "user_id": 29085,
  "unread_messages_count": 0,
  "xmpp_room_jid": "105_5c091060e588ce59fdf873dc@muc.chatstage.connectycube.com"
}
```



## Add/Remove Users To Dialog (Update Dialog)
User can update group chat name, photo or add/remove occupants, based on their role and privileges.


### Add Users
```javascript
const dialogId = "5356c64ab35c12bd3b108a41";
const toUpdateParams = { push_all: { occupants_ids: [29088] } };

ConnectyCube.chat.dialog
  .update(dialogId, toUpdateParams)
  .then((dialog) => {})
  .catch((error) => {});
```

### Remove Users
**- Important note: Only group chat owner can remove other users from group chat.**

```javascript
const dialogId = "5356c64ab35c12bd3b108a41";
const toUpdateParams = { pull_all: { occupants_ids: [29088] } };

ConnectyCube.chat.dialog
  .update(dialogId, toUpdateParams)
  .then((dialog) => {})
  .catch((error) => {});
```

### Endpoint
PUT https://api.connectycube.com/chat/Dialog/{dialog_id}

### Request Example
```javascript
curl -X PUT \
-H "Content-Type: application/json" \
-H "CB-Token: <TOKEN>" \
-d '{"name":"Crossfit2","push_all":{"occupants_ids":[29088],"pinned_messages_ids":["5c123fdce588ce064043f53a"]},"photo":"gym2.jpeg"}' \
https://api.connectycube.com/chat/Dialog/5c123f75e588ce063e43f541
```

### Response
```javascript
{
  "_id": "5c123f75e588ce063e43f541",
  "admins_ids": [],
  "created_at": "2018-12-13T11:16:05Z",
  "description": "strong man",
  "last_message": "cool",
  "last_message_date_sent": 1544699868,
  "last_message_id": "5c123fdce588ce064043f53a",
  "last_message_user_id": 29085,
  "name": "Crossfit2",
  "occupants_ids": [29085, 29086, 29087, 29088],
  "photo": "gym2.jpeg",
  "pinned_messages_ids": ["5c123fdce588ce064043f53a"],
  "type": 2,
  "updated_at": "2018-12-13T11:21:21Z",
  "user_id": 29085,
  "unread_messages_count": 0,
  "xmpp_room_jid": "105_5c123f75e588ce063e43f541@muc.chatstage.connectycube.com"
}
```


  

## Remove Dialog 
Remove/Delete a dialog 

### Code
```javascript
// Remove single dialog
const dialogId = "5356c64ab35c12bd3b108a41";

// Remove multiple dialogs
const dialogIds = ['5356c64ab35c12bd3b108a41', ..., '5356c64ab35c12bd3b108a84']

ConnectyCube.chat.dialog.delete(dialogId).catch((error) => {});
```

### Endpoint
DELETE https://api.connectycube.com/chat/Dialog/{dialog_id}

### Request Example
```javascript
curl -X DELETE \
-H "CB-Token: <TOKEN>" \
https://api.connectycube.com/chat/Dialog/5c091060e588ce59fdf873dc
```

### Response
```javascript
{
  "_id": "5c123f75e588ce063e43f541",
  "admins_ids": [],
  "created_at": "2018-12-13T11:16:05Z",
  "description": "strong man",
  "last_message": "cool",
  "last_message_date_sent": 1544699868,
  "last_message_id": "5c123fdce588ce064043f53a",
  "last_message_user_id": 29085,
  "name": "Crossfit2",
  "occupants_ids": [29085, 29086, 29087, 29088],
  "photo": "gym2.jpeg",
  "pinned_messages_ids": ["5c123fdce588ce064043f53a"],
  "type": 2,
  "updated_at": "2018-12-13T11:21:21Z",
  "user_id": 29085,
  "unread_messages_count": 0,
  "xmpp_room_jid": "105_5c123f75e588ce063e43f541@muc.chatstage.connectycube.com"
}
```


## Roles and Priviliges
There are different roles of users in a chat dialog:

**Regular user** - user who can send and receive messages.

**Admin** - advanced user with moderation privileges.

**Super admin** - chat owner (creator) with all possible privileges.


 Roles  | Private chat	 | Group chat	  | Public chat	 | Broadcast
------------- | ------------- | ------------- | ------------- | ------------- 
Regular user  | - send/receive messages <br/> - delete own message (one side/both sides) <br/> - delete chat dialog for themselve  | - send/receive messages <br/> - delete own message (one side/both sides) <br/> - delete chat dialog for themselve <br/> - add more users <br /> - change name, photo, description  | - send/receive messages <br/> - delete own message (one side/both sides) <br/> - delete chat dialog for themselves (or unsubscribe)  | - receive messages <br/> - delete chat dialog for themselve
Admin  | -  | Content Cell  | Content Cell  | Content Cell 
Super admin  | -  | Content Cell  | Content Cell  | Content Cell 






