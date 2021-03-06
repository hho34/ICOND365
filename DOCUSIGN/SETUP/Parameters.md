---
# required metadata

title: [Docusign]
description: [Setup Parameters]
author: [ndavidson2]
manager: Kym Parker
ms.date: 12/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Application User]
# ms.devlang: 
ms.reviewer: [ndavidson2]
ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Parameters

The Docusign parameters form is used to set up the connection between your Dynamics 365 environment and your Docusign account.  Within this form, you will set up the details regarding the administrator of the Docusign account, along with a connection key that will be utilized when sending data through to Docusign.
 You can reach the parameters form by navigating to **Organization administration** > **Setup** > **Docusign** > **Docusign Parameters**


| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| **Web services address**          | Docusign will provide the web address utilized to initiate the connection to your Docusign account. Two variants of this field value will be used; one for a development or non-production instance and the second for production. <br> <br>An example of this would be: *https://demo.docusign.net/restapi *  |
| **Integrator key**                | An integrator key is a unique identified for each Docusign account that is used for integration into another third-party system. It is used for all API calls to Docusign.  This field value is provided by Docusign in their Administration area.     |
| **User name**                     | Enter the Docusign Administrator username.  This user will need to have administration rights on the connected Docusign account.     | 
| **Password**                      | Enter the passoword associated with the Docusign administrator account.     | 
| **Log exception**                 | Select *Yes* to capture the Docusign error messages when they occur.  The messages will appear on the **Exeptions** page within the Docusign integration. <br> <br> The errors will allow for investiation and resolution by an administrator.      | 

When working within the parameters form, the web services UI will be varied both across environments and across regions.  The test environments will have a working services connection by connecting to the following:  https://demo.docusign.net/restapi .  This is regardless of the region of the business.  

When moving to a production environment, you must update your integration to use the right base URL for API calls instead of https://demo.docusign.net/restapi . The base URL will vary, depending on the DocuSign account being used.  Each registered DocuSign user for your application can access one or more accounts. Each account has an associated base URL. Currently, the production base URLs include: www.docusign.net, na2.docusign.net, eu.docusign.net, etc. Additional base URLs are added regularly.  


## Updates FastTab 

The updates FastTab provides the details regarding the frequency of updates between the two systems.

| **Field**                         | **Description**                      | 
| :-------------------------------- |:-------------------------------------| 
| **Status update time overlap**          | The update **Update document status** periodic task must be set up to run, as a minimum, every 15 minutes. <br> <br> When this batch process runs, it will send Docusign a time value and request all document status updates after that time, and up to the time the batch process is run.  Dynamics then stores the time the batch process completes.   |


*Note on Updates:*  As an example of the batch process for Docusign, assume the batch process runs at 9:00 a.m. and sent a time of 8:45 a.m.  All document status updates between 8:45 and 9:00 would be requested.  Dynamics will store a value of 9:00 a.m., so that the next time the batch process runs it would request all document status updates from 9:00 a.m. 

There will be instances where the process my take longer to finalize.  When this occurs, the finalization time will be recorded and will be used as the initialization time at the next batch process run.  This is why the field has been provided.  
