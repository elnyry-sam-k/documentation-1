# Administrator' User Guide

## Overview
To get started with using the Admin portal, an admin user must be assigned to a zone.

### Creation of First Admin user

1. Setup of hierarchial zones (using DML scripts)
2. Create Admin roles in KeyCloak (using scripts)
3. Create first admin user in KeyCloak (scripts available)
4. Assign first user to root zone (scripts available)

### First user login

 ![](_images/admin-login.png)
 
1. Select the preferred language in the Admin login screen
2. Login with the KeyCloak credentials.
3. Admin user can view the Home page.

Note: The admin portal integrates with the KeyCloak IAM to store users and provide the login functionality.
  
 ### Admin UI- Home page
 
 ![](_images/admin-home.png)
 
 **MENU BAR**
 
 On successful login, the user can see the following on the menu bar:
 
     * MOSIP logo
     * Zone of the logged in user
     * Admin UserName
  
The options seen on the left navigation pane is displayed or hidden based on the role of the logged in admin user.

### First user actions

1. Map the other users(admins/registration operators/supervisors) to respective zones
2. Create centers and assign the users to a particular center

Note: Ensure to revoke the first super user's zone mapping and role after first user actions are completed.

Post setup, the following operations can be done using the Admin application:
* Center management
* Device management
* Machine management
* User management
* Other Master Data management
* Bulk operations
* KeyManager operations

Registration related services
* Packet status
* Retrieve Lost RID
* Pause/ Resume RID

### Admin Roles and their default accessibility matrix

* GLOBAL_ADMIN
* ZONAL_ADMIN
*	REGISTRATION_ADMIN
* MASTERDATA_ADMIN
*	KEY_MAKER

Based on the role, following are the menu list accessible to the admin users:

|GLOBAL_ADMIN|ZONAL_ADMIN|REGISTRATION_ADMIN|MASTERDATA_ADMIN|KEY_MAKER|
|------|-----|-----|-----|-----|
|Centers|Devices|Packet Status|All Master Data|GenerateMasterKey|
|User Zone Mapping|Machines|Pause/ Resume RID|Bulk Upload||||||
|All Master Data|User Zone Mapping|Retrieve Lost RID|GenerateCSR|||||
|Bulk Upload|User Center Mapping|Packet Upload|GetCertificate||||
|GenerateCSR|All Master Data||UploadCertificate|||
|GetCertificate|Bulk Upload||UploadOtherDomainCertificate||
|UploadCertificate|GenerateCSR||||
|UploadOtherDomainCertificate|UploadCertificate||||
||UploadOtherDomainCertificate||||

### RESOURCE MANAGEMENT

#### Center Management
* Admin portal allows an administrator to manage registration centers setup by the country for taking registrations of the residents.
* Center management includes functionalities like viewing, creating, editing, activating, deactivating and decommission of centers. 
* An admin can manage only centers under his/her administrative zone.

**View Center**

![](_images/admin-view-center.png)

To view the list of centers,
1. Click Resources-> Center
2. For a detailed view, click on a particular center name. 
This detailed view shows all the details of a registration center in the logged in language.
3. To apply a filter, click **Filter**.
The administrator can filter the list of registration centers based on parameters like *Center name, Center type, Status, Location hierarchy (all location levels)*.
 
![](_images/admin-view-center-filter.png)

* The system does not fetch the details of decommissioned registration centers but only active and inactive centers. 
* If the admin does not find a center, they can click the *Center not available in logged in language* button. Clicking on this button, displays the list of centers that are already created in other languages. On selecting a particular center, the information will be auto-populated data in the Create page and be made available to the admin to modify language specific fields to create a center in the current logged in language.

**Create Center**

![](_images/admin-create-center.png)

To create a center,
1. Click Resources-> Center
2. Enter the mandatory details.
3. Click **Create**.

* An admin can create a center by providing data in the fields marked as mandatory. 
* A center is created with the following attributes: Center name, center type, address, latitude, longitude, location, contact phone, contact person, working hours, no. of kiosk, center start time, center end time, lunch start time, lunch end time, time zone, holiday zone and administrative zone the center belongs to.
* A center can only be mapped to the configured location hierarchy level. 
* While defining centers, an admin can also define the working days of the week for a center and any exceptional holidays that might be applicable for a particular center.

