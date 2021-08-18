---
title: AUTOCONT SOLUTIONS - AC Parcels - Balikobot integration - setup | Microsoft Docs
description: This section describes parcel functionality - Setup of Balikobot
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, shipment, parcels, Shipping, settings
ms.date: 06/24/2020
ms.author: v-makune
---

# Setup - AC Parcels - Integration Balikobot

There are several areas that need to be set up for the AC Parcel addon to work properly. The addon is initially set up using the wizard and then the settings can be changed manually.

## Addon settings areas:
- Numbered series
- Expedition places
- Shipment Settings
- Shipping agents
- Location Settings
- Shipment parameters
- Print Settings
- Payment settings (COD)

The other data sets (Shipping agent services, Handling Units and Carrier Branches) are downloaded from the API of Balikobot.

## Setting up AC Parcels using the wizard

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Assisted setup**, and then choose the related link.  
2. Run Setup Parcels assisted setup. 
3. After you read entry instructions click Next. 
4. If you want to manually import Rapid Start configuration you can do it, otherwise, click Next and it will be downloaded and applied automatically. 
5. Open page Expedition places and enter new record:
   - Code
   - Username
   - User password
6. You can even fill in the optional information: 
   - Description
   - Name
   - Adress
   - City
   - Postcode
7. In the field **Expedition Place code** select your created expedition place and click Next. 
8. Open location list page and her open location card ZÁPADNÍ. 
9. Assign location by choosing your created expedition place in the **Expedition place code** field. 
10. Close the card and the list and click Next. 
11. Create new shipping agent Česká pošta with following details:
      - Code:
      - Name:
      - Integration service:
      - Balikobot code:
      - Allow More packages: Yes 
      - Master Data sync: Yes 
12. Click action **Synchronize master data** and click Next. 
13. In the field **Parcel Nos.** select ZASILKY and click Next. 
14. After you will click Finish, the Parcel Setup wizard will synchronize selected data. 
## Manual adjustment of settings
### Expedition Places

The Expedition Places are locations of your warehouses from where shipments are dispatched. A user can have several expedition places. A different API is required for each expedition place, and the expedition place is associated with one location of your company. 

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Expedition places**, and then choose the related link.
2. Choose the function **New**
3. Insert **Code** for expedition place, description, address and **User Name and password** to yours API.
4. Close the list of Expedition places.

![Settings AC Parcels](media/BB_exp_pl.png)

### Location Settings
In the location tab, you need to select the expedition place that is associated with the API. If there are multiple locations, you will need to set the appropriate expedition place on each location. This is to limit user errors so that users cannot combine documents with different shipping locations into a shipment.

To assign a expedition place to a location, you need to set the filed **Expedition Place Code**.

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Location**, and then choose the related link.
2. Open the location card.
3. Fill field **Expedition Place Code** in General FastTab.

![Settings AC Parcels](media/BB_lokace.png)
### Parcels Management Setup

Basic settings for AC Parcels - Integration BalikoBot must be made on the **Parcels Management Setup** page.
![Settings AC Parcels](media/BB_setup.png)

Parcels Management Setup page contain:
 - **Parcels Nos.** - Specifies the No. Series for parcels.
 - **Default Expediton Place Code** - Specifies the API credentials and shipment location from where the parcel will be shipped.
 - **Print Handover After Order** – Automatic print of Handover protocols after collection order.
 - **Default Printer Name** – Specifies the printer for printing labels and handover protocols.
 - **Limit Response Time** – Specifies the timeout of communication.
 - **Activity Log Enabled** - Starts activity log tracking.
 - **Debug Mode** – Enables message catching in communication with the service.
 - **Automatic synchronization of master data** - Executes a procedure on the job queue that updates all data from the PackageBot side within a certain time period.
 - **Automatic tracking status update** - Runs a procedure on the job queue that updates the status of the shipment overflow for the last month at a specific time period.


**Basic setup is done using the application setup wizard.**
The other tables are downloaded and loaded after master data synchronization is enabled.
These data are updated manually using the "Resync master data" function.
#### Základní nastavení AC Parcels - Integrace Balíkobot

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Parcel Setup**, and then choose the related link.
2. Choose Parcel Nos.
4. Choose default Expedition place
5. Enable Print Handover After Order, Activity Log Enabled, Automatic synchronization of master dataand Automatic tracking status update.
### Shipping Agent Setup
The base dataset is loaded using the RapidStart package for Business Central. This package contains data that is not downloaded from the PackageBot API.
#### Shipping Agent Table

