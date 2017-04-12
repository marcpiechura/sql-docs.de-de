---
title: "Richtlinien f&#252;r Onlineindexvorg&#228;nge | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gruppierte Indizes, Onlinevorgänge"
  - "Onlineindexvorgänge"
  - "Indizes [SQL Server], Onlinevorgänge"
  - "Speicherplatz auf dem Datenträger [SQL Server], Indizes"
  - "Nicht gruppierte Indizes [SQL Server], Onlinevorgänge"
  - "Transaktionsprotokolle [SQL Server], Indizes"
ms.assetid: d82942e0-4a86-4b34-a65f-9f143ebe85ce
caps.latest.revision: 64
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 60
---
# Richtlinien f&#252;r Onlineindexvorg&#228;nge
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Für das Ausführen von Onlineindexvorgängen gelten die folgenden Richtlinien:  
  
-   Gruppierte Indizes müssen offline erstellt, neu erstellt oder gelöscht werden, wenn die zugrunde liegende Tabelle die folgenden LOB-Datentypen (Large Object) enthält: **image**, **ntext**und **text**.  
  
-   Nicht eindeutige, nicht gruppierte Indizes können online erstellt werden, wenn die Tabelle LOB-Datentypen enthält, keine dieser Spalten jedoch in der Indexdefinition als Schlüssel- oder Nichtschlüsselspalte (eingeschlossene Spalte) verwendet wird.  
  
-   Indizes für lokale temp-Tabellen können nicht online erstellt, neu erstellt oder gelöscht werden. Diese Einschränkung gilt nicht für Indizes globaler temporärer Tabellen.  
  
> [!NOTE]  
>  Onlineindexvorgänge sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 Die folgende Tabelle enthält eine Auflistung der Indexvorgänge, die online ausgeführt werden können, und der Indizes, die von diesen Onlinevorgängen ausgeschlossen sind. Zusätzliche Einschränkungen werden ebenfalls aufgeführt.  
  
