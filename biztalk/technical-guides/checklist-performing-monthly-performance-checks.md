---
title: "Checklist: Performing Monthly Performance Checks | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa103777-af4d-480d-abc7-3c4718f493c1
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Performing Monthly Performance Checks
This topic lists best practices that you should follow on a monthly basis to avoid performance issues with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.  
  
|Steps|Reference|  
|-----------|---------------|  
|Determine the information you need to track during planning|You should decide during the planning stages which information you need to track, so that after you deploy the project you can set the tracking options and limit the amount of tracked data to give you only the information you need. **Note:**  For more information about best practices related to tracking, see [Planning for Tracking](../technical-guides/planning-for-tracking.md) in this guide and [Health and Activity Tracking](http://go.microsoft.com/fwlink/?LinkId=154187) (http://go.microsoft.com/fwlink/?LinkId=154187) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.|  
|Do not track all messages|We recommend that you not track all messages, because each time a message is touched, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes another copy. You can instead narrow the scope by tracking only a specific port. This helps to maximize the performance of your system and to keep the databases uncluttered.|  
|Do not track all events for orchestrations|Tracking all events for an orchestration might increase the size of dta_DebugTrace and dta_MessageInoutEvents tables. For instructions on how to disable tracking for an orchestration, see [To disable tracking for an orchestration](../technical-guides/how-to-disable-tracking.md#BKMK_DisableOrchTracking).|  
|Set tracking on send ports and receive ports instead of on a pipeline|If you set tracking options on pipelines, you will also set the tracking options globally for every port that uses the pipeline. This in turn may result in far more data being tracked than you intend, which will slow system performance. Instead, you can set tracking options on send ports and receive ports.|  
|Adjust throttling based on resource utilization|Throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured by default to provide good protection for the system. Monitor the performance counters for throttling states to see if throttling is taking place, then gauge for yourself if the resource on which throttling is based (for example, database size or memory usage) is under or overutilized, and then adjust the throttling thresholds up or down accordingly. For more information, see [Adjusting Throttling Thresholds: When and Why](http://go.microsoft.com/fwlink/?LinkId=154188) (http://go.microsoft.com/fwlink/?LinkId=154188).|  
|Use the PassThruTransmit pipeline if possible|If no document processing is required before sending a message to its destination, use the PassThruTransmit pipeline instead of the XML send pipeline.|  
|Take into account various factors when you size the BizTalk Tracking database|-   When sizing the BizTalk Tracking database, account for SQL Server factors, such as index size, by adding a contingency multiplier to your calculations.<br />-   When determining the size of messages in the BizTalk Tracking database, add the average size of the message context to the message size if it is significant compared to the message size.<br />-   To limit the size of messages in the BizTalk Tracking database, limit the number of properties that you promote.<br />-   If the orchestration debugger option is enabled, take into account that the status of each shape in the orchestration is saved in the BizTalk Tracking database.|  
|Apply hardware solutions to avoid disk contention|To avoid disk contention in the MessageBox database, do the following:<br /><br /> -   Use high-speed disks<br />-   Deploy the databases on a high-speed SAN<br />-   Separate the MessageBox database onto a dedicated server that is separate from the tracking databases<br />-   Scale up the CPUs and add more CPUs to the dedicated MessageBox database server<br />-   Move the PageFile and/or MSDTC log to a separate drive<br /><br /> For more information about avoiding database contention, see [How to Avoid Disk Contention](http://go.microsoft.com/fwlink/?LinkId=158809) (http://go.microsoft.com/fwlink/?LinkId=158809).|  
  
## See Also  
 [Routine Performance Checklists](../technical-guides/routine-performance-checklists.md)   
 [Checklist: Performing Weekly Performance Checks](../technical-guides/checklist-performing-weekly-performance-checks.md)