---
title: AC - Financial pack - Controling Basic | Microsoft Docs
description: Jednoduchy popis tematu
author: ACMartinKunes

ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.search.keywords: Controling basic, finance 
ms.date: 01/31/2021
ms.author: AC MartinKunes
---
# Application extension set - Settings
> Update: 01.02.2022 
## CreditCheck Control - Settings
### CreditCheck settings

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **CreditCheck Settings**, and then choose the related link.
2. Start the Set Default Web Service feature, which populates the service URL.
3. Use the **Enabled** button to start the service.
 

![CreditCheck - setup](media/credit_check-setup.png)

> [!NOTE]
> If your company does not use Contacts, you must turn on Do not use contacts for CreditCheck. Then, when downloading data from CrediCheck, the fields "CreditCheck status" on the customer's card will be filled directly.

### Update creditworthiness information

You can update manually as needed or let the system update at regular intervals.

To set up automatically, follow these steps:
1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **CreditCheck Settings**, and then choose the related link.
2.	Set the **Automatic Update** flag.

>[!NOTE]
> The created job queue entry is set to run at 6:00 AM on weekdays by default. 

To perform a manual update, use the CreditCheck Status Update feature as follows:

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **CreditCheck Status Update**, and then choose the related link.
2. Press **Ok** to start the service.

### User setup

In the user settings on the General tab, there is a new boolean **Allow change of CreditCheck status**, which, if the user has it checked, then allows him to cancel the imported status. 

### Web resources settings and updates

In the CreditCheck settings, it is possible to turn on the update of web feed creation for all contacts with a completed ID.

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **CreditCheck Settings**, and then choose the related link.
2.	Set the **Auto flag. web resource updates**.

>[!NOTE]
> Creating web feeds for a paid statement is possible using **Aut. update web feeds - Full**, but only if the Access code field is filled.

>[!NOTE]
> The created job queue entry is set to run at 6:00 AM on weekdays by default.


## Setting the Hierarchy proposal of sales prices
### Sales and receivables setup
1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Sales and Receivables Setup**, and then choose the related link.

>[!NOTE]
> Nastavení závisí na používané verz
2. Ve verzi BC17 pro zapnutí zvolte **Hierarchický návrh cen povolen**.

![Hierarchický návrh cen povolen](media/Hierarchical_price_setup.png)

>[!NOTE]
As of BC18, we recommend using a completely new pricing functionality in BC. Select the icon   , enter Function Management, and then select the related link. Verify that you have the Feature Updates: New Sales Pricing Experience feature enabled for all users.


## Payment cumulation settings
### Vendor settings for payment accumulation

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Vendros**, and then choose the related link.
2.	Open the vendor card for which you want to allow payment cumulation.
3.	On the Vendor Card page, on the Payments tab, set **Cumulate Payments**.


### Setting the accumulation parameters on the bank account

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Banks**, and then choose the related link.
2.	Open the bank account tab for which you want to set up payment cumulation.
3.	On the Bank Account Card page, in the Payment Orders / Bank Statements tab, set the cumulation of payments as required.
 

### Payment cumulation settings:
 - **Cumulate payment orders field** – enables / disables cumulation
 - **Field Cumulate export according to variable symbol** – cumulation after VS
 - **Field Cumulate export according to constant symbol** – accumulates for KS
 - **Field Cumulate export according to specific symbol** – accumulates after SS
 - **Variable symbol number series field** – if it is not accumulated according to VS, KS or SS, then the number according to the number series set here is added to the VS field (SS and KS are taken from the first merged line of the command)
 - Field **Description of the accumulated payment order line** – description for the created cumulative line


## Exchange rate controls settings
### Checking for correctness when entering the exchange rate

The upper and lower limits of the value in the local currency can be set for each foreign currency defined in the system. This is especially advantageous for less used currencies, where there is an even greater risk of user error when entering the exchange rate on the document, etc. If the field with the currency limit is empty, the check is not performed.

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Currencies**, and then choose the related link.
2.	Run the **Edit** action.
3.	On the Currency tab page, on the General tab, set the **Rel.Exch.Rate Amt. Upper Limit** and **Rel.Exch.Rate Amt. Lower** Limit fields.

