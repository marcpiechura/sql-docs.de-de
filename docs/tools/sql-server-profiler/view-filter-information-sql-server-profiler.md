---
title: Anzeigen von Filterinformationen (SQL Server Profiler) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 693dc730de16e14b4e6e0fc9626aa469eb66ed9b
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="view-filter-information-sql-server-profiler"></a>Anzeigen von Filterinformationen (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Filter von Datenspalten für Ereignisklassen mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]angezeigt werden können.  
  
### <a name="to-view-filter-information"></a>So zeigen Sie Filterinformationen an  
  
1.  Öffnen Sie eine Ablaufverfolgungsdatei, eine Ablaufverfolgungstabelle oder ein SQL-Skript, und klicken Sie im Menü **Datei** auf **Eigenschaften**. Wenn Sie eine Ablaufverfolgungsvorlage bearbeiten oder eine neue Ablaufverfolgung erstellen, können Sie diesen Schritt auslassen.  
  
2.  Klicken Sie auf der Registerkarte **Ereignisauswahl** mit der rechten Maustaste auf den Namen der Datenspalte für den anzuzeigenden Filter, und klicken Sie dann auf **Spaltenfilter bearbeiten**.  
  
3.  Erweitern Sie im Dialogfeld **Filter bearbeiten** die Vergleichsoperatoren für den Filter, um den zugewiesenen Wert für das angegebene Kriterium anzuzeigen. Wiederholen Sie Schritt 2 und 3 für alle Spalten, für die Sie Filterinformationen anzeigen möchten.  
  
> [!NOTE]  
>  Vergleichsoperatoren mit zugewiesenen Werten sind fett formatiert.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  