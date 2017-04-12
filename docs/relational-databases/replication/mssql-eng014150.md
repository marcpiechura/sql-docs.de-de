---
title: "MSSQL_ENG014150 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014150 (Fehler)"
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014150
    
## Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14150|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Replikations-%1!: %2! (Agent) erfolgreich. %3!|  
  
## Erklärung  
 Mit dieser Meldung wird angegeben, dass ein Replikations-Agent erfolgreich zu Ende ausgeführt wurde. Für die Replikation werden die folgenden Agents verwendet:  
  
-   Der Momentaufnahme-Agent. Dieser Agent wird von allen Veröffentlichungen verwendet.  
  
-   Der Protokolllese-Agent. Dieser Agent wird von allen Transaktionsveröffentlichungen verwendet.  
  
-   Der Warteschlangenlese-Agent. Dieser Agent wird von Transaktionsveröffentlichungen verwendet, die für Abonnements mit verzögertem Update über eine Warteschlange aktiviert sind.  
  
-   Der Verteilungs-Agent. Mit diesem Agent werden Abonnements für Transaktions- und Momentaufnahmeveröffentlichungen synchronisiert.  
  
-   Der Merge-Agent. Mit diesem Agent werden Abonnements für Mergeveröffentlichungen synchronisiert.  
  
-   Aufträge zur Replikationswartung.  
  
## Benutzeraktion  
 Der Protokolllese-Agent, der Warteschlangenlese-Agent und der Verteilungs-Agent werden normalerweise kontinuierlich ausgeführt. Die anderen Agents werden hingegen bei Bedarf oder nach einem Zeitplan ausgeführt. Wenn Sie nicht erwarten, dass ein Agent zu Ende ausgeführt wurde, überprüfen Sie den Status des Agents. Weitere Informationen finden Sie unter [Monitor Replication Agents](../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
## Siehe auch  
 [Replikations-Agent-Verwaltung](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Fehler und Ereignisreferenz & #40; Replikation & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Replikationsverteilungs-Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replikationsprotokolllese-Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replikationsmerge-Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Warteschlangenlese-Agent der Microsoft SQL Server-Replikation](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replikationsmomentaufnahme-Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  