**Update Center**

![](_images/admin-edit-center.png)

To update a center,
1. Click Resources-> Center
2. Select the **Edit** option from the Actions menu against a center name.
3. Make the changes in the required fields.
4. Click **Update**.

*Note - Updates made to language specific fields updates data only for that language in the database while updates made to non-language dependent fileds updates data against all the language entries for that center. 

**Activate/Deactivate/Decommission center**

![](_images/admin-deactivate-center.png)

To activate/deactivate/decommission a center,
1. Click Resources-> Center
2. Select the **Deactivate/Decommission** option from the Actions menu against the center name.
3. On the confirmation pop-up, click **Confirm**.

* Deactivation refers to a temporary shut down while decommission refers to a permanent shut down of the center. 
* Decommissioning a center also automatically deactivates the center. In cases where a center has some resources mapped to it (e.g. machines, devices or users), the portal will not allow the admin to decommission such a center.
* The primary difference between *deactivated* and *decommissioned* center is that a deactivated center can be activated later through admin portal as required by the country. But a decommissioned center cannot be bought into commission again as decommission refers to a permanent shutdown.
* Activation/Deactivation/Decommission of a center in one language will be applied to same center created in all other languages.

### Device Management

**Note: Device entity is language agnostic.**

* Admin Portal allows an administrator to manage the Devices a country will use for registering residents.
* These include devices for bio-metric capture (Fingerprint, Iris, Web camera, etc.), printers, scanners.
* Device management includes Viewing, Creating, Editing, Activating, Deactivating and Decommissioning of Devices.

**View Devices**

![](_images/admin-view-device.png)

To view the list of devices,
1. Click Resources-> Devices
2. For a detailed view, click on a particular Device. 
3. To apply a filter, click **Filter**.
The Admin can filter the list of Registration Centers based on parameters like *Device Name, Mac Address, Serial Number, Status, Map Status, Device Type, Device Spec ID.

![](_images/admin-view-device-filter.png)

* The Admin portal allows an administrator to view the list of all Devices available in the jurisdiction of his/her administrative zone. 
* The system does not fetch the details of Decommissioned Devices but only Active and Inactive Devices. 

**Create Devices**

![](_images/admin-create-device.png)

To create a device,
1. Click Resources-> Devices
2. Enter the mandatory details for creating the device.
3. Click **Create**.

* A Device can be created with the following attributes: Device ID, Device Name, Mac Address, Serial Number, Device Spec ID and Administrative Zone the Device belongs to. 
* A Device needs to be mapped to the Administrative Zone it belongs to.

**Update Devices**

![](_images/admin-edit-device.png)

To update a Device,
1. Click Resources-> Devices
2. Select the **Edit** option from the Actions menu against the Device name.
3. Make the required changes in the fields.
4. Click **Edit** and Confirm the changes.

**Activate/Deactivate/Decommission Device**

![](_images/admin-deactivate-device.png)

To activate/deactivate/decommission a Device,
1. Click Resources-> Devices
2. Select the **Deactivate/Decommission** option from the Actions menu against the Device name.
3. On the confirmation pop-up, click **Confirm**.

* Deactivation refers to a temporary shut down while Decommission refers to a permanent shut down of the Device. 
* Decommissioning a Device also automatically deactivates the Machine.
* In cases, where a Device is mapped to any Center, the portal will not allow the Admin to decommission such a Device.
* Difference between Deactivated and Decommissioned Device is that a Deactivated Device can later be Activated through Admin Portal after a period as required by the country.   A Decommissioned Device cannot be bought into commission again as decommission refers to a permanent shutdown. 

**Map/Un-map/Re-map Device to a Center**

![](_images/admin-map-device-center.png)

To map/un-map/re-map device to a center,
1. Click Resources-> Devices
2. Select the device and choose **Center name** from the dropdowm.
3. Click **Edit** and confirm.

* Admin portal allows an Admin to map/un-map each Device to a Center.
* This mapping specifies as to which Center the Device will be used in.
* A Device can only be mapped to a Center which belongs under the Device’s Administrative Zone.

