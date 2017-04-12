---
title: "L&#246;schen von Benutzern oder Gruppen (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Löschen von Gruppen [Master Data Services]"
  - "Gruppen [Master Data Services], löschen"
  - "Benutzer [Master Data Services], löschen"
  - "Löschen von Benutzern [Master Data Services]"
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# L&#246;schen von Benutzern oder Gruppen (Master Data Services)
  Löschen Sie Benutzer oder Gruppen, wenn Sie nicht mehr möchten, dass sie auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zugreifen.  
  
 Beachten Sie das folgende Verhalten, wenn Sie Benutzer und Gruppen löschen:  
  
-   Wenn Sie einen Benutzer löschen, der Mitglied einer Gruppe ist, die Zugriff auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]hat, kann der Benutzer weiter auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] zugreifen, bis Sie den Benutzer aus Active Directory oder der lokalen Gruppe entfernen.  
  
-   Wenn Sie eine Gruppe löschen, werden alle Benutzer aus der Gruppe mit Zugriff auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] in der Liste **Benutzer** angezeigt, bis Sie sie löschen.  
  
-   Änderungen an der Sicherheit werden 20 Minuten lang nicht an MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] weitergegeben.  
  
## Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
### So löschen Sie Benutzer oder Gruppen  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Um einen Benutzer zu löschen, bleiben Sie auf der Seite **Benutzer** . Um eine Gruppe zu löschen, klicken Sie auf der Menüleiste auf **Gruppen verwalten**.  
  
3.  Wählen Sie im Raster die Zeile für den Benutzer oder die Gruppe aus, die Sie löschen möchten.  
  
4.  Klicken Sie auf **Ausgewählten Benutzer löschen** oder **Ausgewählte Gruppe löschen**.  
  
5.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## Siehe auch  
 [Sicherheit &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  