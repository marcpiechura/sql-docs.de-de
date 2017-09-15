---
title: Erstellen ein Modells (Master Data Services) | Microsoft Docs
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
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
caps.latest.revision: 13
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1791558cec3999d3a038bc3b651cd3c8edbd307d
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-model-master-data-services"></a>Erstellen eines Modells (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein Modell, das Modellobjekte enthalten soll.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model"></a>So erstellen Sie ein Modul  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Modelle**.  
  
3.  Klicken Sie auf der Seite **Modelle verwalten** auf **Hinzufügen**. Auf der rechten Seite wird ein Panel angezeigt.  
  
4.  Geben Sie im Feld **Name** den Namen des Modells ein.  
  
5.  (Optional) Geben Sie im Feld **Beschreibung** die Modellbeschreibung ein.  
  
6.  Wählen Sie im Feld **Tage für Protokollbeibehaltung** eine der Optionen für die Aufbewahrung von Protokolldaten aus. Der Standardwert ist **Systemeinstellung**, was bedeutet, dass der Wert der Systemeinstellungen in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] übernommen wird. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
     Wählen Sie **NEIN** aus, um die Systemeinstellung zu überschreiben und Transaktionsprotokolldaten nicht zu entfernen. Wählen Sie **JA** aus, und legen Sie das Feld **Tage** auf „0“ fest, um die Protokolldaten aller vorherigen Tage zu entfernen und nur die Protokolldaten des aktuellen Tags aufzubewahren. Wählen Sie **JA** aus, und legen Sie das Feld **Tage** auf eine bestimmte Anzahl von Tagen fest, um die Protokolldaten für die angegebene Anzahl von Tagen aufzubewahren.  
  
7.  Optional können Sie **Entität mit demselben Namen wie das Modell erstellen** auswählen, um eine Entität mit dem gleichen Namen wie das Modell zu erstellen.  
  
8.  Klicken Sie auf **Modell speichern**.  
  
 Für jedes erstellte Modell wird dem Raster eine Zeile mit acht Spalten hinzugefügt. Die acht Spalten lauten:  
  
-   **Status**: Der Status des Modells. Beim Klicken auf die **speichern Modell** Schaltfläche, die ![aktualisieren](../master-data-services/media/mds-model-status-updating.png "aktualisieren") Bild angezeigt, was bedeutet, dass das Modell aktualisiert wird. Treten Fehler beim Erstellen oder Bearbeiten eines Modells der ![Fehler](../master-data-services/media/mds-model-status-error.png "Fehler") Bild angezeigt. Andernfalls lautet der Status „OK“, und das Bild ![OK](../master-data-services/media/mds-model-status-ok.png "OK") angezeigt.  
  
-   **Name**: Der Name des Modells.  
  
-   **Beschreibung**: Die Beschreibung des Modells.  
  
-   **Tage für Protokollbeibehaltung**: Die Beibehaltungsdauer des Protokolls für das Modell in Tagen.  
  
-   **Erstellt von**: Der Benutzername des Benutzers, der das Modell erstellt hat.  
  
-   **Erstellungsdatum und -uhrzeit**: Das Datum und die Uhrzeit der Erstellung des Modells.  
  
-   **Aktualisiert von**: Der Benutzername des Benutzers, der das Modell zuletzt aktualisiert hat.  
  
-   **Aktualisierungsdatum und -uhrzeit**: Das Datum und die Uhrzeit der letzten Aktualisierung des Modells.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Modelle &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Entitäten &#40; Master Data Services &#41;](../master-data-services/entities-master-data-services.md)   
 [Löschen eines Modells &#40; Master Data Services &#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Bearbeiten Sie Modell &#40; Master Data Services &#41;](../master-data-services/edit-model-master-data-services.md)   
 [Transaktionen &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)  
  
  