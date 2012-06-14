Connections
===========

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
   "creator_full_name":"nicolas raspal",`
   "technical_type":"RDBMS",
   "schema":[
    {datafield:"product_name", display_name:"product name",is_measure:false},
    {datafield:"customer_state", display_name:"customer state",is_measure:false},
    {datafield:"trn_over", display_name:"turn over",is_measure:true}
  ],
  "data_security_groups":[
    {id:434343,datafield:"product_name",autorized_values: }
  ]
  "named_user_groups": [
    {
      "id": "605",
      "name": "finance",
    },
    {
      "id": "602",
      "name": "HR",
    }
  ]
}
```
