Connections
===========

(Read only)
A connection hold informations on the datasource used, the name and type of columns along what are the user groups and security rules that has to be applied.

Get connections
---------------

* `GET /connections.json` will return all connections.

```json
[
  {
    "id": 6056632,
    "name": "Oracle prod 1",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "creator_full_name":"nicolas raspal",
    "technical_type":"RDBMS"
  },
  {
    "id": 6056631,
    "name": "Oracle prod 2",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "creator_full_name":"nicolas raspal",
    "technical_type":"RDBMS"
  }
]
```


Get connection
--------------

* `GET /connection/1.json` will return the specified connection.

```json
{
   "id": 6056631,
   "name": "Oracle prod 2",
   "updated_at": "2012-03-23T13:55:43-05:00",
   "created_at": "2012-03-23T13:55:43-05:00",
   "creator_full_name":"nicolas raspal",
   "technical_type":"RDBMS",
   "schema":[
    {"datafield":"product_name", "display_name":"product name","is_measure":false},
    {"datafield":"customer_state", "display_name":"customer state","is_measure":false},
    {"datafield":"trn_over", "display_name":"turn over","is_measure":true}
   ],
   "data_security_rules":[
    {"id":434343,"datafield":"product_name","autorized_values":"'atari','xbox','ps3'" },
    {"id":434342,"datafield":"product_name","autorized_values":"'atari'" },
    {"id":434341,"datafield":"product_name","autorized_values":"'atari','ps3'" },
    {"id":434340,"datafield":"customer_state","autorized_values":"'herault'" }
   ],
   "named_user_groups": [
    {"id": "605","name": "finance south","data_security_rules":[{"id":434340},{"id":434341}]},
    {"id": "603","name": "hr","data_security_rules":[{"id":434340},{"id":434341}]},
    {"id": "601","name": "south","data_security_rules":[{"id":434340},{"id":434341}]}
   ]
}
```