## Checking for the existence of an exchange rate 

In the Finance settings, you enter the date formula that the system will use (in relation to the settlement date) to define the period in which it notifies the user that there is no entry in the exchange rate table. If the Ex.Rate Check DateForm. on Doc is not fulfiled, the notification is turned off.

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **General Ledger Setup**, and then choose the related link.
2.	Run the **Edit** action.
3.	On the Finance Settings page, set the **Ex.Rate Check DateForm. on Doc** field 

>[!NOTE]
> "-1D" is usually set for daily exchange rates.

## Enforcement of receivables - settings
### Enforcement methods

Specific types of recovery can be set using the Enforcement Methods:

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Enforcement Methods**, and then choose the related link.
2.	On the Enforcement Methods page, enter the code for the new record (eg "FACTORING" to distinguish the reason for the claim). You can also add a more detailed description in the Description field.

## Setup of number series extensions
### Number series mask settings

A new field for the number series mask structure has been added to the number series table, where the user defines the positional structure of the number generated in this number series. This feature makes it easier to create new number series for a new fiscal year and reduces errors.

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **No. Series**, and then choose the related link.
2.	In the Mask field, set the combination of fixed and wildcards in the format "XXrrcccc".  
        - XX - fixed part of the number; must be in capital letters, length is not limited (only the total length of the final number).  
        - yyyy (or yyyy) - year designation, which is completed by the generator from the specified start date.  
        - cccc - variable part of a number; must be lowercase, length is not limited (only the total length of the final number)
 
> [!TIP]
> If you set the mask "BVY1rrcccccc", then the generator started with the starting date 1.1.2021 will create No. series Line, where the Starting No. will be "BVY121000001" and the Ending No. will be "BVY121999999".

### Number Series Links Setup 

A new No. Series Link table has been added.  

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Posted Sales Invoices**, and then choose the related link.
2.	Select the **Links** action.
3.	Fill in one of the columns according to the number series:
    - **Linked No. Series** – which number series is to be used in the connected activity, when the source document has a specified number series: order created from demand, order created from bulk order
    - **Posting No. Series** – which number range is to be used for the posted document when the source document has the specified number range: posted sales / purchase / service document (invoice, credit memo), issued reminder, issued penalties, charged delivery / warehouse receipt, posted assembly order, posted inventory receipt / issue, posted physical inventory volume
    - **Shiping No. Series** – which number series is to be used for the posted delivery when the source document has the specified number range: billed sales delivery from the sales order or invoice, transfer delivery from the transfer order
    - **Receiving No. Series** – which number range is to be used for the posted receipt when the source document has the specified number range: charged purchase receipt from the purchase order or invoice, transfer receipt from the transfer order.
    - **Shiping Wh. No. Series** – which number range is to be used for delivery from the warehouse when the source document has the specified number range: delivery from the warehouse from the sales / purchase / transfer order.
    - **Receiving Wh. No. Series** – which number series is to be used for the warehouse receipt when the source document has the specified number series: warehouse receipt from the sales / purchase / transfer order


## Rounding setup according to the method of payment 

Rounding settings are made differently depending on the currency, as is the case with other similar parameters:

**Local currency setup**

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **General ledger Setup**, and then choose the related link.
2.	Select the **Invoice Rounding Setup** action.
3.	On the Invoice Rounding Setup page, define the rounding settings for all payment methods that should be set differently than the default from General ledger Setup.

> [!NOTE]
> The view is filtered to an empty currency code.

**Foreign currency setup**

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Payment Methods**, and then choose the related link.
2.	Select the **Invoice Rounding Settings** action.
3.	On the Invoice Rounding Settings page, define the rounding settings for foreign currencies in combination with the selected payment method, for which the settings should be different from the default on the Currency Card.

## VAT deduct reduction setting 
### VAT Posting Setup

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **VAT Posting Setup**, and then choose the related link.

For combinations of VAT account groups, where the reduction of the input VAT coefficient will be solved, it must be set (among other things):
- VAT Coeff. Posting Type
- VAT Prod. Posting Group Coefficient

