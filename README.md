# UNIVERSAL PICKLISTS IMPLEMENTATION GUIDE

This readme will help you through the implementation of the Universal Picklists app for your Salesforce.com Org.  Thank you for considering our app in your organization. It is a work in progress, so please do take notes and let us know if you run into any issues with the text or if you believe there is a better way to accomplish the tasks we describe.

Before you deploy this solution to your production Org, it is strongly recommended that you test it in a sandbox first. This app is very, very powerful.  It has the power to overwrite multiple fields, including field dependencies, with the click of a single button.  If you are not careful, you could end up with a bunch of cleanup work. Please always test any admin app of this type first, but in particular one that attempts to accomplish tasks which are usually not possible.

Test. Test.  Test.

## Installation

First, install the app from the [AppExchange Listing](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N30000000pvmXEAQ).  We recommend starting in a Sandbox and installing in Production after you have tested it thoroughly.  We recommend installing for Administrators only.

After successfull installation, the initial configuration steps in the configuration are completed by clicking the “Configure” button on the Universal Picklists package after it has been installed from the AppExchange.com app store. 

> Setup → App Setup → Installed Packages → Configure

## Setting Up Your Org’s “Remote Site”

The first thing you will see when you go to configure your Universal Picklist app, is a warning telling you that you need to set up a “remote site” before you can use the app.  “Remote site” is the term used for the URL to access your Org’s metadata.

**Please note that To A Finish (the makers of this amazing app) cannot access your Org as this term might imply to some.  This step is necessary so that you can access your own metadata (data about your data, including picklist options) through our app.**