|Onlineindexvorgang|Ausgeschlossene Indizes|Andere Einschränkungen|  
|----------------------------|----------------------|------------------------|  
|ALTER INDEX REBUILD|Deaktivierter gruppierter Index oder deaktivierte indizierte Sicht<br /><br /> XML-Index<br /><br />Columnstore-Index <br /><br /> Index für eine lokale temp-Tabelle|Die Angabe des ALL-SchlüsselwOrts kann bewirken, dass die Operation einen Fehler erzeugt, wenn die Tabelle einen ausgeschlossenen Index enthält.<br /><br /> Weitere Einschränkungen zum Neuerstellen deaktivierter Indizes gelten ebenfalls. Weitere Informationen finden Sie unter [Deaktivieren von Indizes und Einschränkungen](../../relational-databases/indexes/disable-indexes-and-constraints.md).|  
|CREATE INDEX|XML-Index<br /><br /> Eindeutiger gruppierter Ausgangsindex für eine Sicht<br /><br /> Index für eine lokale temp-Tabelle||  
|CREATE INDEX WITH DROP_EXISTING|Deaktivierter gruppierter Index oder deaktivierte indizierte Sicht<br /><br /> Index für eine lokale temp-Tabelle<br /><br /> XML-Index||  
|DROP INDEX|Deaktivierter Index<br /><br /> XML-Index<br /><br /> Nicht gruppierter Index<br /><br /> Index für eine lokale temp-Tabelle|Es können nicht mehrere Indizes in einer einzigen Anweisung angegeben werden.|  
|ALTER TABLE ADD CONSTRAINT (PRIMARY KEY oder UNIQUE)|Index für eine lokale temp-Tabelle<br /><br /> Gruppierter Index|Es ist nur jeweils eine Unterklausel gleichzeitig zulässig. Sie können z. B. PRIMARY KEY- oder UNIQUE-Einschränkungen nicht in der gleichen ALTER TABLE-Anweisung hinzufügen oder löschen.|  
|ALTER TABLE DROP CONSTRAINT (PRIMARY KEY oder UNIQUE)|Gruppierter Index||  
  
 Die zugrunde liegende Tabelle kann nicht geändert, abgeschnitten oder gelöscht werden, während ein Onlineindexvorgang ausgeführt wird.  
  
 Die beim Erstellen oder Löschen eines gruppierten Indexes angegebene Einstellung für die Onlineoption (ON oder OFF) wird auf alle nicht gruppierten Indizes angewendet, die neu erstellt werden müssen. Wenn der gruppierte Index z. B. online mithilfe von CREATE INDEX WITH DROP_EXISTING, ONLINE=ON erstellt wird, werden alle zugeordneten nicht gruppierten Indizes ebenfalls online neu erstellt.  
  
 Wenn Sie einen UNIQUE-Index online erstellen oder neu erstellen, versuchen die Indexerstellung und eine gleichzeitige Benutzertransaktion möglicherweise, den gleichen Schlüssel einzufügen. Dies verletzt die Eindeutigkeit. Wenn eine von einem Benutzer in den neuen Index (Ziel) eingegebene Zeile eingefügt wird, bevor die ursprüngliche Zeile aus der Quelltabelle in den neuen Index verschoben wird, schlägt der Onlineindexvorgang fehl.  
  
 Obwohl der Fall nicht häufig auftritt, kann der Onlineindexvorgang aufgrund von Benutzer- oder Anwendungsaktivitäten einen Deadlock bewirken, wenn sie mit den Datenbankupdates interagiert. In diesen seltenen Fällen wählt [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Benutzer- oder Anwendungsaktivität als Deadlockopfer aus.  
  
 Sie können gleichzeitige Onlineindex-DDL-Operationen für die gleiche Tabelle oder Sicht nur dann ausführen, wenn Sie mehrere neue, nicht gruppierte Indizes erstellen oder nicht gruppierte Indizes neu organisieren. Alle anderen gleichzeitig durchgeführten Onlineindexvorgänge erzeugen einen Fehler. Sie können z. B. keinen neuen Index online erstellen, während Sie einen vorhandenen Index für die gleiche Tabelle online neu erstellen.  
  
 Ein Onlinevorgang kann nicht ausgeführt werden, wenn ein Index eine Spalte des Datentyps für große Objekte enthält und wenn dieselbe Transaktion vor diesem Onlinevorgang Updatevorgänge enthält. Um dieses Problem zu umgehen, platzieren Sie den Onlinevorgang außerhalb der Transaktion oder vor den Updates in der Transaktion.  
  
## <a name="disk-space-considerations"></a>Überlegungen zum Speicherplatz  
 Im Allgemeinen gelten für Online- und OfflineIndexvorgänge die gleichen Speicherplatzanforderungen. Eine Ausnahme bildet der zusätzliche Speicherplatz, der für den temporären Zuordnungsindex erforderlich ist. Dieser temporäre Index wird in Onlineindexvorgängen verwendet, die einen gruppierten Index erstellen, neu erstellen oder löschen. Das Löschen eines gruppierten Indexes online benötigt den gleichen Speicherplatz wie das Erstellen eines gruppierten Indexes online. Weitere Informationen finden Sie unter [Disk Space Requirements for Index DDL Operations](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md).  
  
## <a name="performance-considerations"></a>Leistungsaspekte  
 Zwar ermöglichen Onlineindexvorgänge gleichzeitige Benutzerupdateaktivitäten, die Indexvorgänge benötigen jedoch mehr Zeit, wenn die Updateaktivitäten umfangreich sind. In der Regel sind Onlineindexvorgänge langsamer als die entsprechenden Offlineindexvorgänge, und zwar unabhängig davon, in welchem Umfang gleichzeitige Updateaktivitäten ausgeführt werden.  
  
 Da sowohl die Quell- als auch die Zielstrukturen während des Onlineindexvorgangs verwaltet werden, kann die Ressourcenverwendung für Einfüge-, Update- und Löschtransaktionen bis um das Doppelte zunehmen. Dieser Vorgang kann einen Leistungsabfall und erhöhte Ressourcenverwendung (insbesondere CPU-Zeit) während des Indexvorgangs bewirken. Onlineindexvorgänge werden vollständig protokolliert.  
  
 In der Regel werden Onlinevorgänge empfohlen, Sie sollten jedoch Ihre Umgebung sowie besondere Anforderungen berücksichtigen. Es kann vorteilhafter sein, Indexvorgänge offline auszuführen. Dabei besitzen Benutzer während der Operation nur eingeschränkten Zugriff auf die Daten, der Vorgang wird jedoch schneller abgeschlossen und verwendet weniger Ressourcen.  
  
 Auf Mehrprozessorcomputern, auf denen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ausgeführt wird, verwenden Indexanweisungen möglicherweise mehrere Prozessoren, um die Scan- und Sortierungsvorgänge auszuführen, die mit der Indexanweisung verknüpft sind, genau so, wie andere Abfragen dies tun. Sie können die MAXDOP-Indexoption verwenden, um die Anzahl der Prozessoren für den Onlineindexvorgang zu steuern. Auf diese Weise können Sie die Ressourcen, die vom Indexvorgang verwendet werden, mit den Ressourcen gleichzeitiger Benutzer ausgleichen. Weitere Informationen finden Sie unter [Konfigurieren von Parallelindexvorgängen](../../relational-databases/indexes/configure-parallel-index-operations.md). Weitere Informationen zu den Editionen von SQL Server, die parallele Indexvorgänge unterstützen, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 Da eine Sperre des Typs S- oder Sch-M in der Abschlussphase des Indexvorgangs aktiviert wird, sollten Sie Vorsicht walten lassen, wenn Sie einen Onlineindexvorgang innerhalb einer expliziten Benutzertransaktion ausführen, z. B. in einem BEGIN TRANSACTION...COMMIT-Block. In diesem Fall bleibt die Sperre aktiviert, bis die Transaktion beendet ist, und beeinträchtigt daher die Benutzerparallelität.  
  
 Die Onlineneuerstellung von Indizes kann die Fragmentierung erhöhen, wenn diese für die `MAX DOP > 1` -Option und die `ALLOW_PAGE_LOCKS = OFF` -Option aktiviert ist. Weitere Informationen finden Sie unter [Vorgehensweise: Onlineneuerstellung von Indizes kann zu erhöhter Fragmentierung führen](http://blogs.msdn.com/b/psssql/archive/2012/09/05/how-it-works-online-index-rebuild-can-cause-increased-fragmentation.aspx).  
  
## <a name="transaction-log-considerations"></a>Überlegungen zum Transaktionsprotokoll  
 Umfangreiche Indexvorgänge, die offline oder online ausgeführt werden, können große Datenlasten generieren, die das Transaktionsprotokoll schnell füllen können. Damit sichergestellt wird, dass für den Indexvorgang ein Rollback ausgeführt werden kann, kann das Transaktionsprotokoll erst abgeschnitten werden, nachdem der Indexvorgang abgeschlossen wurde; das Protokoll kann jedoch während des Indexvorgangs gesichert werden. Aus diesem Grund muss das Transaktionsprotokoll für die Dauer des Indexvorgangs genügend Speicherplatz zum Speichern der Transaktionen des Indexvorgangs sowie ggf. der gleichzeitigen Benutzertransaktionen aufweisen. Weitere Informationen finden Sie unter [Transaction Log Disk Space for Index Operations](../../relational-databases/indexes/transaction-log-disk-space-for-index-operations.md).  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Funktionsweise von Onlineindexvorgängen](../../relational-databases/indexes/how-online-index-operations-work.md)  
  
 [Ausführen von Onlineindexvorgängen](../../relational-databases/indexes/perform-index-operations-online.md)  
  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
  