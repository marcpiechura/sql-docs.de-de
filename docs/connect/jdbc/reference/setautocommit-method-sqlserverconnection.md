---
title: SetAutoCommit-Methode (SQLServerConnection) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f1549693ac6b4e558c2fc86b29dc6aaa6122c235
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# SetAutoCommit-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Autocommit-Modus für diese [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) Objekt, das dem angegebenen Status.  
  
## Syntax  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### Parameter  
 *value*  
  
 **"true"** Autocommit-Modus für die Verbindung aktivieren **"false"** zu deaktivieren.  
  
## Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Hinweise  
 Diese SetAutoCommit-Methode wird von der SetAutoCommit-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Ist für eine Verbindung der Modus für automatische Commits aktiviert, werden alle SQL-Anweisungen als einzelne Transaktionen ausgeführt, und die Commits der SQL-Anweisungen werden als einzelne Transaktionen ausgeführt. Andernfalls die SQL-Anweisungen in Transaktionen, die durch einen Aufruf von entweder beendet werden gruppiert die [Commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md) Methode oder die [Rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md) Methode. Der Modus für automatische Commits ist für neue Verbindungen standardmäßig aktiviert.  
  
 Der Commit wird ausgeführt, wenn die Anweisung abgeschlossen wird oder die nächste Ausführung durchgeführt wird, je nachdem, welches Ereignis zuerst eintritt. Im Fall von Anweisungen, die Zurückgeben einer [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) -Objekt, die Anweisung abgeschlossen wird, wenn die letzte Zeile des Resultsets abgerufen wurde, oder wenn das Resultset geschlossen wurde. In erweiterten Fällen kann eine einzelne Anweisung zusätzlich zu den Ausgabeparameterwerten mehrere Ergebnisse zurückgeben. In diesen Fällen wird der Commit ausgeführt, nachdem alle Ergebnisse und Ausgabeparameterwerte abgerufen wurden.  
  
 Wenn der Autocommit-Modus ist **"false"**, der JDBC-Treiber eine neue Transaktion nach jedem Commit implizit gestartet.  
  
> [!NOTE]  
>  Wenn diese Methode während einer Transaktion aufgerufen wird, wird ein Commit der Transaktion ausgeführt.  
  
## Siehe auch  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  