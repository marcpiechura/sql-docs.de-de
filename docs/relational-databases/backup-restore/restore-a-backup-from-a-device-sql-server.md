---
title: "Wiederherstellung einer Sicherung von einem Medium (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Wiederherstellen von Datenbanken [SQL Server], Gerätewiederherstellungen"
  - "Sicherungsmedien [SQL Server], Wiederherstellen von"
  - "Datenbankwiederherstellungen [SQL Server], Gerätewiederherstellungen"
  - "Medien [SQL Server]"
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Wiederherstellung einer Sicherung von einem Medium (SQL Server)
  In diesem Thema wird beschrieben, wie Sie ein Sicherung von einem Gerät in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] wiederherstellen können.  
  
> [!NOTE]  
>  Informationen zu SQL Server-Sicherung im Microsoft Azure-BLOB-Speicherdienst finden Sie unter [SQL Server-Sicherung und -Wiederherstellung mit dem Microsoft Azure Blob Storage Service](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So stellen Sie eine Sicherung von einem Medium wieder her mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Ist die wiederherzustellende Datenbank nicht vorhanden, muss der Benutzer über CREATE DATABASE-Berechtigungen verfügen, um RESTORE ausführen zu können. Ist die Datenbank vorhanden, werden RESTORE-Berechtigungen standardmäßig den Mitgliedern der festen Serverrollen **sysadmin** und **dbcreator** sowie dem Besitzer (**dbo**) der Datenbank erteilt (für die Option FROM DATABASE_SNAPSHOT ist die Datenbank immer vorhanden).  
  
 RESTORE-Berechtigungen werden Rollen erteilt, in denen Mitgliedsinformationen immer für den Server verfügbar sind. Da die Mitgliedschaft in einer festen Datenbankrolle nur geprüft werden kann, wenn die Datenbank unbeschädigt ist und auf sie zugegriffen werden kann, was beim Ausführen von RESTORE nicht immer der Fall ist, verfügen Mitglieder der festen Datenbankrolle **db_owner** nicht über RESTORE-Berechtigungen.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### So stellen Sie eine Sicherung von einem Medium wieder her  
  
1.  Klicken Sie im Objekt-Explorer nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie je nach Datenbank eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Wiederherstellen**.  
  
4.  Klicken Sie auf den gewünschten Wiederherstellungsvorgangstyp (**Datenbank**, **Dateien und Dateigruppen** oder **Transaktionsprotokoll**). Dadurch wird das entsprechende Wiederherstellungsdialogfeld geöffnet.  
  
5.  Klicken Sie auf der Seite **Allgemein** im Abschnitt **Wiederherstellungsquelle** auf **Von Medium**.  
  
6.  Klicken Sie auf die Schaltfläche zum Durchsuchen für das Textfeld **Von Medium** , sodass das Dialogfeld **Sicherung angeben** geöffnet wird.  
  
7.  Wählen Sie im Textfeld **Sicherungsmedium** das entsprechende ****Sicherungsmedium aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** , um das Dialogfeld **Sicherungsmedium auswählen** zu öffnen.  
  
8.  Wählen Sie im Textfeld **Sicherungsmedium** das Medium aus, das Sie für den Wiederherstellungsvorgang verwenden möchten.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### So stellen Sie eine Sicherung von einem Medium wieder her  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Geben Sie in der [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) -Anweisung ein logisches oder physisches Sicherungsmedium an, das für den Sicherungsvorgang verwendet werden soll. In diesem Beispiel wird ein Wiederherstellungsvorgang von einer Datenträgerdatei mit dem physischen Namen `Z:\SQLServerBackups\AdventureWorks2012.bak`ausgeführt.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## Siehe auch  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md)   
 [Wiederherstellen einer Datenbanksicherung unter dem einfachen Wiederherstellungsmodell &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Wiederherstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)   
 [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)   
 [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)   
 [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
  