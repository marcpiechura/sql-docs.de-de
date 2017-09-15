---
title: "Ausschließen einer Geschäftsregel (Master Data Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 264f58554df70d5531cecdaea9bbc94606086e9a
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="exclude-a-business-rule-master-data-services"></a>Ausschließen einer Geschäftsregel (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie eine Geschäftsregel ausschließen, die nicht zur Datenüberprüfung verwendet, aber auch nicht dauerhaft gelöscht werden soll.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-exclude-a-business-rule"></a>So schließen Sie eine Geschäftsregel aus  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Geschäftsregeln** in der Dropdownliste **Modell** ein Modell aus.  
  
4.  Wählen Sie in der Dropdownliste **Entität** eine Entität aus.  
  
5.  Wählen Sie in der Dropdownliste **Member Types** (Elementtypen) einen Elementtyp aus.  
  
6.  Klicken Sie im Raster auf die Zeile der Geschäftsregel, die Sie ausschließen möchten, und klicken Sie auf **Bearbeiten**.  
  
7.  Aktivieren Sie das Kontrollkästchen **Ausgeschlossen** .  
  
8.  Klicken Sie auf **Speichern**.  
  
9. Klicken Sie auf **Alle veröffentlichen**.  
  
10. Klicken Sie im Bestätigungsdialogfeld auf **OK**. Der Wert in der Spalte **Geschäftsregelstatus** lautet **Ausgeschlossen** , und die Spalte **Ausgeschlossen** ist auf **Ja**festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen einer Geschäftsregel &#40; Master Data Services &#41;](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [Erstellen Sie und veröffentlichen Sie einer Geschäftsregel &#40; Master Data Services &#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Geschäftsregeln &#40; Master Data Services &#41;](../master-data-services/business-rules-master-data-services.md)  
  
  