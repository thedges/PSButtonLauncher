# PSButtonLauncher

This package contains a "Waze like" experience to allow users to launch actions. Current actions supports are:
* <b>Launch a URL</b> - open a defined URL (could be external URL or direct to community page)
* <b>Create New Record</b> - create a new Salesforce record (ex: Case) and default fields to defined set of values

This component requires that a configuration setting be defined first. Four custom objects were created to support the configuration. You should create the objects in this order:

1. <b>PSButtonLauncherSetting__c</b>

First create this object to define a configuration setting. This drives the first drop-down list in the Lightning Component configuration screen. Here is definition of fields:

   - <b>Name</b> - provide a name for the configuration setting (ex: "311 Services")

2. <b>PSButtonLauncherCategory__c</b>

Next create 1-to-many categories to group related functions/actions. For example in a 311 scenario, you could a category named "Animal Control" that could contain a variety of launcher actions defined in step 3.

   - <b>Name</b> - provide a name for the category (ex: "Animal Control")
   - <b>Icon URL</b> - provide a URL to an icon for this category. This can be a full "https://..." type URL or if you use static resources, use a value like "/resource/SampleIcon" where SampleIcon would be name of your static resource
   
3. <b>PSButtonLauncherItem__c</b>

Next create 1-to-many launcher items that will be related to your category defined above. For example the "Animal Control" scenario above, you could create some launcher items to send users to a defined URL for animal control info, or have a launcher item that will create a new case record and capture the current user, lat/lng, and GPS address location.

   - <b>Name</b> - provide a name for the launcher item (ex: "Animal Loose")
   - <b>Icon URL</b> - provide a URL to an icon for this item. This can be a full "https://..." type URL or if you use static resources, use a value like "/resource/SampleIcon" where SampleIcon would be name of your static resource
   - <b>Type</b> - the type of item. Current values are "URL" or "Create a Record"

   
   If type is "URL"...
   - <b>URL</b> - provide a URL to launch (could be external URL or direct to community page)
   
   If type is "Create a Record"...
   - <b>Object API Name</b> - the API name of the sObject to create a new record for
   - <b>Confirmation Msg</b> - the message to show user before creating new record to confirm action press
   - <b>Contact Field API Name</b> - the field API name of the sObject field to store the current community user reference
   - <b>Full Address Field API Name	</b> - the field API name to store the full address obtained from GPS reverse lookup
   - <b>Street Field API Name	</b> - the field API name to store the street obtained from GPS reverse lookup
   - <b>City Field API Name</b> - the field API name to store the city obtained from GPS reverse lookup
   - <b>State Field API Name</b> - the field API name to store the state obtained from GPS reverse lookup
   - <b>Zipcode Field API Name</b> - the field API name to store the zipcode obtained from GPS reverse lookup
   - <b>Latitude Field API Name</b> - the field API name to store the latitude value
   - <b>Longitude Field API Name</b> - the field API name to store the longitude value

   <b>Note:</b>LauncherItem records can be defined for a category as defined in the flow above BUT you can also define a LaunchItem record as a child directly from the setting record as defined in step #1. This give you option to have category and launcher items at the setting level.

4. <b>PSButtonLauncherKeyValue__c</b>

Next if you chose type of "Create a Record" in the previous step, you can define 1-to-many default field values to store in the new object record. You 

   - <b>Key</b> - the field API name for the sObject defined in step #3 that you want to provide a value (ex: "Status" or "Sub-type__c")
   - <b>Value</b> - the value to store for that field


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
