---
title: "Modellieren von Berechtigungen für Modellobjekte (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ee6ede91067d2b358a403458e07af37b2f895ac3
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="model-object-permissions-master-data-services"></a>Berechtigungen für Modellobjekte (Master Data Services)
  Berechtigungen für Modellobjekte sind erforderlich. Sie bestimmen die Attribute, auf die ein Benutzer im Funktionsbereich **Explorer** der Benutzeroberfläche zugreifen kann.  
  
 Wenn Sie z.B. der Entität „Product“ die Benutzerberechtigung **Aktualisieren** zuweisen, kann der Benutzer alle Attribute der Entität „Product“ aktualisieren. Wenn Sie einem einzelnen Attribut die Berechtigung **Aktualisieren** zuweisen, kann der Benutzer nur dieses Attribut aktualisieren.  
  
 Um die jedem Attributwert zugewiesene Sicherheit zu ermitteln, werden Modellobjektberechtigungen mit Hierarchieelementberechtigungen kombiniert, die die Elemente bestimmen, auf die ein Benutzer zugreifen kann.  
  
 Um einem Benutzer Zugriff auf einen anderen Funktionsbereich als **Explorer** zu gewähren, muss der Benutzer ein Modelladministrator sein, der Objektmodellen auch Administratorberechtigungen zuweisen kann. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
 Berechtigungen für Modellobjekte werden in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Benutzeroberfläche im Funktionsbereich **Benutzer- und Gruppenberechtigungen** auf der Registerkarte **Modelle** zugewiesen. Auf dieser Registerkarte wird das Modell als Baumstruktur dargestellt. Wenn Sie einem Objekt in der Struktur eine Berechtigung zuweisen, wird diese Berechtigung von allen untergeordneten Objekten geerbt. Sie können die Vererbung überschreiben, indem Sie einzelnen Objekten eine Berechtigung zuweisen.  
  
 Sie können eine Kombination aus lesen, erstellen, aktualisieren und löschen zuweisen oder Verweigern von Berechtigungen für Modellobjekte. Wenn Sie auf der Registerkarte **Modelle** keine Berechtigungen zuweisen, kann der Benutzer keine Modelle oder Daten in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]anzeigen.  
  
## <a name="best-practice"></a>Bewährte Methoden  
 Im Allgemeinen sollten Sie dem Modellobjekt die Berechtigung **ALLE** zuweisen und anschließend untergeordneten Objekten die Berechtigung explizit zuweisen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogbeitrag [Sicherheitsverbesserungen](http://go.microsoft.com/fwlink/p/?LinkId=615376), auf msdn.com.  
  
## <a name="see-also"></a>Siehe auch  
 [Weisen Sie Modellobjektberechtigungen &#40; Master Data Services &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modellberechtigungen &#40; Master Data Services &#41;](../master-data-services/model-permissions-master-data-services.md)   
 [Berechtigungen für Funktionsbereiche &#40; Master Data Services &#41;](../master-data-services/functional-area-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40; Master Data Services &#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Wie Berechtigungen &#40; Master Data Services &#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  