#### MACHINE MANAGEMENT
* Admin portal allows an administrator to manage the machines a country will use for registering residents. 
* In MOSIP, a machine is a device on which the registration client is installed.
* Machine management includes viewing, creating, editing, activating, deactivating and decommissioning of machines. 

**View Machines**

![](_images/admin-view-machine.png)

To view the list of machines,
1. Click Resources-> Machines
2. For a detailed view, click on a particular machine name. 
This detailed view shows all the details of a registration machine in the logged in language.
3. To apply a filter, click **Filter**.
The administrator can filter the list of machines based on parameters like *Machine name, Mac address, Serial number, Status, Machine type.*

![](_images/admin-view-machine-filter.png)

* The admin portal allows an admin to view the list of all the machines available in the jurisdiction of his/her administrative zone. 
* The system does not fetch the details of decommissioned machines but only shows the active and inactive machines. 

 **Create Machines**
 
![](_images/admin-create-machine.png)

To create a machine,
1. Click Resources-> Machines
2. Enter the mandatory details for creating the machine.
3. Click **Create**.

* A Machine can be created with the attributes like *Machine ID, machine name, mac address, serial number, machine spec ID and administrative zone* the machine belongs to.
* While entering data through UI in multiple languages, the dropdown values and numeric values entered in primary language gets automatically captured in all language.
* But the text fields (e.g., machine name) needs to be manually input in all the languages. A machine can be mapped to the administrative zone which is at the any zonal hierarchy.

**Update Machines**

![](_images/admin-edit-machine.png)

To update a machine,
1. Click Resources-> Machines
2. Select the **Edit** option from the Actions menu against the machine name.
3. Make the required changes in the fields.
4. Click **Edit** and Confirm the changes.

*Note - Updates made to language specific fields updates data only for that language in the database while updates made to non-language dependent fileds updates data against all the language entries for that center. 

**Activate/Deactivate/Decommission Machine**

![](_images/admin-deactivate-machine.png)

To activate/deactivate/decommission a Machine,
1. Click Resources-> Machines
2. Select the **Deactivate/Decommission** option from the Actions menu against the Machine name.
3. On the confirmation pop-up, click **Confirm**.

An admin can deactivate or decommission a machine through the admin portal.

**Map/Un-map/Re-map Machine to a Center**

![](_images/admin-map-machine-center.png)

To map/un-map/re-map machine to a center,
1. Click Resources-> Machines
2. Select the machine and choose **Center name** from the dropdowm.
3. Click **Edit** and confirm.

* Admin portal allows an Admin to map/un-map each Machine to a Center.
* This mapping specifies as to which Center the Machine will be used in.
* A Machine can only be mapped to a Center which belongs under the Machine’s Administrative Zone.

### USER MANAGEMENT

* MOSIP uses Keycloak as an IAM (Identity access management tool) for managing Users. These users are internal users of MOSIP including Registration Officers, Registration Supervisors, Zonal Admins, Global Admins etc.
* User Management includes Viewing, Creating, Editing, Activating, Deactivating and Blacklisting of Users.

#### User Zone Mapping
* Once the user is created in KeyCloak, they need to be mapped to a zone to get access to specific information available in that zone.
* Administrative Zones are virtual boundaries which a country can define to manage their resources better during registrations. These resources includes Centers, Users, Machines and Devices. 
* These zones can be defined in a hierarchical fashion and a country can allocate resources to such zones based on their requirements.
* Resources under each zone is managed by a Zonal Admin. This is done by assigning an Administrative zone to the Zonal Admin during user creation. These Zonal Admins can exist at any zonal hierarchy. (For e.g, a Zonal Admin can directly be mapped to the whole country as a Zone or can be mapped to a significantly smaller zone such as a city). Thus these resources when mapped to an Administrative Zone can only be managed by the Admin of that Zone.

**View User Zone Mapping(s)**

![](_images/admin-user-zone-list.png)

**Map/Un-map/re-map user to a Zone**

![](_images/admin-user-zone-map.png)

To map a user to a zone,
1. Click Resources-> User Zone mapping
2. Click **+Map Zone**
3. Select the *User Name, Administrative Zone* from the dropdown.
4. Click **Save**.

To re-map a user to a zone,
1. Click Resources-> User Zone mapping
2. Select **Remap** from the Actions menu against the mapped user.
3. Update the *User Name/ Administrative Zone* from the dropdown.
4. Click **Save**.

