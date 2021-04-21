<h1>RH SSO Integration with MS AD, GitHub</h1>
<p>Table of Contents</p>
<ul>
<li><a href="#_background">Background</a></li>
<li><a href="#_prerequisites">Prerequisites</a></li>
<li><a href="#_rhssoad">RH SSO &amp; Microsoft AD Configuration</a></li>
<li><a href="#_rhssogithubint">RH SSO &amp; GitHub Integration</a>
<ul>
<li><a href="#_githubconf">GitHub Configuration</a></li>
<li><a href="#_rhssogithub">RH SSO &amp; GitHub Configuration</a></li>
</ul>
</li>
</ul>
<h2 id="_background">Background</h2>
<p><strong>R</strong>ed <strong>H</strong>at <strong>S</strong>ingle <strong>S</strong>ign <strong>O</strong>n (RH SSO) is a single sign on solution for web apps and RESTful web services. The goal of RHSSO is to make security simple so that it is easy for application developers to secure the apps and services they have deployed in their organization. Security features that developers normally have to write for themselves are provided out of the box and are easily tailorable to the individual requirements of your organization. RH SSO provides customizable user interfaces for login, registration, administration, and account management. You can also use RHSSO as an integration platform to hook it into existing LDAP and Active Directory servers. You can also delegate authentication to third party identity providers like Facebook and Google+. In this article we will see ho we can integrate RH SSO with Microsoft AD and GitHub.</p>
<h2 id="_prerequisites">Prerequisites</h2>
<ul>
<li>Red Hat Single Sign On Installed and Running</li>
<li>Access to Microsoft Active Directory</li>
<li>Access to GitHub Account</li>
</ul>
<h2 id="_rhssoad">RH SSO &amp; Microsoft AD Configuration</h2>
<ul>
<li>Login to RH SSO</li>
<li>Navigate to you Realm (dropdown on the the top left of the page)</li>
<li>In the navigation panel click <strong>User Fedration</strong></li><br>
<p>
  <img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/rhsso-user-fedration.png" alt="User Fedration" />
  </p><br>
<li>Provide the AD configuration details as shown in the screenshot and click <strong>Save.</strong></li>

<table style="width: 100%; height: 216px;" border="1" cellspacing="0" cellpadding="0">
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
<tr style="height: 90px;">
<td style="width: 28.9676%; height: 90px;">Bind DN</td>
<td style="width: 24.1911%; height: 90px;">User Provided</td>
<td style="width: 46.5331%; height: 90px;">DN of the user for authenticating and get the user list from AD. Admin user or a service account. Example: CN=Administrator,CN=Users,DC=demo, DC=example,DC=com</td>
</tr>
<tr style="height: 18px;">
<td style="width: 28.9676%; height: 18px;">Bind Credential</td>
<td style="width: 24.1911%; height: 18px;">User Provided</td>
<td style="width: 46.5331%; height: 18px;">Password of the Bind DN user above</td>
</tr>
<tr style="height: 18px;">
<td style="width: 28.9676%; height: 18px;">Other Fields</td>
<td style="width: 24.1911%; height: 18px;">&nbsp;</td>
<td style="width: 46.5331%; height: 18px;">Change as appropriate</td>
</tr>
</tbody>
</table>
</ul>
<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/ad-setup.png" alt="AD Setup" /></p>
<ul>
<li>Once the screen reloads scroll to the bottom and click <strong>Synchronize all users</strong> button. This will synchronize all the user from AD and you should see a message similar to the one below.</li>
</ul>
<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/sync-all.png" alt="Sync All Users" /></p>
<ul>
<li>In the navigation pane click <strong>Users</strong> and click <strong>View all users </strong>on the screen that appears on the right pane this will list all the users that have been synchronized with RH SSO.</li>
<li>Log out and login back with a user synced with RH SSO and the user should be able to login as get an unauthorized error. This indicates that the user login is successfull but the user does not have the appropriate access rights.</li>
</ul>
<h2 id="_rhssogithubint">RH SSO &amp; GitHub Integration</h2>
<h3 id="_githubconf">GitHub Configuration</h3>

<ul>
<li>Under developer settings:(<a class="ex ks" href="https://github.com/settings/developers" rel="noopener nofollow">https://github.com/settings/developers</a>)</li>
</ul>

<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/dev-settings.png" alt="Git Hub Dev Settings" /></p>
<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/github-app.png" alt="GitHub App" /></p>
<ul>
<li>Click on&nbsp;<strong class="gk kt">New Oauth App:</strong> (name anything as per your use-case). You will see a client id and client secret generated for your application.</li>
<li>Keep a note of the client secret.</li>
<li>Provide the Authorization callback URL from RH SSO (instructions in RH SSO &amp; GitHub configuration below) and click register application.&nbsp;</li>

<table style="border-collapse: collapse; width: 100%;" border="1">
<tbody>
<tr style="background-color: #90c78f; color: #000000;">
<td style="width: 50%; text-align: center;"><strong>Field</strong></td>
<td style="width: 50%; text-align: center;"><strong>Value</strong></td>
</tr>
<tr>
<td style="width: 50%;">Application name</td>
<td style="width: 50%;">Appropriate Name</td>
</tr>
<tr>
<td style="width: 50%;">Homepage URL</td>
<td style="width: 50%;">Application Homepage URL</td>
</tr>
<tr>
<td style="width: 50%;"><label for="oauth_application_callback_url">Authorization callback URL</label></td>
<td style="width: 50%;"><label for="oauth_application_callback_url">Authorization callback URL from RH SSO (instructions below)</label></td>
</tr>
</tbody>
</table>

</ul>
<h3 id="_rhssogithub">RH SSO &amp; Configuration</h3>

<ul>
<li>Login to RH SSO</li>
<li>On the navigation panel select the Identity Provider &amp; select Github as the provider. Copy the client id and client secret generated above from GitHub and past it here.</li>
</ul>

<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/idp.png" alt="IDP" /></p>
<ul>
<li>Copy the Redirect URL from here and use it in GitHub as mentioned in step 4 above Authorization callback URL</li>
<li>Logout of RH SSO. It will take you back to the RH SSO Login Screen. Here you should see an additional option <strong>GitHub</strong> for login.</li>
</ul>
<p><img src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/login-rhsso.png" alt="GitHub Login" /></p>
