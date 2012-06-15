bime dashboard integration
--------------------------

Third party solution providers can seamlessly embed bime dashboards as part of their applications.

The pieces required are:
* BimeDB to host analytic data
* A Bime OEM account
* Make API calls to synchronize named users access rights
* Pass the Bime access token of the user to the embeded dashboards

common workflow
---------------
1. Create a dashboard from the BimeUI (create connections => queries => dashboard)

---- set up on time only -----
2. For all the users in your app create a named viewers through the [named_viewers API] (https://https://github.com/nicolas/bime-api/blob/master/ressources/named_users.md)
3. Organize those users into named user groups through the [named_user_group API] (https://github.com/nicolas/bime-api/blob/master/ressources/named_user_groups.md)
4. Give dashboard access to your named user through the [named_user_group/dashboard API] (https://github.com/nicolas/bime-api/blob/master/ressources/dashboard_subscriptions.md)
5. Give dashboard access to your named user through the [named_user_group/dashboard API] (https://github.com/nicolas/bime-api/blob/master/ressources/dashboard_subscriptions.md)

---- recurring task -----
6. Create named viewers automatically when a new user is created in your system
7. Delete named viewers automatically when user is deleted in your system