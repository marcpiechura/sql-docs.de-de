---
title: dm_db_fts_index_physical_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 952f07e7112b316e9109e0761deecf99f694306a
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmdbftsindexphysicalstats-transact-sql"></a>sys.dm_db_fts_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jeden Volltextindex oder semantischen Index in jeder Tabelle mit einem zugeordneten Volltextindex oder semantischen Index zurück.  
  
||||  
|-|-|-|  
|**Spaltenname**|**Typ**|**Beschreibung**|  
|**object_id**|int|Objekt-ID der Tabelle, die den Index enthält.|  
|**fulltext_index_page_count**|**bigint**|Logische Größe der Extraktion in Anzahl von Indexseiten.|  
|**keyphrase_index_page_count**|**bigint**|Logische Größe der Extraktion in Anzahl von Indexseiten.|  
|**similarity_index_page_count**|**bigint**|Logische Größe der Extraktion in Anzahl von Indexseiten.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [verwalten und Überwachen der semantischen Suche](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Führen Sie eine Abfrage der folgenden dynamischen Verwaltungssichten durch, um Informationen über den Status der semantischen Indizierung zu erhalten:  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie eine Abfrage der logischen Größe von jedem Volltextindex oder semantischen Index in allen Tabellen mit einem zugeordneten Volltextindex oder semantischen Index durchgeführt wird:  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten und Überwachen der semantischen Suche](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