Note: If the center is mapped already, the admin needs to unmap the center to remap the zone.

* Admin portal allows an admin to map users to a zone. This mapping specifies as to which zone the user will belong to.
* A user can only be mapped to a zone which belongs under the User’s Administrative Zone.
* A user can later be un-mapped from the zone in case a user needs to be moved to another zone. In such cases, the user will later need to be mapped to the new zone. 

![](_images/admin-user-zone-mapping.png)

#### User Center Mapping

* Once the user is mapped to a zone, they will be listed in the screen below. Now, the user will be mapped to a center to be able to manage their assigned center.
* Admin portal allows an admin to map users to a center. This mapping specifies as to which center the user will be used in. 
* A user can only be mapped to a center which belongs under the user’s Administrative Zone.
* A user can later be un-mapped from the Center in cases where a User is needed to be moved to another Center. In such cases, the user will later need to be mapped to the new center. In case the user is required to be mapped to a Registration Center outside the Administrative Zonal restriction, the Administrative Zone of the user must be changed.

**View User Center Mapping(s)**

![](_images/admin-user-center-list.png)

**Map/Un-map/re-map user to a Registration Center**

![](_images/admin-user-center-map.png)

To map a user to a center,
1. Click Resources-> User Center Mapping
2. Select **Map** from the Actions menu against the mapped user.
3. Select the *Center name* from the dropdown against the User Name, Administrative Zone.
4. Click **Save**.

### PACKET STATUS (based on RID)
* A Registration packet generated in Registration Client is sent to Registration Processor for further processing and UIN generation. 
* Using the Portal, A Registration Admin can view the status of a packet by entering the RID of the packet. 
* The packet status will contain all the stages the packet has passed through along with the last stage the packet is in. 
* In case the packet has not been processed or is marked for *Re-Send/Re-Register*, the admin will be able to view specific comments indicating the reason for that particular status.

![](_images/admin-packet-status.png)

### PAUSE/ RESUME RID 
* The Registration Admin has the privilege to view the registration packets that gave been paused for getting processed further.
* They make perform certain validations and if need be, they can resume the packet processing.

![](_images/admin-packet-status.png)

### RETRIEVE LOST RID
The Registration Admin can use this feature to retrieve lost RID. For instance, if the resident did not provide any valid email and/or phone number and has lost the RID slip received during the registration, in order to find their RID details, the resident contact MOSIP helpline and share details such as name, centre name, registration date and postal code to the admin, who will use the lost RID feature and try to retrieve the RID number.

A few filters may be applied to retrieve the RID.

![](_images/admin-retrieve-lost-rid.png)

Note: This feature is currently under development.

### MASTER DATA MANAGEMENT
* Admin portal allows an administrator to manage the Masterdata applicable for a country.
* These data includes list of Genders, list of Holidays, Templates etc. This data is used by all the modules across MOSIP which includes Pre-Registration, Registration Client, Registration processor and ID-Authentication.
* An Administrator should have the role of a Global Admin to manage Masterdata.

![](_images/admin-master-data.png)

#### Manage Master Data**

***Common***

**Center Types**
* Registration Center Type indicates the type of Centers a country can have. Some examples can be Regular, Mobile, temporary etc. 
* The Global Admin can view list of all the available Registration Center Types on the Admin UI portal. 
* A registration center while creation, can be assigned to a Center Type as defined by the country. 
* The portal shows both activated or deactivated Center Types. 
* The Admin can filter the list of Center Types based on Status (Drop-down).

View center type

![](_images/admin-master-data.png)

Create center type

![](_images/admin-center-type-create.png)

1. Click Master Data-> Center Types
2. Click **+Create**
3. Enter the necessary details
4. Click **Save**



Edit\Deactivate Center type
Admin Portal also allows modification of any detail of a Registration Center Type. 

(Although the Portal will allow creation of a Registration Center Type in only primary language but will not allow activation of that Registration Center Type until data for that Type is not updated for all the languages. While entering the data, the text fields (e.g., Registration Center Type Name) needs to be manually input in all the languages. After successful creation, a Registration Center Type code will be generated.)



