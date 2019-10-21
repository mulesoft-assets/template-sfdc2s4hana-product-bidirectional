
# Anypoint Template: Salesforce to SAP S/4HANA Product Bidirectional Sync	

<!-- Header (start) -->

<!-- Header (end) -->

# License Agreement
This template is subject to the conditions of the <a href="https://s3.amazonaws.com/templates-examples/AnypointTemplateLicense.pdf">MuleSoft License Agreement</a>. Review the terms of the license before downloading and using this template. You can use this template for free with the Mule Enterprise Edition, CloudHub, or as a trial in Anypoint Studio. 
# Use Case
<!-- Use Case (start) -->
As a Salesforce administrator I want to have my Products synchronized between SAP S/4HANA and Salesforce organization.

This Template should serve as a foundation for setting an online bi-directional sync between SAP S/4HANA Product and Salesforce Product Objects.

The integration main behaviour is polling for changes (new Products or modified ones) that have occurred either in SAP S/4HANA or Salesforce during a certain defined period of
time. For those Products that both have not been updated yet the integration triggers an upsert (update or create depending on the case) taking the last modification as the one that should be applied.

Requirements have been set not only to be used as examples, but also to establish a starting point to adapt your integration to your requirements.

### Template overview
Let's say we want to keep Salesforce instance synchronized with SAP S/4HANA. Then, the integration behavior can be summarized just with the following steps:

1. Ask Salesforce:
*Which changes have there been since the last time I got in touch with you?*

2. For each of the updates fetched in the previous step (1.), ask SAP S/4HANA:
*Does the update received from Salesforce should be applied?*

3. If SAP S/4HANA answer for the previous question (2.) is *Yes*, then *upsert* (create or update depending each particular case) SAP S/4HANA with the belonging change

4. Repeat previous steps (1. to 3.) the other way around (using SAP S/4HANA as source instance and Salesforce as the target one)

Repeat *ad infinitum*:

5. Ask Salesforce:
*Which changes have there been since the question I've made in the step 1.?*
And so on...
<!-- Use Case (end) -->

# Considerations
<!-- Default Considerations (start) -->

<!-- Default Considerations (end) -->

<!-- Considerations (start) -->
To make this template run, there are certain preconditions that must be considered. All of them deal with the preparations in both source (SAP S/4HANA) and destination (SFDC)
systems, that must be made for the template to run smoothly. Failing to do so can lead to unexpected behavior of the template.

