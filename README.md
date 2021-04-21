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
	<li>Login to RH SSO</li>
	<li>Navigate to you Realm (dropdown on the the top left of the page)</li>
	<li>In the left hand panel click <strong>User Fedration</strong></li>
	<img alt="User Fedration" src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/rhsso-user-fedration.png" />
	<li>Provide the AD configuration details as shown in the screenshot</li>
	<img alt="User Fedration" src="https://github.com/rohitralhan/RHSSOIntegADGitLDAP/blob/main/images/ad-setup.png" />
</ol>

<h2>GitHub Configuration</h2>

<h2>RH SSO &amp; GitHub Configuration</h2>
