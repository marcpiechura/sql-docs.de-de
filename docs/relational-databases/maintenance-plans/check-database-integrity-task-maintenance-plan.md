---
title: "Task &#39;Datenbankintegrit&#228;t &#252;berpr&#252;fen&#39; (Wartungsplan) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.maint.maintplanproperties.integrity.f1"
  - "sql13.swb.maint.integrity.f1"
helpviewer_keywords: 
  - "Datenbankintegrität überprüfen (Dialogfeld für den Task)"
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Task &#39;Datenbankintegrit&#228;t &#252;berpr&#252;fen&#39; (Wartungsplan)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Verwenden Sie das Dialogfeld **Task „Datenbankintegrität überprüfen“**, um die Zuordnung und die strukturelle Integrität von Benutzer- und Systemtabellen sowie Indizes in der Datenbank zu überprüfen, indem Sie die `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung ausführen. Durch die Ausführung von `DBCC` wird sichergestellt, dass etwaige Integritätsprobleme in der Datenbank gemeldet werden und später vom Systemadministrator oder Datenbankbesitzer behoben werden können.  
  
## Optionen  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Datenbanken**  
 Gibt die Datenbanken an, die von dieser Aufgabe betroffen sind.  
  
-   **Alle Datenbanken**  
  
     Generieren Sie einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken außer **tempdb** ausführt.  
  
-   **Alle Systemdatenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken außer **tempdb**ausführt. Für benutzerdefinierte Datenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Alle Benutzerdatenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle benutzerdefinierten Datenbanken ausführt. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Diese Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks nur für die ausgewählten Datenbanken ausführt. Wenn diese Option ausgewählt wird, muss mindestens eine Datenbank in der Liste ausgewählt werden.  
  
    > [!NOTE]  
    >  Wartungspläne werden nur für Datenbanken mit Kompatibilitätsgrad 80 oder höher ausgeführt. Datenbanken mit Kompatibilitätsgrad 70 oder niedriger werden nicht angezeigt.  
  
 **Indizes einschließen**  
 Überprüft die Integrität aller Indexseiten und der Tabellendatenseiten.  
  
 **Nur physisch**  
 Begrenzt die Überprüfung der Integrität der physischen Struktur der Seite, der Datensatzheader und der Zuordnungskonsistenz der Datenbank. Das Verwenden dieser Option verkürzt möglicherweise die Ausführungszeit von DBCC CHECKDB für große Datenbanken. Sie wird daher für die häufige Verwendung in Produktionssystemen empfohlen.  
  
 **Tablock**  
 Bewirkt, dass DBCC CHECKDB Sperren erhält, statt eine interne Datenbankmomentaufnahme zu verwenden. Dies schließt eine kurzfristige exklusive Sperre (X) für die Datenbank ein. Durch diese Option wird DBCC CHECKDB schneller in einer stark ausgelasteten Datenbank ausgeführt, allerdings verringert sich während der Ausführung von DBCC CHECKDB die in der Datenbank verfügbare Parallelität.  
  
 **T-SQL anzeigen**  
 Zeigt die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen an, die für diesen Task auf dem Server auf Basis der ausgewählten Optionen ausgeführt werden.  
  
> [!NOTE]  
>  Wenn die Anzahl der betroffenen Objekte groß ist, kann die Anzeige erhebliche Zeit in Anspruch nehmen.  
  
## Neue Verbindung (Dialogfeld)  
 **Verbindungsname**  
 Geben Sie einen Namen für die neue Verbindung ein.  
  
 **Wählen Sie einen Servernamen aus, oder geben Sie ihn ein.**  
 Wählen Sie den Server aus, zu dem bei der Ausführung dieses Tasks eine Verbindung hergestellt werden soll.  
  
 **Aktualisieren**  
 Mithilfe dieser Option aktualisieren Sie die Liste der verfügbaren Server.  
  
 **Geben Sie Informationen zum Anmelden am Server ein**  
 Legt fest, wie die Authentifizierung gegenüber dem Server stattfindet.  
  
 **Integrierte Sicherheit von Windows NT verwenden**  
 Stellt mithilfe der Windows-Authentifizierung eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
 **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung eine Verbindung zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## Siehe auch  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
  