# PSButtonLauncher

This package contains a "Waze like" experience to allow users to launch actions. Current actions supports are:
* <b>Launch a URL</b> - open a defined URL (could be external URL to direct to community page)
* <b>Create New Record</b> - create a new Salesforce record (ex: Case) and default fields to defined set of values

This component requires that a configuration setting be defined first. Four custom objects were created to support the configuration. You should create the objects in this order:

1. <b>PSButtonLauncherSetting__c</b>

2. <b>PSButtonLauncherCategory__c</b>

3. <b>PSButtonLauncherItem__c</b>

4. <b>PSButtonLauncherKeyValue__c</b>


<b>Dependency:</b> Install the [PSCommon](https://github.com/thedges/PSCommon) package first

![alt text](https://github.com/thedges/PSButtonLauncher/blob/master/PSButtonLauncher.gif "Sample Image")

* The component configuration fields are:
  - <b>Launcher Setting</b> - the PSButtonLauncher setting name as defined in the PSButtonLauncherSetting object
  - <b>Background Color</b> - the background color of main container (ex: #E8E8E8)
  - <b>Back Icon</b> - the URL to the back icon used to navigate in the button screen (default: /resource/PSButtonLauncherBackIcon)
  - <b>Confirm Create Record</b> - show confirmation screen for creating new records
  - <b>Navigate to Record</b> - load detail screen after creating new record
  - <b>GPS Icon</b> - the icon to show in top-right that lat/lng has been acquired (default: /resource/PSButtonLauncherGPSIcon)
  - <b>Show GPS Icon</b> - boolean to show the GPS icon in top-right
  
<a href="https://githubsfdeploy.herokuapp.com">
  <img alt="Deploy to Salesforce"
       src="https://raw.githubusercontent.com/afawcett/githubsfdeploy/master/deploy.png">
</a>
