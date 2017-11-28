---
title: Sys.pdw_loader_run_stages (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d209fff76a89f84b67e351864b102ebf8ecbcd5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwloaderrunstages-transact-sql"></a>Sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu laufenden und abgeschlossenen Ladevorgänge in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Die Informationen, die über Systemneustarts weiterhin besteht.  
  
|||||  
|-|-|-|-|  
|Spaltenname|Datentyp|Description|Bereich|  
|run_id|**int**|Eindeutiger Bezeichner des ein Ladeprogramm ausführen.||  
|Stufe|**nvarchar(30)**|Die aktuelle Phase der Ausführung.|"CREATE_STAGING", "DMS_LOAD", "LOAD_INSERT", "LOAD_CLEANUP"|  
|request_id|**nvarchar(32)**|Die ID der Anforderung dieser Stufe ausgeführt.||  
|status|**nvarchar(16)**|Der Status dieser Phase.||  
|start_time|**datetime**|Zeitpunkt, an dem die Phase gestartet wurde.||  
|end_time|**datetime**|Zeitpunkt, zu dem die Phase beendet wurde, sofern vorhanden.|NULL, wenn nicht gestartet oder ausgeführt.|  
|total_elapsed_time|**int**|Gesamtzeit dieser Phase aufgewendet hat (oder aufgewendet hat bisher) ausgeführt wird.|Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl (24.8 Tage in Millisekunden) überschreitet, führt es Materialisierung Fehler aufgrund einer dazu, dass "Überlauf".<br /><br /> Der maximale Wert in Millisekunden entspricht 24.8 Tage.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  