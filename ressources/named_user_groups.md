named user groups
=================

Get named user groups
---------------------

* `GET /named_user_groups.json` will return all named user groups.

```json
[
  {
    "id": 605816632,
    "full_name": "Nicolas Raspal",
    "external_id": "60581D",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "access_token": "AZALPODP12332MLSDSDSLM",
    "named_user_group_group_id":5
  },
  {
    "id": 605816634,
    "full_name": "Yannick Chaze",
    "external_id": "60581D",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "access_token": "AZAL2P1DP12332MLSDSDSLM",
    "named_user_group_group_id":4
  }
]
```


Get named user group
--------------------

* `GET /named_user_groups/1.json` will return the specified named user group.

```json
{
   "id": 605816634,
   "full_name": "Yannick Chaze",
   "external_id": "60581D",
   "updated_at": "2012-03-23T13:55:43-05:00",
   "created_at": "2012-03-23T13:55:43-05:00",
   "access_token": "AZALPODP112332MLSDSDSLM",
   "named_user_group_group_id":5
}
```


Create named user group
-----------------------

* `POST /named_user_group.json` will create a new named user group from the parameters passed.

```json
{
  "full_name": "Mathias Paulin",
  "external_id": "007"
}
```

This will return `201 Created`, with the current JSON representation of the named user group if the creation was a success. See the **Get named user group** endpoint for more info. 


Update named user group
-----------------------

* `PUT /named_user_group/1.json` will update the named user group from the parameters passed.

```json
{
  "full_name": "Dr Mathias Paulin",
  "external_id": "007",
  "renew_access_token":true
}
```
The renew_access_token parameter when set at **true** will expire the current one and create a new one.

This will return `200 OK` if the update was a success along with the current JSON representation of the named user group. See the **Get named user group** endpoint for more info.


Delete named user group
-----------------------

* `DELETE /named_user_group/1.json` will delete the named user group specified and return `204 No Content` if that was successful.