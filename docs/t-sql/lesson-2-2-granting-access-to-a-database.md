---
title: Gewähren von Zugriff auf eine Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 40071e1d42cbc8906084bab62f625516df653335
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Lektion 2.2: Gewähren von Zugriff auf eine Datenbank
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Mary hat nun Zugriff auf diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], verfügt jedoch nicht über die Berechtigung zum Zugriff auf die Datenbanken. Selbst auf die Standarddatenbank **TestData** kann sie erst zugreifen, wenn Sie sie als Datenbankbenutzerin autorisieren.  
  
Wenn Sie Mary Zugriff gewähren möchten, wechseln Sie zur **TestData** -Datenbank, und ordnen Sie ihren Anmeldenamen mithilfe der CREATE USER-Anweisung einer Benutzerin namens Mary zu.  
  
### <a name="to-create-a-user-in-a-database"></a>So erstellen Sie einen Benutzer in einer Datenbank  
  
1.  Geben Sie die folgenden Anweisungen ein (wobei Sie `computer_name` durch den Namen Ihres Computers ersetzen), und führen Sie sie aus, um `Mary` Zugriff auf die `TestData` -Datenbank zu gewähren.  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    Mary hat nun sowohl auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als auch auf die `TestData` -Datenbank Zugriff.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
[Erstellen von Sichten und gespeicherten Prozeduren](../t-sql/lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
  