Blocklisted Words -
* The Global Admin can view list of all the available Blocklisted words on the Admin UI portal. 
* The portal shows both activated or deactivated Blocklisted words. Blocklisted words in the only Masterdata which is language independent and will show the data in all the languages unlike the rest of the Masterdata tables which will show data only in the logged in language. The Admin can filter the list of Blocklisted Words based on Status (Drop-down), Blocklisted Words (Search Box).
* Admin can also add\edit\deactivate blocklisted words.
* Deactivation of a Blocklisted Word can be done if the country feels the Blocklisted word is not applicable anymore. 

![](_images/admin-blocklisted-words.png)





List of Holidays 
List of Holiday defines all the public holiday a applicable for a country. These holidays are on of the criteria for Pre-Registration to generate appointments. The holidays only define the public holidays and not the week-end days for the country. The Global Admin can view list of all the defined Holidays on the Admin UI portal. The portal shows both activated or deactivated Holidays. The Admin can filter the list of Holidays based on Status (Drop-down), Date Range (Search Box) and Name (Search Box).
Create/Update Holidays
Using the portal, the Global Admin can create a Holiday providing the Document Category name, date, location, and description if applicable. A Holiday needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Holiday in only primary language but will not allow activation of that Holiday until data for that Holiday is not updated for all the languages. A deactivated Holiday will not be considered for appointment generation in Pre-Registration While entering the data, the text fields (e.g., Holiday Name) needs to be manually input in all the languages. After successful creation, a Holiday ID will be generated.
Admin Portal also allows modification of any detail of a Holiday. The modification includes either adding the details in another language that were missed during creation of the Holiday or changing the details of a Holiday itself including name, description etc.

Templates

List of Holiday defines all the public holiday a applicable for a country. These holidays are on of the criteria for Pre-Registration to generate appointments. The holidays only define the public holidays and not the week-end days for the country. The Global Admin can view list of all the defined Holidays on the Admin UI portal. The portal shows both activated or deactivated Holidays. The Admin can filter the list of Holidays based on Status (Drop-down), Date Range (Search Box) and Name (Search Box).
Create/Update Holidays
Using the portal, the Global Admin can create a Holiday providing the Document Category name, date, location, and description if applicable. A Holiday needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Holiday in only primary language but will not allow activation of that Holiday until data for that Holiday is not updated for all the languages. A deactivated Holiday will not be considered for appointment generation in Pre-Registration While entering the data, the text fields (e.g., Holiday Name) needs to be manually input in all the languages. After successful creation, a Holiday ID will be generated.
Admin Portal also allows modification of any detail of a Holiday. The modification includes either adding the details in another language that were missed during creation of the Holiday or changing the details of a Holiday itself including name, description etc.

Dynamic Field

Create New Dynamin Field

Gender
View Gender Types
List of Gender Types contains all the Gender types defined by a country. The Global Admin can view list of all the defined Genders on the Admin UI portal. The portal shows both Activated or Deactivated Gender types.
Create/Update Gender Types
Using the portal, the Global Admin can create a Gender Type providing the Gender Type nameand description if applicable. A Gender Type needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Gender Type in only primary language but will not allow activation of that Gender Type until data for that Gender Type is not updated for all the languages. A deactivated Gender Type will not show up on the Pre-Registration/Registration Client UI. While entering the data, the text fields (e.g., Gender Type Name) needs to be manually input in all the languages. After successful creation, a Gender Type code will be generated.
Admin Portal also allows modification of any detail of a Gender Type. The modification includes either adding the details in another language that were missed during creation of the Gender Type or changing the details of a Gender Type itself including name, description etc.

Registration Type 
Mode of Claim
User preferred language
residenceStatus
Blood Type
Marital Status

Device Definitions
Device Specs
Device Types

Machine Definitions


Machine Specs
Machine Types