The other tables are downloaded and populated after synchronizing the master data and in the carrier table.
These data are updated manually using the "Resync master data" function.

![Setup AC Parcel](media/BB_shipping-agents.png)
 
The list also includes shipping agents that you do not have configured with Balíkobot. For such, no additional data import is performed (see below).
### There are several fields to set in the Shipping agent list:
 - **Integration service** – Specifies the type of service providing integration API. The service is called when you send and receive data of parcels.
 - **Master data Sync. Enabled** – Specifies that synchronization of master data with the integration service is enabled.
 - **Master Data Last Sync.** – Specifies the last time a synchonization of master data has been performed.
 - **Balikobot Enabled** - Shipping agent is enabled a ready to use.
 - **Allow More Packages** - When creating a shipment, the feature allows you to create multiple packages within a single shipment.
 - **Pallet Shipping**
 - **No. Of Allowed Man. Units** - Multiple handling units can be set up for pallet transport.
 - **Branches Only** – Specifies that the carrier serves only as a dispensing point.
 - **Maximum Address Length** – Sets the address length for the selected carrier.
 #### Functions over Shipping Agents
 - **Test connection** – Communication test between the integration service and Business Central.
 - **Synchronize Master Data** – Starts master data synchronization.
 - **Shipping Agent Services** - Table of services of shipping agent.
 - **Shipping Agent Branches** - Table of locations where customers can collect goods from the carrier.
 - **Manipulation Units** - Table of pallet handling units
 - **ADR Units** – Table of ADR units.

If you add a Shipping agent after the initial setup has been performed using assisted setup, you must fill in the fields correctly:
- Code
- Package Tracking URL
- Integration Service
- Code Balikobot

Then you must use the **Sync master data** function!

### Setting up Shipping Agent Services

Shipping Agent Services are downloaded automatically from Balikobot API. It is possible to enforce certain settings for individual carrier services. For the settings you have to:
1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Shipping Agent**, and then choose the related link.
2. Select the Shipping Agent from the list and select **Shhipping Agent Services**
3. On the following page, fill in the fields as required:
    - **Balikobot Enabled** - Službu je možné používat (ve výchozím stavu povoleno)
    - **Enforce Parcel Weight**
    - **Enforce Parcel Cubage**
    - **Enforce Parcel Price**
    - **Enforce Parcel Cash On**
    - **Enforce Parcel Variable symbol**
    - **Enforce Parcel Weight on line**
    - **Enforce Parcel Cubage on line**
### Parcel Parameters Setup

Parameters for each Shipping agent are downloaded from the Balikobot API.
### Payment method settings - Cash on delivery

To set up and use the Cash on Delivery feature, you need to set the **Cash on Delivery** field on the payment method.

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Payment method**, and then choose the related link. 
2. In the overview select boolean **Delivery** for the given payment method
3. Close payment method overview
 ## Print Setup
### PDF reader
To print labels, you need to have install PDF reader. For working with labels we recommend Foxit PDF and also have it set as the default program for PDF files on your server or computer.
### Print format selection - Client zone
The basic step of setting up label printing is to define how the label PDFs will be generated from the Balikobot side. In the client area (https://client.balikobot.cz/), the user must set whether to print in full page format or by position on A4 size paper. It all depends on which printer it will be printed on. For printing on a label printer, the label printing position does not need to be selected.
### Printer Selection
 To set up label printing, you need to set the report ID and assign a printer to the user. The label printing function is set to print on the defined printer.

The following steps are required for printer definitions:
1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Printer Selection**, and then choose the related link.  
2. Choose **New**
3. In New line fill fields:
   - User ID
   - Report ID - 52O68430 Print Parcel Labels
   - Printer Name
4. Close Printer Selection page.

The printout of the handover report is printed automatically after ordering the collection. If the user does not want automatic printing, just disable Boolean - Printing of collection handover reports in the Parcel Settings. Printing is done from the Default Printer according to your device. Alternatively, if you have set the default printer in **Printer Selections** as the rest of your print reports.


## See Also
[Parcels](ac-parcels.md)  
[AC Productivity Pack](ac-productivity-pack.md)  
[AUTOCONT Solutions](../index.md)