Before you continue with the use of this template, you may want to check out this [Documentation Page](https://docs.mulesoft.com/connectors/sap/sap-s4hana-cloud-connector), that teaches you how to work with SAP S/4HANA and Anypoint Studio.
<!-- Considerations (end) -->

## Salesforce Considerations

Here's what you need to know about Salesforce to get this template to work:

- Where can I check that the field configuration for my Salesforce instance is the right one? See: <a href="https://help.salesforce.com/HTViewHelpDoc?id=checking_field_accessibility_for_a_particular_field.htm&language=en_US">Salesforce: Checking Field Accessibility for a Particular Field</a>.
- Can I modify the Field Access Settings? How? See: <a href="https://help.salesforce.com/HTViewHelpDoc?id=modifying_field_access_settings.htm&language=en_US">Salesforce: Modifying Field Access Settings</a>.

### As a Data Source

If the user who configured the template for the source system does not have at least *read only* permissions for the fields that are fetched, then an *InvalidFieldFault* API fault displays.

```
java.lang.RuntimeException: [InvalidFieldFault [ApiQueryFault
[ApiFault  exceptionCode='INVALID_FIELD'
exceptionMessage='Account.Phone, Account.Rating, Account.RecordTypeId,
Account.ShippingCity
^
ERROR at Row:1:Column:486
No such column 'RecordTypeId' on entity 'Account'. If you are attempting to
use a custom field, be sure to append the '__c' after the custom field name.
Reference your WSDL or the describe call for the appropriate names.'
]
row='1'
column='486'
]
]
```

### As a Data Destination

There are no considerations with using Salesforce as a data destination.
## SAP S/4HANA Considerations

Here's what you need to know to get this template to work with SAP S/4HANA.

### As a Data Source

There are no considerations with using SAP S/4HANA as a data destination.
### As a Data Destination

There are no considerations with using a SAP S/4HANA as a data origin.
# Run it!
Simple steps to get this template running.
<!-- Run it (start) -->

<!-- Run it (end) -->

## Running On Premises
In this section we help you run this template on your computer.
<!-- Running on premise (start) -->

<!-- Running on premise (end) -->

### Where to Download Anypoint Studio and the Mule Runtime
If you are new to Mule, download this software:

+ [Download Anypoint Studio](https://www.mulesoft.com/platform/studio)
+ [Download Mule runtime](https://www.mulesoft.com/lp/dl/mule-esb-enterprise)

**Note:** Anypoint Studio requires JDK 8.
<!-- Where to download (start) -->

<!-- Where to download (end) -->

### Importing a Template into Studio
In Studio, click the Exchange X icon in the upper left of the taskbar, log in with your Anypoint Platform credentials, search for the template, and click Open.
<!-- Importing into Studio (start) -->

<!-- Importing into Studio (end) -->

### Running on Studio
After you import your template into Anypoint Studio, follow these steps to run it:

+ Locate the properties file `mule.dev.properties`, in src/main/resources.
+ Complete all the properties required as per the examples in the "Properties to Configure" section.
+ Right click the template project folder.
+ Hover your mouse over `Run as`.
+ Click `Mule Application (configure)`.
+ Inside the dialog, select Environment and set the variable `mule.env` to the value `dev`.
+ Click `Run`.
<!-- Running on Studio (start) -->
After you import your template into Anypoint Studio, follow these steps to run it:

+ Locate the properties file `mule.dev.properties`, in
src/main/resources.
+ Complete all the properties required as per the examples in the "Properties to Configure" section.
+ Right click the template project folder.
+ Hover
your mouse over `Run as`.
+ Click `Mule Application (configure)`.
+ Inside the dialog, select Environment and set the variable `mule.env` to the value `dev`.
+ Click
`Run`.

To make this template run on Studio there are a few extra steps that needs to be made.
Check this Documentation Page: [Enabling Your Studio Project for SAP
S/4HANA](https://docs.mulesoft.com/connectors/sap/sap-s4hana-cloud-connector#configuring-the-connector-in-studio-7).
<!-- Running on Studio (end) -->

### Running on Mule Standalone
Update the properties in one of the property files, for example in mule.prod.properties, and run your app with a corresponding environment variable. In this example, use `mule.env=prod`. 


## Running on CloudHub
When creating your application in CloudHub, go to Runtime Manager > Manage Application > Properties to set the environment variables listed in "Properties to Configure" as well as the mule.env value.
<!-- Running on Cloudhub (start) -->

<!-- Running on Cloudhub (end) -->

### Deploying a Template in CloudHub
In Studio, right click your project name in Package Explorer and select Anypoint Platform > Deploy on CloudHub.
<!-- Deploying on Cloudhub (start) -->

<!-- Deploying on Cloudhub (end) -->

## Properties to Configure
To use this template, configure properties such as credentials, configurations, etc.) in the properties file or in CloudHub from Runtime Manager > Manage Application > Properties. The sections that follow list example values.
### Application Configuration
<!-- Application Configuration (start) -->
**Application Configuration**
+ page.size `1000`
+ aggregator.size `10`

**Scheduler Configuration**
+ scheduler.frequency `10000`
+ scheduler.startDelay `0`

**Watermarking Default Last Query Timestamp e.g. 2019-12-13T03:00:59Z**
+ watermark.default.expression `2018-02-25T11:00:00.000Z`


**SalesForce Connector Configuration**

+ sfdc.username `bob.dylan@sfdc`
+ sfdc.password `DylanPassword123`
+ sfdc.securityToken `avsfwCUl7apQs56Xq2AKi3X`
+ sfdc.integration.user.id `1234678`

**SAP S/4HANA Connector Configuration**

+ s4hana.baseUrl `your.s4hana.address.com`
+ s4hana.username `your.s4hana.username`
+ s4hana.password `your.s4hana.password`
+ s4hana.productType `s4hana.productType`
+ s4hana.baseUnit `s4hana.baseUnit`
+ s4hana.productGroup `s4hana.productGroup`

            ​
<!-- Application Configuration (end) -->

# API Calls
<!-- API Calls (start) -->
SalesForce imposes limits on the number of API Calls that can be made.
Therefore calculating this amount may be an important factor to consider. Template calls to the API can be calculated using the formula:

**X / ${page.size}**

Being X the number of Products to be synchronized on each run.

The division by ${page.size} is
because, by default, Products are gathered in groups of ${page.size} for each Upsert API Call in the aggregation step. Also consider that this calls are executed repeatedly every polling cycle.

For instance if 10 records are fetched from origin instance, then 1 api calls to SFDC will be made (1).
<!-- API Calls (end) -->

# Customize It!
This brief guide provides a high level understanding of how this template is built and how you can change it according to your needs. As Mule applications are based on XML files, this page describes the XML files used with this template. More files are available such as test classes and Mule application files, but to keep it simple, we focus on these XML files:

* config.xml
* businessLogic.xml
* endpoints.xml
* errorHandling.xml<!-- Customize it (start) -->

<!-- Customize it (end) -->

## config.xml
<!-- Default Config XML (start) -->
This file provides the configuration for connectors and configuration properties. Only change this file to make core changes to the connector processing logic. Otherwise, all parameters that can be modified should instead be in a properties file, which is the recommended place to make changes.<!-- Default Config XML (end) -->

<!-- Config XML (start) -->

<!-- Config XML (end) -->

## businessLogic.xml
<!-- Default Business Logic XML (start) -->
Functional aspect of the template is implemented on this XML, directed by a batch job that's responsible for creations or updates. The several message processors constitute three high level actions that fully implement the logic of this template:
1. Job execution is invoked from SchedulerFlow (endpoints.xml) every time there is a new query executed asking for created or updated Products.
2. During the *Process* stage, each product is filtered depending on if it has an existing matching product in target system.
3. The last step of the *Process* stage groups the products and creates or updates them in target system.
4. Finally during the *On Complete* stage, the template logs the output statistics data on the console.<!-- Default Business Logic XML (end) -->

<!-- Business Logic XML (start) -->

<!-- Business Logic XML (end) -->

## endpoints.xml
<!-- Default Endpoints XML (start) -->
This file contains the endpoints for triggering the template and for retrieving the objects that meet the defined criteria in a query. You can execute a batch job process with the query results.<!-- Default Endpoints XML (end) -->

<!-- Endpoints XML (start) -->

<!-- Endpoints XML (end) -->

## errorHandling.xml
<!-- Default Error Handling XML (start) -->
This file handles how your integration reacts depending on the different exceptions. This file provides error handling that is referenced by the main flow in the business logic.<!-- Default Error Handling XML (end) -->

<!-- Error Handling XML (start) -->

<!-- Error Handling XML (end) -->

<!-- Extras (start) -->

<!-- Extras (end) -->
