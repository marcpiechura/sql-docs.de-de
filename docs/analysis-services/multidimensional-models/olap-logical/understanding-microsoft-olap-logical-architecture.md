---
title: Logische Architektur (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b6b33ffbf59cf05bc5455d3daac437e9e79407c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Grundlegendes zur Microsoft OLAP-logische Architektur
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet sowohl Server-als auch Clientkomponenten zum Bereitstellen von online analytical Processing (OLAP) und Datamining-Funktionalität für Business Intelligence-Anwendungen:  
  
-   Die Serverkomponente von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird als Microsoft Windows-Dienst implementiert. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt mehrere Instanzen auf demselben Computer, wobei jede Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] als eine separate Instanz des Windows-Diensts implementiert.  
  
-   Clients kommunizieren mit [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mithilfe des öffentlichen Standards für XMLA (XML for Analysis). Hierbei handelt es sich um ein SOAP-basiertes Protokoll für die Ausgabe von Befehlen und den Empfang von Antworten in Form eines Webdiensts. Clientobjektmodelle werden ebenfalls über XMLA bereitgestellt. Auf diese Modelle kann sowohl ein verwalteter Anbieter (ADOMD.NET) als auch ein eigener OLE DB-Anbieter zugreifen.  
  
-   Abfragebefehle können mithilfe der folgenden Abfragesprachen ausgegeben werden: SQL; MDX (Multidimensional Expressions), eine Abfragesprache nach Industriestandard für Analysen; oder DMX (Data Mining Extensions), eine am Data Mining orientierte Abfragesprache nach Industriestandard. ASSL (Analysis Services Scripting Language) kann außerdem zum Verwalten von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbankobjekten verwendet werden.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt darüber hinaus ein lokales Cubemodul, mit dessen Hilfe Anwendungen auf nicht verbundenen Clients lokal gespeicherte mehrdimensionale Daten suchen können. Weitere Informationen finden Sie unter [Anforderungen an die Clientarchitektur für Analysis Services-Entwicklung](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 **Übersicht über logische Architektur**  
 [Übersicht über logische Architektur & #40; Analysis Services – mehrdimensionale Daten & #41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Serverobjekte**  
 [Serverobjekte & #40; Analysis Services – mehrdimensionale Daten & #41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **Datenbankobjekte**  
 [Datenbankobjekte & #40; Analysis Services – mehrdimensionale Daten & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Dimensionsobjekte**  
 [Dimensionsobjekte & #40; Analysis Services – mehrdimensionale Daten & #41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Cubeobjekte**  
 [Cubeobjekte & #40; Analysis Services – mehrdimensionale Daten & #41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sicherheit für den Benutzerzugriff**  
 [Sicherheitsarchitektur für den Benutzerzugriff](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zur Microsoft OLAP-Architektur](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Physische Architektur & #40; Analysis Services – mehrdimensionale Daten & #41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