View Machine Types
Machine Type indicates the type of Machines a country uses to take registrations. The Global Admin can view list of all the Machine Types on the Admin UI portal. A Machine while creation, can be assigned to a Machine Types as defined by the country. The portal shows both activated or deactivated Machine Types.
Create/Update Machine Types
Using the portal, the Global Admin can create a Machine type providing the Machine type name and description if applicable.
A Machine type needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Machine type in only primary language but will not allow activation of that Machine type until data for that Type is not updated for all the languages. While entering the data, the text fields (e.g., Machine type Name) needs to be manually input in all the languages. After successful creation, a Machine type code will be generated.
Admin Portal also allows modification of any detail of a Machine Type. The modification includes either adding the details in another language that were missed during creation of the Machine Type or changing the details of a Machine Type itself including name, description etc.
View Machine Specifications
Machine specification indicates the Brand, Make and Model of a Machine a country uses to take registrations. The Global Admin can view list of all the Machine Specifications on the Admin UI portal. A Machine while creation, can be assigned to a Machine Specification as required by the country. The portal shows both activated or deactivated Machine Specification. The Admin can filter the list of Machine Specifications based on Status (Drop-down), Name (Search Box), Brand (Search Box), Model (Search Box), and Machine type (Search Box).
Create/Update Machine Specifications
Using the portal, the Global Admin can create the Machine Specification providing the Machine Specification name, brand, make and model. A Machine Specification needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Machine Specification in only primary language but will not allow activation of that Machine Specification until data for that Specification is not updated for all the languages. While entering the data, the text fields (e.g., Machine Specification Name) needs to be manually input in all the languages. After successful creation, a Machine Specification ID will be generated.
Admin Portal also allows modification of any detail of a Machine Specification. The modification includes either adding the details in another language that were missed during creation of the Machine Specification or changing the details of a Machine Specification itself including name, brand etc.

Document Definitions
Document Types
Document Categories
Document Categoty- Type Mapping

Manage Document Type (View, Create, Update, Activate, Deactivate)
Document types is the list of Documents a country will configure for the users to give during registrations.
View Document Types
The Global Admin can view list of all the available Document Types on the Admin UI portal. The portal shows both activated or deactivated Document Types. The Admin can filter the list of Document Types based on Document Name(Search box) and Status (Drop-down).
Create/Update Document Types
Using the portal, the Global Admin can create the document type providing the Document name and description if applicable. A Document type needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Document type in only primary language but will not allow activation of that Document type until data for that Type is not updated for all the languages. A deactivated document type will not show up on the Pre-Registration/Registration Client UI. While entering the data, the text fields (e.g., Document Type Name) needs to be manually input in all the languages. After successful creation, a Document type code will be generated.
Admin Portal also allows modification of any detail of a Document type. The modification includes either adding the details in another language that were missed during creation of the Document type or changing the details of a Document Type itself including name, description etc.
Activate/Deactivate Document types
The portal allows Zonal Admin to activate or deactivate a document type. Deactivation of a document type can be done if the country feels the document type is not applicable anymore. Thus, deactivated documents does now show up on the Pre-Registration and Registration Client UI. The Activation/Deactivation functionality can be accessed from both the list view or the detail view page of Document Types
View Document Categories
The Global Admin can view list of all the available Document Categories as created by the Country in Masterdata. The portal shows both activated or deactivated Document Categories. The Admin can filter the list of Document Categories based on Status (Drop-down).
Create/Update Document Categories
Using the portal, the Global Admin can create the document category providing the Document Category name and description if applicable. A Document category needs to be created in both configured Primary and Secondary language. Although the Portal will allow creation of a Document category in only primary language but will not allow activation of that Document category until data for that Cateagory is not updated for all the languages. A deactivated document category will not show up on the Pre-Registration/Registration Client UI. While entering the data, the text fields (e.g., Document category Name) needs to be manually input in all the languages. After successful creation, a Document category code will be generated.
Admin Portal also allows modification of any detail of a Document category . The modification includes either adding the details in another language that were missed during creation of the Document category or changing the details of a Document category itself including name, description etc.
View mappings of Document Categories and Document Types
The portal allows an Global Admin to view Document Categories along with its mapped and un-mapped Document Types. From the view screen itself, the Global Admin can map or un-map the Documents from a Document Category.
Map/Un-map Document Type to Document Category
The portal allows the Global Admin to map the available Document types to a Document category. This feature helps the country define as to which document falls under which category. Each Document can be mapped to multiple categories depending on the country's requirement.


### BULK UPLOAD

Master Data

Packets

### KeyManager

GenerateCSR

GetCerificate

UploadCertificate

UploadOtherDocumentCertificate


