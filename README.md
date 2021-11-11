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


## Create a session
For using the ConnectyCube API, user needs a session token, which provides a secure access to ConnectyCube API. <br />
To create an application session use the following code::

### Endpoint
```javascript
POST https://api.connectycube.com/session
```

### Create Application Session
```javascript
ConnectyCube.createSession()
  .then((session) => {})
  .catch((error) => {});
```

### Request Example
```javascript
curl -X POST \
-H "Content-Type: application/json" \
-d '{"application_id": "1", "auth_key": "29WfrNWdvkhmX6V", "nonce": "4214611091", "timestamp": "1544010993",  "signature": "46fd163f78f52a0f8122d3758d6282923471d55f"}' \
https://api.connectycube.com/session
```

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/session"

headers = CaseInsensitiveDict()
headers["Content-Type"] = "application/json"

data = '{"application_id": "1", "auth_key": "29WfrNWdvkhmX6V", "nonce": "4214611091", "timestamp": "1544010993",  "signature": "46fd163f78f52a0f8122d3758d6282923471d55f"}'


resp = requests.post(url, headers=headers, data=data)

print(resp.status_code)
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

### Request Example
```javascript
curl -X POST \
-H "Content-Type: application/json" \
-d '{"application_id": "1", "auth_key": "29WfrNWdvkhmX6V", "nonce": "111", "timestamp": "1544010993",  "signature": "46fd163f78f52a0f8122d3758d6282923471d55f", "user":{"login": "john", "password": "11111111"}}' \
https://api.connectycube.com/session
```

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/session"

headers = CaseInsensitiveDict()
headers["Content-Type"] = "application/json"

data = '{"application_id": "1", "auth_key": "29WfrNWdvkhmX6V", "nonce": "111", "timestamp": "1544010993",  "signature": "46fd163f78f52a0f8122d3758d6282923471d55f", "user":{"login": "john", "password": "11111111"}}'

resp = requests.post(url, headers=headers, data=data)

print(resp.status_code)
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

### Endpoint
POST https://api.connectycube.com/users

### Request Example
```javascript
curl -X POST \
-H "Content-Type: application/json" \
-H "CB-Token: <TOKEN>" \
-d '{"user": {"login": "Dacia", "password": "petU4or!", "email": "dacia_k@domain.com", "facebook_id": "91234409", "twitter_id": "83510562734", "full_name": "Dacia Kail ", "phone": "+6110797757"}}' \
https://api.connectycube.com/users
```

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/users"

headers = CaseInsensitiveDict()
headers["Content-Type"] = "application/json"
headers["CB-Token"] = "<TOKEN>"

data = '{"user": {"login": "Dacia", "password": "petU4or!", "email": "dacia_k@domain.com", "facebook_id": "91234409", "twitter_id": "83510562734", "full_name": "Dacia Kail ", "phone": "+6110797757"}}'

resp = requests.post(url, headers=headers, data=data)

print(resp.status_code)
```

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

## User Sign In (Login Authentication)
If you have an application session, you can upgrade it to a user session by calling login method. <br />
This login method will create a user session and make the user logged in.
If the user is not registered to connecty cube, it will be added to user list.
There are four available sets of data to specify when authenticate a user:
- login and password
- email and password
- provider + keys[token] and keys[secret] - when sign up with Facebook or Twitter
- provider + firebase_phone[project_id] and firebase_phone[access_token] - when sign up with a phone number

** - Important note - login and password is required!

### Code
```javascript
const userCredentials = { login: "cubeuser", password: "awesomepwd" };
// const userCredentials = { email: 'cubeuser@gmail.com', password: 'awesomepwd' };
// const userCredentials = { provider: 'facebook', keys: {token: 'a876as7db...asg34dasd8wqe'} };

ConnectyCube.login(userCredentials)
  .then((user) => {})
  .catch((error) => {});
```

### Endpoint
POST https://api.connectycube.com/login

### Request Example
```javascript
curl -X POST \
-H "Content-Type: application/json" \
-H "CB-Token:  <TOKEN>" \
-d '{"login": "johnsmith", "password": "7665727zxc"}' \
https://api.connectycube.com/login
```

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/login"

headers = CaseInsensitiveDict()
headers["Content-Type"] = "application/json"
headers["CB-Token"] = "<TOKEN>"

data = '{"login": "johnsmith", "password": "7665727zxc"}'

resp = requests.post(url, headers=headers, data=data)

print(resp.status_code)
```

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