Read more about the Remote Site settings from the Salesforce.com Developer documentation [here](https://www.salesforce.com/us/developer/docs/apexcode/index_Left.htm#CSHID=apex_callouts_remote_site_settings.htm|StartTopic=Content%2Fapex_callouts_remote_site_settings.htm|SkinName=webhelp).

If you see an error talking about remote sites, please follow these steps:

1. Copy the endpoint indicated in the error, starting with the “https://” and all the way through the end. (it IS case sensitive)
2. Now, go to: Setup → Security Controls → Remote Site Setup.
3. Click on the New Remote Site button.
4. In the Remote Site Edit dialog, enter any name for the Remote Site Name, and then paste the URL you copied in step #1 into the Remote Site URL field.
> **Note: If you have set up a Custom Domain/My Domain, you will want to add this in here as a Remote Site as well.**
5. Make sure the Active checkbox is enabled, and press the Save button.
6. If you are using the paid version, and plan to manage picklists in your sandbox(es) from this Org, then please also add a Remote Site entry for: https://test.salesforce.com/
7. Now go back to configure Universal Picklists.  Go to: Setup → App Setup → Installed Packages and click on the Configure link next to the Universal Picklists app.

You should see the Universal Picklist Manager setup page, alerting you that you have not yet set up any picklists.  

## Adding a Universal Picklist to Manage

Picklist values for the same or similar picklists in different objects (and different Orgs in the paid version) can be managed from one single location.  If you have reached the setup page in the previous section, you can now follow these simple steps to set up a universal picklist.

1. Click the Add Picklist button.
2. From the Edit page, enter the Title of the picklist.  To manage multiple picklists as one Universal Picklist, give both of the records the same title.
> **This title is critically important, as it determines the uniqueness of the picklist.  In other words, if you add multiple picklists with this same title, the system will treat them all as the same universal picklist.**
3. Select the desired Object.
4. Select the desired Picklist to manage.  This is the picklist that will be updated when you sync.
5. Optional.  Select a “Parent” picklist.  This is for situations where the Picklist you are managing has a controlling parent picklist (the Picklist field would be the dependent picklist).  You want to be able to make sure you can indicate which parent value fits the picklist value.
6. Optional.  Select a “Grand Parent” picklist.  This is for situations where the Picklist you are managing has a controlling picklist as a parent, that in turn has a controlling picklist, controlling it!  (Any more than that, and you’re on your own!)
7. If you have record types in this object, optionally click the “Add to All Record Types?” checkbox.  This will add the value to the record types that exist for this object.  Note: Only 10 Record Types per Object are supported.
8. Click the “Make Master” checkbox to make this picklist the default one, which will be used when synchronizing the Universal Picklist you named.
9. Click the Save button, which will return you to the list of Universal Picklists. Add as many records as you want (a maximum of five unique titles in the Standard version).
10. After adding the desired number of picklists, you will see a list of unique Titles, and potentially multiple Objects where the same Universal Picklist is being used.  Click on the Title of the picklist you want to manage (not the “Edit” link).
11.	You can now do several things:
    - Click the Add New button in order to add another option to the list.
    - Edit one of the existing entries directly in line.
    - Sort the existing entries in alphabetical order by clicking the Sort entries in Alphabetical Order.
12. When finished, press the Save and Sync Fields button to save the values listed on the page to the picklists on all of the objects set up.  You will get an email when the synchronization is done.  With the Pro version, it will do this in all the Orgs you have set up, in addition to the current Org.

## Upgrading Your App

The Standard version of the app will allow you to maintain up to five Universal Picklists in a single Org.  The Pro version gives you much more. To upgrade to the Pro version, you will need to email support@toafinish.com and give the following information:
- Your Org Id.  (Go to Setup → Company Profile → Company Information)
- Company Name, Official Contact Name and Address.  The Upgrade Key should be emailed back within 24 hours, usually much less time than that. This upgrade is currently free, with support being charged at an hourly rate. More information on technical support will be emailed to you at the same time as the key.

Once you receive the upgrade key, click on the Upgrade button and paste the key into the box.  When you have entered a valid key, press the OK button to unlock the Pro functionality in the app. Refresh the page manually if it does not refresh.

## Setting up Additional Orgs

Once you have upgraded to the Pro version of the app, you can start controlling multiple Orgs from a single, master Org.  We recommend setting up the app in your production system and then setting up multiple entries for each sandbox in your organization.

> Note: You can also control all picklists from a sandbox, but you run the risk of losing all of your work if the sandbox is refreshed.

Follow these steps to add additional entries to your list of Orgs to synchronize with when you press the Save and Sync Fields button on a universal picklist.

1. Go to Setup → Installed Packages and click “Configure” next to the Universal Picklists app package.
2. Press the Additional Orgs button.
3. Press the New button.
4. Enter all the information in the popup.  When you press the Save button, the app will add a Remote Site to the current Org and verify that it can access the org.  
 
#### FIELD DESCRIPTIONS

- **Name** The name to be displayed on the list; also the name of the Remote Site that will be created in the current org.  That means that the name cannot have any spaces in it.
- **Username** The username in email address format used to log into an Org
- **Password** The password used to log into an Org
- **Security token** The token needed by an external system to log into an Org.  This is needed most cases, but not all.  To get a security token, you can log into the desired Org and Go to: My Settings → Personal → Reset My Security Token.  This will email you a new security token.  

> Note: Do not do this if another external system is already using a security token, or else the previously issues token will be invalidated.  Simply use the one that was email previously.

> Note: If the option to reset your security token is not available, it will most likely be due to your IP address being whitelisted in the org, so that the 2nd security measure is not needed.  This is often the case for administrators who want to get around the constant entering of security codes in order to get into Salesforce.  In order to get the security token, you may need to remove the IP whitelisting and go back to the menu again.

- **Remote Site Setting** This will usually be https://test.salesforce.com, but if the org you are adding has a custom domain, you might need to put it here.  You can find it by simply logging into the Org and checking your browser’s address bar.

- **Type** Select Production, Sandbox or Local.  Note that it is strongly recommended that you manage the Universal Picklists directly from your Production system, so you should not need to enter a production org here, but the Production option is available in case you need to manage picklists from a sandbox.  The *Local* option is ignored during picklists syncs.  It is used exclusively for the End User Picklist Management function.  This is the login into the current org that the end user will use (without seeing it) to modify picklists, using the authority of the login included here.

Once an Org is added, you can close the Additional Org list and from now on, every time you press the Save and Sync Fields button, the Orgs in this list will be updated. 
 
> NOTE: You can only have one “Production” org in your Org list.  If your organization uses more than one production org, or, if you have the technical need to manage both production Orgs from a single location, please email support@toafinish.com and request help with setting this up. Support is billed at the regular rate.

## Setting Up Picklist Management for End Users

End users without System Administrator permissions are able to update picklists that you set up in the regular configuration page.  They cannot add picklists or delete them, but they are able to update the values in those picklists.  This can be very valuable functionality if you trust that certain users can own the picklist values while still restricting them from doing other functions in the Setup area.

#### End User Permissions

The specific end users who need to manage picklist values need certain permissions in order to do so.  They don’t need System Administrator permissions, but they do need access to the objects, pages and classes to use, as well as one permission to allow them access to custom settings.

1. Go to Setup → Administer → Manage Users → Permission Sets.  Find the one called Universal Picklists User (Template) and click on it.
2. Click on the Clone button.   Enter any name you want to use, and Save.
3. Once you are in your new (not the original) Permission Set, click on the System Permissions link, and then press the Edit button to edit the list.
4. Turn the “Manage Custom Permissions” permission ON, and Save.
5. Click the Manage Assignments button and then use this page to add any user you want to have access to the end user picklist management pages.  Exit when done, and go to the next step.

#### System Administrator Credentials Setup

The end users who you set up in the previous step will need System Administrator credentials in order to do the actual changes.  They will not be assigned these credentials, rather, the Picklist Update page they use will employ the credentials behind the scenes to give them more power, this specific area, than they would typically have.

1. Go to Setup → Installed Packages and click “Configure” next to the Universal Picklists app package.
2. Press the Additional Orgs button.
3. Press the New button.
4. Enter all the information in the popup using the table below.  When you Save, the app will be configured to access the current org as a system administrator.

- **Name** The name to be displayed on the list; use something like “LocalAdminAccess”.
- **Username** The username in email address format used to log into an Org
- **Password** The password used to log into an Org
- **Security token** The token needed by an external system to log into an Org.  This is needed most cases, but not all.  To get a security token, you can log into the desired Org and Go to: My Settings → Personal → Reset My Security Token.  This will email you a new security token.  

> Note: Do not do this if another external system is already using a security token, or else the previously issues token will be invalidated.  Simply use the one that was email previously.

> Note: If the option to reset your security token is not available, it will most likely be due to your IP address being whitelisted in the org, so that the 2nd security measure is not needed.  This is often the case for administrators who want to get around the constant entering of security codes in order to get into Salesforce.  In order to get the security token, you may need to remove the IP whitelisting and go back to the menu again.

- **Remote Site Setting** This will usually be https://login.salesforce.com/, but if your org has a custom domain, you might need to put it here.  You can find it by simply logging into the Org and checking your browser’s address bar.
- **Type** Select Local.  This option is used exclusively for the End User Picklist Management function.

Once an Org is added, you can close the Additional Org list and from now on, every time you press the Save and Sync Fields button in the Picklist Update page, the “Local” entry in this list will be used to update the picklist.

You are now pretty much done.  You might want to add the “Picklist Update” page to your user’s apps, or instruct them to go to the “All Tabs” section and find the page.   

Send any comments or documentation improvement suggestions to support@toafinish.com.

Enjoy. Responsibly.