In addition, new combinations of the same VAT business account group and VAT account of the goods group defined in the field "Coef.DPH account of the goods group" (see above) must be set with VAT calculation type = Full VAT 

The following must be set for these combinations (among other things):
- Non Deduction VAT Correction Account – used as a counter-account of the current VAT purchasing account when re-accounting for the reduction of the VAT deduction by the coefficient. 

>[!NOTE]
>The set combinations of VAT account groups with VAT calculation type = Full VAT do not enter the VAT statement.

![Nastavení účtování DHP](media/setup_vat.png)

### VAT Advance Coefficient

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **General Ledger Setup**, and then choose the related link.
2.	In the VAT Advance Coefficient field on the VAT tab, set the percentage value valid for the current accounting period.


## VAT registration in multiple countries setup

### More VAT registration numbers of customers

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Customers**, and then choose the related link.
2.	Select the Registration Country action.
3.	Enter the country code and VAT registration number.
4.	Next, add VAT Bus.Posting Group to be used in the event of a sale to a customer in that country.


### More VAT registration numbers of customers

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Vendors**, and then choose the related link.
2.	Select the Registration Country action.
3.	Enter the country code and VAT registration number.
4.	Next, add VAT Bus.Posting Group to be used in the event of a sale to a customer in that country.
 

### More VAT registrations 

The basic setting consists in the recording of VAT registration numbers in individual countries and setting how the system should change the VAT Bus. Posting Group in documents for the correct processing of VAT entries when concluding VAT and for the correct creation of documentation (most often for accounting offices in these countries). 

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Company Information**, and then choose the related link.
2.	Select the Registration Country action.
3.	On the Registration Country/Region page, enter the country code and VAT reg. number of the company registered in this country. For the created record, fill in the Currency Code (local) specifying the currency in which the VAT return is filed in the selected country.
4.	Close the Registration Country/Region page.
5.	Select the Registration Country/Region Routes action.
6.	On the Registration Country/Region Routes page, define how the system should replace the VAT Business Posting Group on the documents.
 
In the case of using a currency other than the local currency in the country of registration, it is necessary to maintain exchange rates between the currency of the document and the local currency of the country of registration.

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Currencies **, and then choose the related link.
2.	Select the Registration Country Exch. Rates action.
3.	Enter the date and exchange rate on the Reg. Country Curr. Exch. Rate page.
 

>[!NOTE]
> The system does not include functionality for importing Registration Country Exch. Rates. 

### OSS - EU regime

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **General Ledger Setup**, and then choose the related link.
2.	In the OSS - EU Registration field on the VAT tab, confirm that your company is registered for OSS mode.
3.	In the Currency code for OSS field on the VAT tab, select the currency code corresponding to the Euro currency.
4.	Select the VAT Settings for OSS action (Related -> VAT Posting).
5.	On the VAT Settings for OSS page, enter the VAT sales group for the combination of countries where the shipment starts and ends.
 

>[!NOTE]
> The OSS flag determines whether or not the specified country combination is subject to OSS. 

## Nastavení účtování přeplatků nákupních záloh

Popsaná automatizace při účtování finální faktury se zapíná v Nastavení účtování DPH pro vybrané kombinace účtoskupin. Pokud je toto chování vhodné pouze pro některé případy, je třeba pro ně míst vydefinované zvláštní DPH účtoskupiny (zboží). 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení účtování DPH** a poté vyberte související odkaz.

Na stránce Nastavení účtování DPH vyhledejte záznam pro který chcete zapnout a zvolte funkci Úpravy. 

Nastavte příznak v poli Určeno pro vrácení zálohy na záložce Zálohy. 

## Accounting purchase of purchase advances - setup

The described automation when posting the final invoice is activated in the VAT posting settings for selected combinations of account groups. If this behavior is only appropriate for some cases, it is necessary to have defined special VAT Product Posting Group for them.

1.	Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **VAT Posting Setup**, and then choose the related link.
2.	On the VAT Posting Setup page, find the record you want to turn on and select the Edit feature.
3.	Set the flag in the Intended for rollback field on the Backups tab.

**See also**

[Application extension set](ac-controling-basic.md)  
[Financial Pack](ac-finance-pack.md)
