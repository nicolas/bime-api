Named users
===========

Get named users
---------------

* `GET /named_users.json` will return all named users.

```json
[
  {
    "id": 605816632,
    "full_name": "Nicolas Raspal",
    "external_id": "60581D",
    "updated_at": "2012-03-23T13:55:43-05:00",
	"created_at": "2012-03-23T13:55:43-05:00",
    "access_token": "AZALPODP12332MLSDSDSLM",
	"named_user_group_id":5
  },
  {
   "id": 605816634,
   "full_name": "Yannick Chaze",
   "external_id": "60581D",
   "updated_at": "2012-03-23T13:55:43-05:00",
   "created_at": "2012-03-23T13:55:43-05:00",
   "access_token": "AZAL2P1DP12332MLSDSDSLM",
   "named_user_group_id":4
  }
]
```


Get named user
--------------

* `GET /named_users/1.json` will return the specified named user.

```json
{
   "id": 605816634,
   "full_name": "Yannick Chaze",
   "external_id": "60581D",
   "updated_at": "2012-03-23T13:55:43-05:00",
   "created_at": "2012-03-23T13:55:43-05:00",
   "access_token": "AZALPODP112332MLSDSDSLM",
   "named_user_group_id":5
}
```
access_token is sent to dashboards to identify the users and eventually apply data security.

Create named user
-----------------

* `POST /named_user.json` will create a new named user from the parameters passed.

```json
{
  "full_name": "Mathias Paulin",
  "external_id": "007"
}
```

This will return `201 Created`, with the current JSON representation of the project if the creation was a success. See the **Get named user** endpoint for more info. 


Update named user
-----------------

* `PUT /named_user/1.json` will update the project from the parameters passed.

```json
{
  "full_name": "Dr Mathias Paulin",
  "external_id": "007",
  "renew_access_token":true
}
```
The renew_access_token parameter when set at **true** will expire the current one and create a new one.

This will return `200 OK` if the update was a success along with the current JSON representation of the named user. See the **Get named user** endpoint for more info.


Delete named user
-----------------

* `DELETE /named_user/1.json` will delete the named user specified and return `204 No Content` if that was successful.