## Delete User
A user can delete himself from the platform:


### Code
```javascript
ConnectyCube.users
  .delete()
  .then((result) => {})
  .catch((error) => {});
```

### Endpoint
DELETE https://api.connectycube.com/users/{user_id}


### Request Example
```javascript
curl -X DELETE \
-H "CB-Token: <TOKEN>" \
https://api.connectycube.com/users/51959
```

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/users/51959"

headers = CaseInsensitiveDict()
headers["CB-Token"] = "<TOKEN>"

resp = requests.delete(url, headers=headers)

print(resp.status_code)
```

### Response
```javascript
Status: 200
```


## Authentication via external identity provider



### Code
```javascript

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

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/chat/Dialog"

headers = CaseInsensitiveDict()
headers["Content-Type"] = "application/json"
headers["CB-Token"] = "<TOKEN>"

data = '{"type":2,"name":"Friday party","occupants_ids":"29085,29086,29087","description":"lets dance the night away","photo":"party.jpg"}'

resp = requests.post(url, headers=headers, data=data)

print(resp.status_code)
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

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/chat/Dialog/5c123f75e588ce063e43f541"

headers = CaseInsensitiveDict()
headers["Content-Type"] = "application/json"
headers["CB-Token"] = "<TOKEN>"

data = '{"name":"Crossfit2","push_all":{"occupants_ids":[29088],"pinned_messages_ids":["5c123fdce588ce064043f53a"]},"photo":"gym2.jpeg"}'

resp = requests.put(url, headers=headers, data=data)

print(resp.status_code)
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

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/chat/Dialog/5c091060e588ce59fdf873dc"

headers = CaseInsensitiveDict()
headers["CB-Token"] = "<TOKEN>"

resp = requests.delete(url, headers=headers)

print(resp.status_code)
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



## Get Dialogs
You need to pass type: 2 and ids of opponents you want to create a chat with:

### Code
```javascript
const filters = {};

ConnectyCube.chat.dialog
  .list(filters)
  .then((result) => {})
  .catch((error) => {});
```

### Endpoint
GET https://api.connectycube.com/chat/Dialog

### Request Example
```javascript
curl -X GET \
-H "CB-Token: <TOKEN>" \
https://api.connectycube.com/chat/Dialog
```

### Python
```python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.connectycube.com/chat/Dialog"

headers = CaseInsensitiveDict()
headers["CB-Token"] = "<TOKEN>"

resp = requests.get(url, headers=headers)

print(resp.status_code)
```


### Response
```javascript
{
    "total_entries": 4,
    "skip": 0,
    "limit": 1000,
    "items": [
        {
            "_id": "5c094c0ce588ce6856f87422",
            "admins_ids": [29085],
            "created_at": "2018-12-06T16:19:24Z",
            "description": "Cute chat",
            "last_message": "nope?",
            "last_message_date_sent": 1544452627,
            "last_message_id": "5c0e7a13e588ce6b6f3ebf80",
            "last_message_user_id": 29086,
            "name": "hello kitty",
            "occupants_ids": [
                29085,
                29086,
                29087
            ],
            "photo": null,
            "pinned_messages_ids": ["5c0e7a13e588ce6b6f3ebf80"],
            "type": 2,
            "updated_at": "2018-12-10T14:37:07Z",
            "user_id": 29085,
            "unread_messages_count": 1,
            "xmpp_room_jid": "105_5c094c0ce588ce6856f87422@muc.chatstage.connectycube.com"
        },
        ...
    ]
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
Admin  | -  | - delete any messages for everyone <br/> - pin messages <br/> - add/remove users <br/> - regular user privileges  | - change name, description, photo <br/> - delete any messages for everyone <br/> - pin messages <br/> -block/unblock users <br/> - regular user privileges | - change name, description, photo <br/> - delete any messages for everyone <br/> - pin messages <br/> -block/unblock users 
Super admin  | -  |  - add/remove admins <br/> - delete dialog for everyone <br/> - regular admin privileges  | - add/remove admins <br/> - delete dialog for everyone <br/> - regular admin privileges  | - add/remove admins <br/> - delete dialog for everyone 






