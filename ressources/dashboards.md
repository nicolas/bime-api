Dashboards
==========

Get dashboards
--------------

* `GET /dashboards.json` will return all named users.

```json
[
  {
    "id": 605816632,
    "name": "Activity dashboard",
    "publication_guid": "02B41A2B6A3E47AEAA6242DDC55C1D23",
    "updated_at": "2012-03-23T13:55:43-05:00",
    "created_at": "2012-03-23T13:55:43-05:00",
    "is_published":true
    
  },
  {
   "id": 605816634,
   "name": "HR dashboard",
   "publication_guid": "02B41A2B6A3E47AEAA6242DDC55C1D23",
   "updated_at": "2012-03-23T13:55:43-05:00",
   "created_at": "2012-03-23T13:55:43-05:00",
   "is_published":false
  }
]
```


Get dashboard
-------------

* `GET /dashboard/1.json` will return the specified dashboard.

```json
{
   "id": 605816632,
   "name": "Activity dashboard",
   "publication_guid": "02B41A2B6A3E47AEAA6242DDC55C1D23",
   "updated_at": "2012-03-23T13:55:43-05:00",
   "created_at": "2012-03-23T13:55:43-05:00",
   "is_published":true,
   "password_protected":false,
   "group_security":true,
   "connections": [
    {
      "id": 605816632,
      "name": "Oracle prod 2",
    },
    {
      "id": 605816632,
      "name": "Oracle prod 1",
    }
  ],
  "named_user_groups": [
    {
      "id": 605,
      "name": "finance",
    },
    {
      "id": 602,
      "name": "HR",
    }
  ]
}
```
