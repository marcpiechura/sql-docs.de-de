---
title: Erstellen eines Entitätsadministrators (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 717be1e8-488e-4219-8d1e-ca9084b864cd
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3b9e781eb81096e364acd2040c075d7f170ca545
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="create-an-entity-administrator-master-data-services"></a>Erstellen eines Entitätsadministrators (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einen Entitätsadministrator, wenn eine Gruppe oder ein Benutzer über alle Berechtigungen für alle Objekte in mindestens einer Entität oder über die Berechtigung zum Genehmigen ausstehender Changesets verfügen soll.  
  
> [!TIP]  
>  Erstellen Sie zum Vereinfachen der Verwaltung eine Windows-Gruppe oder lokale Gruppe und konfigurieren Sie diese als Entitätsadministrator. Sie können anschließend der Gruppe Benutzer hinzufügen und diese daraus entfernen, ohne auf [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]zuzugreifen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
## <a name="to-create-an-entity-administrator"></a>So erstellen Sie einen Entitätsadministrator  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Wählen Sie die Zeile für den Benutzer oder die Gruppe aus, den bzw. die Sie bearbeiten möchten, und klicken Sie anschließend auf **Ausgewählten Benutzer bearbeiten**.  
  
3.  Klicken Sie auf die Registerkarte **Modelle** , wählen Sie optional ein Modell aus der Liste **Modelle** aus, und klicken Sie anschließend auf **Bearbeiten**.  
  
4.  Klicken Sie auf die Entität, der Sie Berechtigungen erteilen möchten, und klicken Sie anschließend im Menü auf **Admin** .  
  
5.  Führen Sie Schritt 4 für jede Entität aus, für die Sie die Gruppe bzw. den Benutzer als Administrator definieren möchten.  
  
6.  Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Zuweisen von Hierarchieelementberechtigungen &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
