Data security rule
==================
A data security rule express a data restriction on a column for a named user group. In short, it allows to define that a named user group called "Region East" can only access the data where the column "regions" contains the "NORTH-EAST" and "SOUTH-EAST" values.
This rule would translate in SQL by appending automatically to all the queries "WHERE regions in ('NORTH-EAST','SOUTH-EAST')".

Get data security rules
-----------------------

* `GET /data_security_rules` will return all data security rules.

```json
[
  {
    "id":434343,
    "datafield":"product_name",
    "autorized_values":"'atari','xbox','ps3'",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "connection_id": "123334"
  },
  {
    "id":434343,
    "datafield":"product_name",
    "autorized_values":"'atari','xbox','ps3'",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "connection_id": "123334"
  }
]
```


Get data security rule
----------------------

* `GET /data_security_rules/1` will return the specified data security rule.

```json
{
    "id":434343,
    "datafield":"product_name",
    "autorized_values":"'atari','xbox','ps3'",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "connection":{"id": "123334","name":"Oracle prod 1"},
    "name_user_groups": [
    	{"id":112,"name":"South"},
    	{"id":111,"name":"HR South"}
    ]
}
```

Create data security rule
-------------------------

* `POST /data_security_rules` will create a new data security rule from the parameters passed.

```json
{
  "connection_id":123334,
  "datafield": "product_name",
  "autorized_values": "'atari','xbox','ps3'"
}
```

This will return `201 Created`, with the current JSON representation of the data security rule if the creation was a success. See the **Get data security rule** endpoint for more info. 


Update data security rule
-------------------------

* `PUT /data_security_rules/1` will update the data security rule from the parameters passed.

```json
{
  "connection_id":123334,
  "datafield": "product_name",
  "autorized_values": "'atari','xbox','ps3'"
}
```

This will return `200 OK` if the update was a success along with the current JSON representation of the data security rule. See the **Get data security rule** endpoint for more info.


Delete data security rule
-------------------------

* `DELETE /data_security_rule/1.json` will delete the data security rule specified and return `204 No Content` if that was successful.