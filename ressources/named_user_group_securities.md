name user group security
========================
This is where you associate named user groups and data security rules.

Get name user group security
---------------------------

* `GET /named_user_group_securities` will return all name user group securities.

```json
[
  {
    "id": 605816632,
    "named_user_group_id": 345,
    "data_security_rule_id":343,
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00"
  },
  {
    "id": 605826632,
    "named_user_group_id": 342,
    "data_security_rule_id":213,
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00"
  }
]
```


Get name user group security
---------------------------

* `GET /named_user_group_securities/1` will return the specified name user group security.

```json
{
  "id": 605816632,
  "named_user_group_id": 123,
  "data_security_rule_id": 345,
  "updated_at": "2012-03-23T13:55:43-05:00",
  "created_at": "2012-03-23T13:55:43-05:00"
}
```

Create name user group security
-----------------------------

* `POST /named_user_group_securities` will create a new name user group security from the parameters passed.

```json
{
  "named_user_group_id": 123,
  "data_security_rule_id": 435
}
```

This will return `201 Created`, with the current JSON representation of the name user group security if the creation was a success. See the **Get name user group security** endpoint for more info. 


Update name user group security
-----------------------------

* `PUT /named_user_group_securities/1` will update the name user group security from the parameters passed.

```json
{
  "id": 605816632,
  "named_user_group_id": 123,
  "data_security_rule_id": 435
}
```


Delete dashboard subscription
-----------------------------

* `DELETE /named_user_group_securities/1` will delete the name user group security specified and return `204 No Content` if that was successful.