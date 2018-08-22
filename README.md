# UNIVERSAL PICKLISTS IMPLEMENTATION GUIDE

This readme will help you through the implementation of the Universal Picklists app for your Salesforce.com Org.  Thank you for considering our app in your organization. It is a work in progress, so please do take notes and let us know if you run into any issues with the text or if you believe there is a better way to accomplish the tasks we describe.

Before you deploy this solution to your production Org, it is strongly recommended that you test it in a sandbox first. This app is very, very powerful.  It has the power to overwrite multiple fields, including field dependencies, with the click of a single button.  If you are not careful, you could end up with a bunch of cleanup work. Please always test any admin app of this type first, but in particular one that attempts to accomplish tasks which are usually not possible.

Test. Test.  Test.

## Installation and Configuration

First, install the app from the [AppExchange Listing](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N30000000pvmXEAQ).  We recommend starting in a Sandbox and installing in Production after you have tested it thoroughly.  We recommend installing for Administrators only.

After successfull installation, the initial configuration steps in the configuration are completed by clicking the “Configure” button on the Universal Picklists package after it has been installed from the AppExchange.com app store. 

> Setup → App Setup → Installed Packages → Configure

### Setting Up Your Org’s “Remote Site”

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

