RH SSO Integration with MS AD, GitHub
Table of Contents

Background
Prerequisites
RH SSO & Microsoft AD Configuration
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

Once you the scree reloads scroll to the bottom and click Synchronize all users button. This will synchronize all the user from AD and you should see a message similar to the one below.

In the left hand pane click Users and click View all users on the screen that appears on the right pane this will list all the users that have been synchronized with RH SSO.
d
GitHub Configuration
RH SSO & GitHub Configuration
