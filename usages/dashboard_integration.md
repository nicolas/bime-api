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
2. For all the users in your app create a named viewers through the [named_viewers API] (https://https://github.com/nicolas/bime-api/blob/master/ressources/named_users.md)
3. Organize those users into named user groups
4. Give to name user group 

