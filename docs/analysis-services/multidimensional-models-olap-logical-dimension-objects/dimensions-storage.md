---
title: Dimension-Speicher | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b45ab57b151c2cdab5ae7aa133befd06893037bd
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="dimensions---storage"></a>Dimensionen - Speicher
  Dimensionen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützen zwei Speichermodi:  
  
-   Relationale OLAP (ROLAP)  
  
-   Mehrdimensionale OLAP (MOLAP)  
  
 Durch den Speichermodus werden der Speicherort und die Form der Daten einer Dimension bestimmt. MOLAP ist der Standardspeichermodus für Dimensionen. **Verwandte Themen:**[Partition Speichermodi und Verarbeitung](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Daten für eine Dimension, die MOLAP verwendet, werden in einer mehrdimensionalen Struktur in einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert. Diese mehrdimensionale Struktur wird erstellt und aufgefüllt, wenn die Dimension verarbeitet wird. MOLAP-Dimensionen ermöglichen eine bessere Abfrageleistung als ROLAP-Dimensionen.  
  
## <a name="rolap"></a>ROLAP  
 Die Daten für eine Dimension, die ROLAP verwendet, werden eigentlich in den Tabellen gespeichert, die zum Definieren der Dimension verwendet werden. Der ROLAP-Speichermodus kann verwendet werden, um große Dimensionen ohne Kopieren großer Datenmengen zu unterstützen, allerdings zu Lasten der Abfrageleistung. Da die Dimension direkt von den Tabellen in der Datenquellensicht abhängt, die zum Definieren der Dimension verwendet wurden, unterstützt der ROLAP-Speichermodus auch Echtzeit-OLAP.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension den ROLAP-Speichermodus verwendet und die Dimension in einen Cube eingeschlossen ist, der die MOLAP-Speicherung verwendet, muss auf jede Schemaänderung an der zugehörigen Quelltabelle die sofortige Verarbeitung des Cubes folgen. Erfolgt die Verarbeitung nicht, kann dies zu inkonsistenten Ergebnissen führen, wenn der Cube abgefragt wird. **Verwandtes Thema:**[Automatisieren von Analysis Services-Verwaltungsaufgaben mit SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Partition Speichermodi und Verarbeitung](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  