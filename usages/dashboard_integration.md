Bime dashboard integration
--------------------------

Third party solution providers can seamlessly embed bime dashboards as part of their applications.

The pieces required are:
* A Bime OEM account
* Make API calls to synchronize named users access rights
* Pass the Bime access token of the user to the embeded dashboards

Simple Workflow
---------------
1. Create at least one dashboard from the BimeUI (create connections => queries => dashboard)
2. try to get a Bime's named user for your system id of the current user.
3. if it exists go to 6.
4. Retrieve the list of groups
5. Create a named user in Bime and attach it to a group.
6. list the dashboards bime's named user group has access to.
7. load the dashboard passing in parameter the bime's named user access token.

Advanced Workflow
-----------------
Named user group can have associated security rules that can be applied. 

1. Create at least one dashboard from the BimeUI (create connections => queries => dashboard)
2. Create groups for your users
3. Create security rules for your group for your dashboard
4. Associate existing or new users to your group (See simple workflow)
5. Load the dashboard passing in parameter an access token for each user

Warning: please be sure to add the domain from where the dashboard will be loaded in the publish form of the dashboard in the BIME studio interface. 
