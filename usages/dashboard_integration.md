Bime dashboard integration
--------------------------

Third party solution providers can seamlessly embed bime dashboards as part of their applications.

The pieces required are:
* A Bime OEM account
* Make API calls to synchronize named users access rights
* Pass the Bime access token of the user to the embeded dashboards

simple workflow
---------------
1. Create at least one dashboard from the BimeUI (create connections => queries => dashboard)

2. try to get a Bime's named user for your system id of the current user.
3. if it exists goes to 6.
4. if it doesn't exist create a named user in Bime.
5. affect the user to an existing named user group. 
6. list the dashboards bime's named user group has access to.
7. load the dashboard passing in parameter the bime's named user access token.

Advanced workflow
-----------------
Named user group can have associated security rules that can be applied. 