---
title: Sp_helpmergearticleconflicts (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords: sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7a1d10d6d2ba731ceaaaba51b8f786b262a2e28
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Artikel in der Veröffentlichung zurück, die Konflikte aufweisen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Mergeabonnement-Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"***Veröffentlichung***"**  
 Ist der Name der Mergeveröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert  **%** , womit alle Artikel in der Datenbank, die Konflikte aufweisen.  
  
 [  **@publisher=**] **"***Publisher***"**  
 Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@publisher_db=**] **"***Publisher_db***"**  
 Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Artikel**|**sysname**|Der Name des Artikels.|  
|**Der Standardwert**|**sysname**|Besitzer des Quellobjekts.|  
|**source_object**|**nvarchar(386)**|Name des Quellobjekts.|  
|**conflict_table**|**vom Datentyp nvarchar(258)**|Name der Tabelle, in der die Einfüge- oder Updatekonflikte gespeichert werden.|  
|**guidcolname**|**sysname**|Name der ROWGUIDCOL des Quellobjekts.|  
|**centralized_conflicts**|**int**|Gibt an, ob Konfliktdatensätze auf dem angegebenen Verleger gespeichert werden.|  
  
 Wenn der Artikel nur Löschkonflikte und keine hat **Conflict_table** Zeilen, die den Namen der **Conflict_table** im Resultset den Wert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpmergearticleconflicts** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle "" und die **Db_owner** feste Datenbankrolle können ausführen **Sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  