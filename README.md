



RH SSO Integration with MS AD, GitHub

Table of Contents

Background
Prerequisites
RH SSO & Microsoft AD Configuration
RH SSO & GitHub Integration
GitHub Configuration
RH SSO & GitHub Configuration
Background

Red Hat Single Sign On (RH SSO) is a single sign on solution for web apps and RESTful web services. The goal of RHSSO is to make security simple so that it is easy for application developers to secure the apps and services they have deployed in their organization. Security features that developers normally have to write for themselves are provided out of the box and are easily tailorable to the individual requirements of your organization. RH SSO provides customizable user interfaces for login, registration, administration, and account management. You can also use RHSSO as an integration platform to hook it into existing LDAP and Active Directory servers. You can also delegate authentication to third party identity providers like Facebook and Google+. In this article we will see ho we can integrate RH SSO with Microsoft AD and GitHub.

Prerequisites
Red Hat Single Sign On Installed and Running
Access to Microsoft Active Directory
Access to GitHub Account
RH SSO & Microsoft AD Configuration
Login to RH SSO
Navigate to you Realm (dropdown on the the top left of the page)
In the left hand panel click User Fedration
Provide the AD configuration details as shown in the screenshot and click Save.


Field	Value	Notes
Vendor	Active Directory	Fixed
Username LDAP attribute 	cn	Pre-populated. Attribute that contains the user name. You can change it if you want to use a different attribute
Connection URL	User Provided 	Provide MS AD connection URL (ldap(s)://host:port
Users DN	User Provided	DN of the LDAP tree where the users are located. Example: It would be CN=users,DC=example,DC=com
Bind DN	User Provided	DN of the user for authenticating and get the user list from AD. Admin user or a service account. Example: CN=Administrator,CN=Users,DC=demo, DC=example,DC=com
Bind Credential	User Provided	Password of the Bind DN user above
Other Fields	
	Change as appropriate

Once you the scree reloads scroll to the bottom and click Synchronize all users button. This will synchronize all the user from AD and you should see a message similar to the one below.

In the left hand pane click Users and click View all users on the screen that appears on the right pane this will list all the users that have been synchronized with RH SSO.
Log out and login back with a user synced with RH SSO and the user should be able to login as get an unauthorized error. This indicates that the user login is successfull but the user does not have the appropriate access rights.
RH SSO & GitHub Integration
GitHub Configuration
Under developer settings:(https://github.com/settings/developers).
Click on New Oauth App: (name anything as per your use-case). You will see a client id and client secret generated for your application.
Keep a note of the client secret.
Provide the Authorization callback URL from RH SSO (instructions in RH SSO & GitHub configuration below) and click register application. 
Field	Value
Application name	Appropriate Name
Homepage URL	Application Homepage URL
Authorization callback URL	Authorization callback URL from RH SSO (instructions below)
RH SSO & GitHub Configuration
Login to RH SSO
On the left hand panel select the Identity Provider & select Github as the provider. Copy the client id and client secret generated above from GitHub and past it here.
Copy the Redirect URL from here and use it in GitHub as mentioned in step 4 above Authorization callback URL.
