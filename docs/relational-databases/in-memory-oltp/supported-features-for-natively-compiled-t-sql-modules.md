---
title: "Unterst&#252;tzte Funktionen f&#252;r nativ kompilierte T-SQL-Module | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 44
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 44
---
# Unterst&#252;tzte Funktionen f&#252;r nativ kompilierte T-SQL-Module
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


  Dieses Thema listet die T-SQL-Oberflächenbereiche und unterstützten Funktionen im Hauptteil nativ kompilierter T-SQL-Module auf, wie gespeicherte Prozeduren ([CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)), benutzerdefinierte Skalarfunktionen, Inline-Tabellenwertfunktionen und Trigger.  

 Unterstützte Funktionen in der Definition der nativen Module finden Sie unter [Unterstützte Konstrukte für systemintern kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md).  

-   [Abfrageoberfläche in nativen Modulen](#qsancsp)  

-   [Datenänderung](#dml)  

-   [Sprachkonstrukte zur Ablaufsteuerung](#cof)  

-   [Unterstützte Operatoren](#so)  

-   [Integrierte Funktionen in nativ kompilierten Modulen](#bfncsp)  

-   [Überwachen](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#auditing)  

-   [Tabellen- und Abfragehinweise](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#tqh)  

-   [Einschränkungen bei der Sortierung](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#los)  

 Vollständige Informationen zu nicht unterstützten Konstrukten sowie Informationen zu Umgehungslösungen zu einigen der nicht unterstützten Funktionen in nativ kompilierten Modulen finden Sie unter [Migration Issues for Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)(Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren). Weitere Informationen zu nicht unterstützten Funktionen finden Sie unter [Von In-Memory-OLTP nicht unterstützte Transact-SQL-Konstrukte](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  

##  <a name="a-nameqsancspa-query-surface-area-in-native-modules"></a><a name="qsancsp"></a> Abfrageoberfläche in nativen Modulen  

Die folgenden Abfragekonstrukte werden unterstützt:  

SELECT-Klausel:  

-   Aliase für Spalten und Namen (entweder mithilfe von AS oder = Syntax).  

-   Skalare Unterabfragen  

-   TOP*  

-   SELECT DISTINCT  

              DISTINCT aggregates are not supported.  

-   UNION und UNION ALL

-   Variablenzuweisungen  

FROM-Klausel:  

-   FROM \<speicheroptimierte Tabelle oder Tabellenvariable>  

-   FROM \<nativ kompilierte Inline-TVF>  

-   LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN und INNER JOIN.  

-   Unterabfragen `[AS] table_alias`. Weitere Informationen finden Sie unter [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  

WHERE-Klausel:  

-   Filterprädikat IS [NOT] NULL  

-   AND, OR, NOT, IN, EXISTS, BETWEEN  


[GROUP BY](../Topic/GROUP%20BY%20%28Transact-SQL%29.md) -Klausel:

- Aggregatfunktionen AVG, COUNT, COUNT_BIG, MIN, MAX, und SUM.  

- MIN und MAX werden für die Typen nvarchar, char, varchar, varchar, vabinary und binary nicht unterstützt.  

[ORDER BY](../Topic/ORDER%20BY%20Clause%20%28Transact-SQL%29.md) -Klausel:


- Es gibt keine Unterstützung für **DISTINCT** in der **ORDER BY**-Klausel.


- Wird mit [GROUP BY &#40;Transact-SQL&#41;](../Topic/GROUP%20BY%20\(Transact-SQL\).md) unterstützt, wenn ein Ausdruck in der ORDER BY-Liste wörtlich in der GROUP BY-Liste angezeigt wird.
  - Beispielsweise wird GROUP BY a + b ORDER BY a + b unterstützt, aber GROUP BY a, b ORDER BY a + b nicht.  


HAVING-Klausel:

- Unterliegt den gleichen Ausdruckseinschränkungen wie die WHERE-Klausel.


#### <a name="order-by-and-top-are-supported-in-natively-compiled-modules-with-some-restrictions"></a>ORDER BY und TOP werden in nativ kompilierten Modulen mit einigen Einschränkungen unterstützt.


- Es gibt keine Unterstützung für **WITH TIES** oder **PERCENT** in der **TOP** -Klausel.


- Es gibt keine Unterstützung für **DISTINCT** in der **ORDER BY** -Klausel.  


- **TOP** in Kombination mit **ORDER BY** unterstützt höchstens den Wert 8.192 bei Verwendung einer Konstante in der **TOP** -Klausel.
  - Dieser Grenzwert kann herabgesetzt werden, wenn die Abfrage Joins oder Aggregatfunktionen enthält. (Beispielsweise liegt die Beschränkung bei einem Join mit zwei Tabellen bei 4.096 Zeilen. Bei zwei Joins mit drei Tabellen lautet der Grenzwert 2.730 Zeilen).  
  - Sie können Ergebnisse erhalten, die größer als 8.192 sind, indem Sie die Anzahl von Zeilen in einer Variablen speichern:  

```tsql
DECLARE @v INT = 9000;
SELECT TOP (@v) … FROM … ORDER BY …
```

Eine Konstante in der **TOP** -Klausel führt jedoch im Vergleich zur Verwendung einer Variablen zu einer besseren Leistung.  

Diese Einschränkungen für nativ kompilierte [!INCLUDE[tsql](../../includes/tsql-md.md)] gelten nicht für den interpretierten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff auf speicheroptimierte Tabellen.  


##  <a name="a-namedmla-data-modification"></a><a name="dml"></a> Datenänderung  

Die folgenden DML-Anweisungen werden unterstützt.  

-   INSERT VALUES (eine Zeile pro Anweisung) und INSERT... SELECT  

-   UPDATE  

-   DELETE  

-   WHERE wird zusammen mit UPDATE- und DELETE-Anweisungen unterstützt.  

##  <a name="a-namecofa-control-of-flow-language"></a><a name="cof"></a> Sprachkonstrukte zur Ablaufsteuerung  
 Die folgenden Sprachkonstrukte zur Ablaufsteuerung werden unterstützt.  

-   [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  

-   [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  

-   [RETURN &#40;Transact-SQL&#41;](../../t-sql/language-elements/return-transact-sql.md)  

-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md) kann alle [unterstützten Datentypen für In-Memory OLTP](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md) sowie speicheroptimierte Tabellentypen verwenden. Variablen können als NULL oder NOT NULL deklariert werden.  

-   [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  

-   [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  

               To achieve optimal performance, use a single TRY/CATCH block for an entire natively compiled T-SQL module.  

-   [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)  

-   BEGIN ATOMIC (auf der äußeren Ebene der gespeicherten Prozedur). Weitere Informationen finden Sie unter [ATOMIC-Blöcke](../../relational-databases/in-memory-oltp/atomic-blöcke-in-nativen-prozeduren.md).  

##  <a name="a-namesoa-supported-operators"></a><a name="so"></a> Unterstützte Operatoren  
 Die folgenden Operatoren werden unterstützt.  

-   [Vergleichsoperatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md) (z.B. >, \<, >=, und <=)  

-   Unäre Operatoren (+, -)  

-   Binäre Operatoren (*, /, +, -, % (Modulo)).  

               The plus operator (+) is supported on both numbers and strings.  

-   Logische Operatoren (AND, OR, NOT).  

-   Bitweise Operatoren ~, &, |, und ^  

-   APPLY-Operator
    - **Gilt für:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Ab [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 wird der APPLY-Operator in nativ kompilierten Modulen unterstützt.

##  <a name="a-namebfncspa-built-in-functions-in-natively-compiled-modules"></a><a name="bfncsp"></a> Integrierte Funktionen in nativ kompilierten Modulen  
 Die folgenden Funktionen werden in Einschränkungen in speicheroptimierten Tabellen und in nativ kompilierten T-SQL-Modulen unterstützt.  

-   [Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md) (alle)  

-   Datumsfunktionen: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME und YEAR.  

-   Zeichenfolgenfunktionen: LEN, LTRIM, RTRIM und SUBSTRING.  
    - **Gilt für:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Ab [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 werden die folgenden integrierten Funktionen ebenfalls unterstützt: TRIM, TRANSLATE und CONCAT_WS.  

-   Identitätsfunktionen: SCOPE_IDENTITY  

-   NULL-Funktionen: ISNULL  

-   Uniqueidentifier-Funktionen: NEWID und NEWSEQUENTIALID  

-   JSON-Funktionen  
    - **Gilt für:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Ab [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 werden die JSON-Funktionen in nativ kompilierten Modulen unterstützt.

-   Fehlerfunktionen: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY und ERROR_STATE  

-   Systemfunktionen: @@rowcount. Durch Anweisungen in nativ kompilierten gespeicherten Prozeduren wird @@rowcount aktualisiert, und Sie können @@rowcount in einer nativ kompilierten gespeicherten Prozedur verwenden, um die Anzahl der Zeilen zu bestimmen, die von der letzten Anweisung betroffen sind, die innerhalb der nativ kompilierten gespeicherten Prozedur ausgeführt wurde. Allerdings wird @@rowcount am Anfang und am Ende der Ausführung einer nativ kompilierten gespeicherten Prozedur auf 0 zurückgesetzt.  

-   Sicherheitsfunktionen: IS_MEMBER({'Gruppe' | 'Rolle'}), IS_ROLEMEMBER ('Rolle' [, 'database_principal']), IS_SRVROLEMEMBER ('Rolle' [, 'Anmeldename']), ORIGINAL_LOGIN(), SESSION_USER, CURRENT_USER, SUSER_ID(['Anmeldename']), SUSER_SID(['Anmeldename'] [, Param2]), SUSER_SNAME([server_user_sid]), SYSTEM_USER, SUSER_NAME, USER, USER_ID(['Benutzer']), USER_NAME([ID]), CONTEXT_INFO().

-   Die Ausführungen nativer Module können geschachtelt werden.

##  <a name="a-nameauditinga-auditing"></a><a name="auditing"></a> Überwachen  
 Überwachung auf Prozedurebene wird für systemintern kompilierte gespeicherte Prozeduren unterstützt.  

 Weitere Informationen zur Überwachung finden Sie unter [Create a Server Audit and Database Audit Specification](../../relational-databases/security/auditing/create-a-server-audit-and-database-audit-specification.md).  

##  <a name="a-nametqha-table-and-query-hints"></a><a name="tqh"></a> Tabellen- und Abfragehinweise  
 Folgende werden unterstützt:  

-   INDEX-, FORCESCAN- und FORCESEEK-Hinweise, entweder in der Tabellenhinweissyntax oder in der [OPTION-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/option-clause-transact-sql.md) der Abfrage. Weitere Informationen finden Sie unter [Tabellenhinweise &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md).  

-   FORCE ORDER  

-   LOOP JOIN-Hinweis  

-   OPTIMIZE FOR  

 Weitere Informationen finden Sie unter [Abfragehinweise &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).  

##  <a name="a-namelosa-limitations-on-sorting"></a><a name="los"></a> Einschränkungen bei der Sortierung  
 Sie können mehr als 8.000 Zeilen in einer Abfrage sortieren, die [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) und eine [ORDER BY-Klausel &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md) verwendet. Ohne die [ORDER BY-Klausel &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md) kann [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) eine Sortierung von bis zu 8.000 Zeilen durchführen (weniger Zeilen, falls es Verknüpfungen gibt).  

 Wenn die Abfrage jeweils den Operator [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) und eine [ORDER BY-Klausel &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md) verwendet, können Sie bis zu 8192 Zeilen für den TOP-Operator angeben. Wenn Sie mehr als 8192 Zeilen angeben, wird die Fehlermeldung angezeigt: **Msg 41398, Level 16, State 1, Procedure *<ProzedurName>\>*, Line *<ZeilenNummer>\>* Der Operator TOP kann maximal 8192 Zeilen zurückgeben; *<Zahl>\>* wurde angefordert.**  

 Wenn keine TOP-Klausel vorhanden ist, kann eine beliebige Anzahl von Zeilen mit ORDER BY sortiert werden.  

 Wenn keine ORDER BY-Klausel verwendet wird, können Sie jeden ganzzahligen Wert mit dem TOP-Operator verwenden.  

 Beispiel mit TOP N = 8192: Wird kompiliert  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Beispiel mit TOP N > 8192: Kann nicht kompiliert werden  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Die Einschränkung auf 8192 Zeilen gilt nur für `TOP N`, wobei `N` wie in den Beispielen oben eine Konstante ist.  Wenn `N` größer als 8192 sein muss, können Sie den Wert einer Variablen zuweisen und die Variable mit `TOP`verwenden.  

 Beispiel mit einer Variablen: Wird kompiliert  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 **Einschränkungen für zurückgegebene Zeilen:** Es gibt zwei Fälle, in denen sich die Anzahl der Zeilen, die vom TOP-Operator zurückgegeben werden können, u. U. verringert:  

-   Verwenden von JOINs in der Abfrage  Die Auswirkungen von JOINs auf die Einschränkung sind vom Abfrageplan abhängig.  

-   Verwenden von Aggregatfunktionen oder Verweisen auf Aggregatfunktionen in der ORDER BY-Klausel  

 Die Formel zum Berechnen eines im ungünstigsten Fall unterstützten Maximalwerts für N in TOP N lautet wie folgt: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  

## <a name="see-also"></a>Siehe auch  
 [Nativ kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)   
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
