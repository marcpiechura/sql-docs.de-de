---
title: Speichern eines Berichts in einer SharePoint-Bibliothek (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-builder
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fc45abb3fef982e3d9b4a52cf39e6bff8ee1e5d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a>Speichern eines Berichts in einer SharePoint-Bibliothek (Berichts-Generator)
  Wenn Sie einen Bericht auf einem für die SharePoint-Integration konfigurierten Berichtsserver speichern möchten, müssen Sie den SharePoint-Server suchen und eine Verbindung mit dem Berichtsserver herstellen. In der Berichtsdefinition müssen alle Referenzen auf Elemente, die im Zusammenhang mit dem Bericht stehen, Werte verwenden, die für einen SharePoint-Berichtsserver spezifisch sind. Verwandte Elemente schließen Unterberichte, Drillthroughberichte und Ressourcen ein, wie webbasierte Bilder. Weitere Informationen finden Sie unter [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Sie müssen für die SharePoint-Website über die Berechtigung als **Mitglied** oder **Besitzer** verfügen, um die Eigenschaften für das Projekt festzulegen.  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a>So speichern Sie eine Bericht auf einer SharePoint-Website  
  
1.  Klicken Sie über die Schaltfläche Berichts-Generator auf **Speichern**. Das Dialogfeld **Speichern unter***\<Berichtselement>* wird geöffnet.  
  
    > [!NOTE]  
    >  Wenn Sie einen Bericht erneut speichern, wird er automatisch am vorherigen Speicherort erneut gespeichert. Verwenden Sie die Option **Speichern unter** , um den Speicherort zu ändern.  
  
2.  Klicken Sie optional auf **Letzte Sites und Server** , um eine Liste der zuletzt verwendeten Berichtsserver und SharePoint-Websites anzuzeigen.  
  
3.  Wechseln Sie zur SharePoint-Website, und klicken Sie dann auf **Speichern**.  
  
    > [!NOTE]  
    >  Wenn Sie einen geänderten Bericht mehr als 10 Stunden lang nicht speichern, wird er vom Server getrennt, ohne gespeichert zu werden. Klicken Sie in einem solchen Fall in der rechten unteren Statusleiste auf **Trennen**und anschließend auf **Verbinden**. Der letzte Server befindet sich in der Liste der verfügbaren Server. Wählen Sie ihn aus, damit der Bericht erneut eine Verbindung herstellt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Suchen, Anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
