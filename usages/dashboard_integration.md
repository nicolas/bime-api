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
1. Create at least one dashboard from the BimeUI (create connections => queries => dashboard)

### set up
2. For all the users in your app create a named viewers through the [named_viewers API] (https://https://github.com/nicolas/bime-api/blob/master/ressources/named_users.md)
3. Organize those users into named user groups through the [named_user_group API] (https://github.com/nicolas/bime-api/blob/master/ressources/named_user_groups.md)
4. Give dashboard access to your named user through the [dashboard_suscription API] (https://github.com/nicolas/bime-api/blob/master/ressources/dashboard_subscriptions.md)
5. (Optional) create data security rule through the [data_security_rule API] (https://github.com/nicolas/bime-api/blob/master/ressources/data_security_rules.md)
6. (Optional) associate your data security rule with a named user group through the [name_user_group_security API] (https://github.com/nicolas/bime-api/blob/master/ressources/named_user_group_security.md)


### recurring task
* Create named viewers automatically when a new user is created in your system
* Manage others ressource accordingly to your user requierements (for example create new named user group for each of your customer with the right data security rule)