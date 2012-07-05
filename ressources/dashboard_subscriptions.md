dashboard subscriptions
========================
This is where you can give access a named user group to a particular dashboard.

Get dashboard subscriptions
---------------------------

* `GET /dashboard_subscriptions` will return all dashboard subscriptions.

```json
[
  {
    "id": 605816632,
    "dashboard_id": 123,
    "named_user_group_id": 345,
    "updated_at": "2012-03-23T13:55:43-05:00",
	"created_at": "2012-03-23T13:55:43-05:00"
  },
  {
   	"id": 605816632,
    "dashboard_id": 143,
    "named_user_group_id": 345,
    "updated_at": "2012-03-23T13:55:43-05:00",
	"created_at": "2012-03-23T13:55:43-05:00"
  }
]
```


Get dashboard subscription
---------------------------

* `GET /dashboard_subscriptions/1` will return the specified dashboard subscription.

```json
{
  "id": 605816632,
  "dashboard_id": 123,
  "named_user_group_id": 345,
  "updated_at": "2012-03-23T13:55:43-05:00",
  "created_at": "2012-03-23T13:55:43-05:00"
}
```

Create dashboard subscription
-----------------------------

* `POST /dashboard_subscriptions` will create a new dashboard subscription from the parameters passed.

```json
{
  "dashboard_id": 123,
  "named_user_group_id": 435
}
```

This will return `201 Created`, with the current JSON representation of the dashboard subscription if the creation was a success. See the **Get dashboard subscription** endpoint for more info. 


Update dashboard subscription
-----------------------------

* `PUT /dashboard_subscriptions/1` will update the dashboard subscription from the parameters passed.

```json
{
  "dashboard_id": 123,
  "named_user_group_id": 435
}
```


Delete dashboard subscription
-----------------------------

* `DELETE /dashboard_subscriptions` will delete the dashboard subscription specified and return `204 No Content` if that was successful.