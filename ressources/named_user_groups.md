named user groups
=================

Get named user groups
---------------------

* `GET /named_user_groups` will return all named user groups.

```json
[
  {
    "id": 605816632,
    "name": "HR",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00"
  },
  {
    "id": 605816630,
    "name": "finance south",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00"
  }
]
```


Get named user group
--------------------

* `GET /named_user_groups/1` will return the specified named user group.

```json
{
    "id": 605816630,
    "name": "finance south",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "data_security_rules": [
      {"id":124},
      {"id":123}
    ],
    "dashboards":[
     {"id":124,"name":"Profits"},
     {"id":122,"name":"Activity"}
    ]
}
```

data_security_rules attribute is the data security rules that are linked to this named user group
dashboards are the dashboard the group can access

Create named user group
-----------------------

* `POST /named_user_groups` will create a new named user group from the parameters passed.

```json
{
  "name": "finance south"
}
```

This will return `201 Created`, with the current JSON representation of the named user group if the creation was a success. See the **Get named user group** endpoint for more info. 


Update named user group
-----------------------

* `PUT /named_user_groups/1` will update the named user group from the parameters passed.

```json
{
  "name": "finance south"
}
```
The renew_access_token parameter when set at **true** will expire the current one and create a new one.

This will return `200 OK` if the update was a success along with the current JSON representation of the named user group. See the **Get named user group** endpoint for more info.


Delete named user group
-----------------------

* `DELETE /named_user_groups/1` will delete the named user group specified and return `204 No Content` if that was successful.