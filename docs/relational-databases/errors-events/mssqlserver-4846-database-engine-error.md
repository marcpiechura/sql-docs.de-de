---
title: MSSQLSERVER_4846 | Microsoft-Dokumentation
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0b9152072fde4c139602eecef4a182e3e2cd1300
ms.contentlocale: de-de
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver4846"></a>MSSQLSERVER_4846
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|4846|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|BULKPROV_MEMORY|  
|Meldungstext|Der Massendatenanbieter konnte keinen Arbeitsspeicher belegen.|  
  
## <a name="explanation"></a>Erklärung  
Die Speicherbelegung hat einen Fehler erzeugt.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie diese allgemeinen Schritte aus, um Speicherfehler zu beheben:  
  
1.  Überprüfen Sie, ob andere Anwendungen oder Dienste Arbeitsspeicher auf dem Server beanspruchen. Rekonfigurieren Sie weniger kritische Anwendungen oder Dienste, damit sie weniger Speicher beanspruchen.  
  
2.  Sammeln Sie Leistungsindikatoren für **SQL Server: Puffer-Manager** und **SQL Server: Speicher-Manager**.  
  
3.  Überprüfen Sie die folgenden SQL Server-Speicherkonfigurationsparameter:  
  
    -   **Max. Serverarbeitspeicher**  
  
    -   **Min. Serverarbeitsspeicher**  
  
    -   **Min. Arbeitsspeicher pro Abfrage**  
  
    Achten Sie auf ungewöhnlichen Einstellungen. Berichtigen Sie sie bei Bedarf. Konto für Arbeitsspeicheranforderungen für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Die Standardeinstellungen werden unter "Festlegen von Serverkonfigurationsoptionen" in der SQL Server-Onlinedokumentation aufgeführt.  
  
4.  Verfolgen Sie die Ausgabe von DBCC MEMORYSTATUS und deren Veränderungen beim Anzeigen der Fehlermeldungen.  
  
5.  Überprüfen Sie die Arbeitsauslastung (z. B. Anzahl gleichzeitiger Sitzungen, derzeit ausgeführte Abfragen).  
  
Durch die folgenden Aktionen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mehr Arbeitsspeicher zur Verfügung gestellt werden:  
  
-   Wenn Anwendungen außer SQL Server Ressourcen verbrauchen, sollten Sie diese Anwendungen beenden oder auf einem separaten Server ausführen. Dadurch fällt der Mangel an externem Arbeitsspeicher weg.  
  
-   Wenn Sie **Max. Serverarbeitsspeicher** konfiguriert haben, erhöhen Sie den betreffenden Wert.  
  
Führen Sie die folgenden DBCC-Befehle aus, um mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speichercaches freizugeben.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Wenn das Problem weiterhin besteht, müssen Sie weitere Untersuchungen ausführen und möglicherweise die Arbeitsauslastung reduzieren.  
  
