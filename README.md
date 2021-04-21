<h1>&nbsp;</h1>
<h1>&nbsp;</h1>
<h1>RH SSO Integration with MS AD, GitHub</h1>
<p>Table of Contents</p>
<ul>
<li><a href="#_background">Background</a></li>
<li><a href="#_prerequisites">Prerequisites</a></li>
<li><a href="#_goals">RH SSO &amp; Microsoft AD Configuration</a></li>
<li><a href="#_steps">GitHub Configuration</a></li>
<li><a href="#_steps">RH SSO &amp; GitHub Configuration</a></li>
</ul>
<h2>Background</h2>
<p><strong>R</strong>ed <strong>H</strong>at <strong>S</strong>ingle <strong>S</strong>ign <strong>O</strong>n (RH SSO) is a single sign on solution for web apps and RESTful web services. The goal of RHSSO is to make security simple so that it is easy for application developers to secure the apps and services they have deployed in their organization. Security features that developers normally have to write for themselves are provided out of the box and are easily tailorable to the individual requirements of your organization. RH SSO provides customizable user interfaces for login, registration, administration, and account management. You can also use RHSSO as an integration platform to hook it into existing LDAP and Active Directory servers. You can also delegate authentication to third party identity providers like Facebook and Google+. In this article we will see ho we can integrate RH SSO with Microsoft AD and GitHub.</p>
<h2>Prerequisites</h2>
<ul>
<li>Red Hat Single Sign On Installed and Running</li>
<li>Access to Microsoft Active Directory</li>
<li>Access to GitHub Account</li>
</ul>
<h2>RH SSO &amp; Microsoft AD Configuration</h2>
<ol>
<ol>
<li>Login to RH SSO</li>
<li>Navigate to you Realm (dropdown on the the top left of the page)</li>
<li>In the left hand panel click <strong>User Fedration</strong></li>
<li><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/rhsso-user-fedration.png" alt="User Fedration" /></li>
<li>Provide the AD configuration details as shown in <a href="https://geekprank.com/chat-screenshot/" rel="nofollow">the screenshot</a> and click <strong>Save.</strong></li>
<li>&nbsp;</li>
<li>
<table style="width: 100%; height: 162px;" border="1" cellspacing="0" cellpadding="0">
<tbody>
<tr style="background-color: #90c78f; color: #000000;">
<td style="text-align: center; height: 18px; width: 28.9676%;"><strong>Field</strong></td>
<td style="text-align: center; height: 18px; width: 24.1911%;"><strong>Value</strong></td>
<td style="text-align: center; height: 18px; width: 46.5331%;"><strong>Notes</strong></td>
</tr>
<tr style="height: 18px;">
<td style="height: 18px; width: 28.9676%;">Vendor</td>
<td style="height: 18px; width: 24.1911%;">Active Directory</td>
<td style="height: 18px; width: 46.5331%;">Fixed</td>
</tr>
<tr style="height: 18px;">
<td style="height: 18px; width: 28.9676%;">Username LDAP attribute&nbsp;</td>
<td style="height: 18px; width: 24.1911%;">cn</td>
<td style="height: 18px; width: 46.5331%;">Pre-populated. Attribute that contains the user name. You can change it if you want to use a different attribute</td>
</tr>
<tr style="height: 18px;">
<td style="height: 18px; width: 28.9676%;">Connection URL</td>
<td style="height: 18px; width: 24.1911%;">User Provided&nbsp;</td>
<td style="height: 18px; width: 46.5331%;">Provide MS AD connection URL (ldap(s)://host:port</td>
</tr>
<tr style="height: 18px;">
<td style="height: 18px; width: 28.9676%;">Users DN</td>
<td style="height: 18px; width: 24.1911%;">User Provided</td>
<td style="height: 18px; width: 46.5331%;">DN of the LDAP tree where the users are located. Example: It would be CN=users,DC=example,DC=com</td>
</tr>
<tr>
<td style="width: 28.9676%;">Bind DN</td>
<td style="width: 24.1911%;">User Provided</td>
<td style="width: 46.5331%;">DN of the user for authenticating and get the user list from AD. Admin user or a service account. Example: CN=Administrator,CN=Users,DC=demo, DC=example,DC=com</td>
</tr>
<tr>
<td style="width: 28.9676%;">Bind Credential</td>
<td style="width: 24.1911%;">User Provided</td>
<td style="width: 46.5331%;">Password of the Bind DN user above</td>
</tr>
<tr>
<td style="width: 28.9676%;">Other Fields</td>
<td style="width: 24.1911%;">&nbsp;</td>
<td style="width: 46.5331%;">Change as appropriate</td>
</tr>
</tbody>
</table>
</li>
</ol>
</ol>
<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/ad-setup.png" alt="AD Setup" /></p>
<ol>
<ol>
<li>Once you the scree reloads scroll to the bottom and click <strong>Synchronize all users</strong> button. This will synchronize all the user from AD and you should see a message similar to the one below.</li>
</ol>
</ol>
<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/sync-users.png" alt="Sync All Users" /></p>
<ol>
<li>In the left hand pane click <strong>Users</strong> and click <strong>View all users </strong>on the screen that appears on the right pane this will list all the users that have been synchronized with RH SSO.</li>
<li>Log out and login back with a user synced with RH SSO and the user should be able to login as get an unauthorized error. This indicates that the user login is successfull but the user does not have the appropriate access rights.</li>
</ol>
<h2>GitHub Configuration</h2>
<h2>RH SSO &amp; GitHub Configuration</h2>
