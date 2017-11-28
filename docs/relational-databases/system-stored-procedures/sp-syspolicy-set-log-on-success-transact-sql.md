---
title: Sp_syspolicy_set_log_on_success (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_set_log_on_success_TSQL
- sp_syspolicy_set_log_on_success
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_set_log_on_success
ms.assetid: 6b33383b-5949-488a-a911-59299a270f46
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 95d79dfcd1e4942cb5604df98b8edc49eb4dc2da
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="spsyspolicysetlogonsuccess-transact-sql"></a>sp_syspolicy_set_log_on_success (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt an, ob erfolgreiche Richtlinienauswertungen im Richtlinienverlaufsprotokoll der richtlinienbasierten Verwaltung protokolliert werden.  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syspolicy_set_log_on_success [ @value = ] value  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@value=** ] *Wert*  
 Bestimmt, ob erfolgreiche Richtlinienauswertungen protokolliert werden. *Wert* ist **Sqlvariant**, und kann einen der folgenden Werte:  
  
-   0 oder 'false' = Erfolgreiche Richtlinienauswertungen werden nicht protokolliert.  
  
-   1 oder 'true' = Erfolgreiche Richtlinienauswertungen werden protokolliert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen sp_syspolicy_set_log_on_success im Kontext der Systemdatenbank msdb ausführen.  
  
 Wenn *Wert* festgelegt ist auf 0 oder auf "False", nur fehlerhafte richtlinienauswertungen protokolliert.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle PolicyAdministratorRole.  
  
> **WICHTIG!** Mögliche Erweiterung der Anmeldeinformationen: Benutzer mit der Rolle PolicyAdministratorRole können Servertrigger erstellen und die Ausführung von Richtlinien planen. Dies kann sich auf die Arbeitsweise der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz auswirken. Ein Benutzer mit der Rolle PolicyAdministratorRole kann beispielsweise eine Richtlinie erstellen, durch die das Erstellen der meisten Objekte in [!INCLUDE[ssDE](../../includes/ssde-md.md)] verhindert wird. Aufgrund dieser möglichen Erweiterung der Anmeldeinformationen, sollte die PolicyAdministratorRole-Rolle gewährt werden nur für Benutzer, die hinsichtlich der Kontrolle der Konfigurations der vertrauenswürdig sind die [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Protokollierung von erfolgreichen Richtlinienauswertungen aktiviert.  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_log_on_success @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Richtlinienbasierte Verwaltung gespeicherte Systemprozeduren &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [Sp_syspolicy_configure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  