---
title: COUNT_BIG (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COUNT_BIG_TSQL
- COUNT_BIG
dev_langs:
- TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT_BIG function
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT_BIG function
ms.assetid: f2e3601f-487e-4917-bb01-47b1047908cd
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a76766659a771d1ab88d0fa33a9ef62f986a8a06
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="countbig--sql"></a>COUNT_BIG (-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt die Anzahl der in einer Gruppe gefundenen Elemente zurück. `COUNT_BIG` arbeitet wie die [COUNT](../../t-sql/functions/count-transact-sql.md)-Funktion. Diese Funktionen unterscheiden sich nur in den Datentypen ihrer Rückgabewerte. `COUNT_BIG` gibt immer einen Wert vom Datentyp **bigint** zurück. `COUNT` gibt immer einen Wert vom Datentyp **int** zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT_BIG ( { [ ALL | DISTINCT ] expression } | * )  
   [ OVER ( [ partition_by_clause ] [ order_by_clause ] ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Aggregation Function Syntax  
COUNT_BIG ( { [ [ ALL | DISTINCT ] expression ] | * } )  
  
-- Analytic Function Syntax  
COUNT_BIG ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Argumente  
ALL  
Wendet die Aggregatfunktion auf alle Werte an. ALL dient als Standardeinstellung.
  
DISTINCT  
Gibt an, dass `COUNT_BIG` die Anzahl der eindeutigen Werte zurückgibt, die nicht NULL sind.
  
*expression*  
Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) beliebigen Typs. Beachten Sie, dass `COUNT_BIG` keine Aggregatfunktionen oder Unterabfragen in einem Ausdruck unterstützt.
  
*\**  
Gibt an, dass `COUNT_BIG` alle Zeilen zählen soll, um die Gesamtzahl der zurückzugebenden Tabellenzeilen zu bestimmen. `COUNT_BIG(*)` nimmt keine Parameter an und unterstützt die Verwendung von DISTINCT nicht. `COUNT_BIG(*)` erfordert keinen *expression*-Parameter, da definitionsgemäß keine Informationen zu einer bestimmten Spalte verwendet werden. `COUNT_BIG(*)` gibt die Anzahl der Zeilen in einer angegebenen Tabelle zurück. Duplikate werden beibehalten. Dabei werden alle Zeilen einzeln gezählt. Dies schließt Zeilen mit NULL-Werten ein.
  
OVER **(** [ *partition_by_clause* ] [ *order_by_clause* ] **)**  
Das Argument *partition_by_clause* unterteilt das von der `FROM`-Klausel erzeugte Resultset in Partitionen, auf die die `COUNT_BIG`-Funktion angewendet wird. Wird dies nicht angegeben, verarbeitet die Funktion alle Zeilen des Abfrageresultsets als einzelne Gruppe. *order_by_clause* bestimmt die logische Reihenfolge, in der der Vorgang ausgeführt wird. Weitere Informationen finden Sie unter [OVER-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Rückgabetypen
**bigint**
  
## <a name="remarks"></a>Remarks  
COUNT_BIG(\*) gibt die Anzahl von Elementen in einer Gruppe zurück. Dies schließt NULL-Werte und Duplikate ein.
  
COUNT_BIG (ALL *expression*) wertet *expression* für jede Zeile in einer Gruppe aus und gibt die Anzahl der Werte zurück, die nicht NULL sind.
  
COUNT_BIG (DISTINCT *expression*) wertet *expression* für jede Zeile in einer Gruppe aus und gibt die Anzahl der eindeutigen Werte zurück, die nicht NULL sind.
  
COUNT_BIG ist eine deterministische Funktion, wenn sie ***ohne*** die OVER- und ORDER BY-Klauseln angegeben wird. Sie ist nicht deterministisch, wenn sie ***mit*** den OVER- und ORDER BY-Klauseln verwendet wird. Weitere Informationen finden Sie unter [Deterministische und nicht deterministische Funktionen](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Beispiele  
Beispiele finden Sie unter [COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md).
  
## <a name="see-also"></a>Siehe auch
[Aggregate Functions &#40;Transact-SQL&#41; (Aggregatfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md)  
[int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
[OVER Clause &#40;Transact-SQL&#41; (OVER-Klausel &#40;Transact-SQL&#41;)](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
