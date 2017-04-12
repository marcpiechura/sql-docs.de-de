---
title: "Konfigurieren der Websynchronisierung | Microsoft Docs"
ms.custom: ""
ms.date: "01/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.SNAPSHARE.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.SNAPSHARE.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.VIRDIRINFO.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.CLIENTAUTH.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.DIRACCESS.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.SUBTYPE.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.ANONACCESS.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.WEBSERV.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.CLIENTAUTH.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.SUBTYPE.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.COMPLETEWIZ.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.DIRACCESS.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.ANONACCESS.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.AUTHACCESS.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.AUTHACCESS.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.COMPLETEWIZ.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.VIRDIRINFO.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.WEBSERV.F1"
helpviewer_keywords: 
  - "Websynchronisierung, bewährte Methoden bezüglich der Sicherheit"
  - "Websynchronisierung, konfigurieren"
ms.assetid: 21f8e4d4-cd07-4856-98f0-9c9890ebbc82
caps.latest.revision: 74
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 73
---
# Konfigurieren der Websynchronisierung
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die Websynchronisierungsoption für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Mergereplikation ermöglicht die Datenreplikation mithilfe des HTTPS-Protokolls über das Internet. Um die Websynchronisierung zu verwenden, müssen Sie zuerst die folgenden Konfigurationsaktionen ausführen:  
  
1.  Erstellen Sie neue Domänenkonten und ordnen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen zu.  
  
2.  Konfigurieren Sie den Computer, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internetinformationsdienste (Internet Information Services, IIS) ausgeführt wird, für die Synchronisierung von Abonnements.  
  
3.  Konfigurieren Sie eine Mergeveröffentlichung für die Websynchronisierung.  
  
4.  Konfigurieren Sie ein oder mehrere Abonnements zur Verwendung der Websynchronisierung.  
  
> [!NOTE]  
>  Wenn Sie planen, große Datenmengen replizieren oder umfangreiche Datentypen wie **varchar(max)**, lesen Sie den Abschnitt "Replizieren großer Datenmengen" in diesem Thema.  
  
 Um die Websynchronisierung erfolgreich einzurichten, müssen Sie entscheiden, wie die Sicherheit gemäß bestimmter Anforderungen und Richtlinien konfiguriert werden soll. Es wird empfohlen, diese Entscheidungen zu treffen und die notwendigen Konten zu erstellen, bevor Sie IIS, die Veröffentlichung und die Abonnements konfigurieren.  
  
 In den folgenden Schritten wird aus Platzgründen eine vereinfachte Sicherheitskonfiguration mit lokalen Konten beschrieben. Diese vereinfachte Konfiguration ist für Installationen geeignet, bei denen IIS und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger und -Verteiler auf dem gleichen Computer ausgeführt werden, obwohl es viel wahrscheinlicher ist (und empfohlen wird), dass eine Multiservertopologie für eine Produktionsinstallation verwendet wird. Sie können in diesen Schritten die lokalen Konten durch Domänenkonten ersetzen.  
  
## Erstellen von neuen Konten und Zuordnen von SQL Server-Anmeldungen  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Replikationsüberwachung (replisapi.dll) stellt eine Verbindung mit dem Verleger durch Identitätswechsel des für den Anwendungspool angegebenen Kontos her, der der Replikationswebsite zugeordnet ist.  
  
 Das Konto für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -replikationsüberwachung muss über Berechtigungen verfügen, wie in beschrieben [Sicherheit für den Merge-Agent](../../relational-databases/replication/merge-agent-security.md), klicken Sie im Abschnitt "Verbinden mit dem Verleger oder Verteiler". Zusammengefasst muss das Konto folgende Bedingungen erfüllen:  
  
-   Es muss Mitglied der Veröffentlichungszugriffsliste (PAL) sein.  
  
-   Es muss einer mit einem Benutzer in der Veröffentlichungsdatenbank verknüpften Anmeldung zugeordnet sein.  
  
-   Es muss einer mit einem Benutzer in der Verteilungsdatenbank verknüpften Anmeldung zugeordnet sein.  
  
-   Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.  
  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Replikation das erste Mal verwenden, müssen Sie auch Konten und Anmeldungen für die Replikations-Agents erstellen. Weitere Informationen finden Sie in diesem Thema in den Abschnitten "Konfigurieren der Veröffentlichung" und "Konfigurieren des Abonnements".  
  
 Bevor Sie die Websynchronisierung konfigurieren, sollten Sie den Abschnitt "Bewährte Methoden bezüglich der Sicherheit bei der Websynchronisierung" in diesem Thema lesen. Weitere Informationen zur Sicherheit bei der Websynchronisierung finden Sie unter [Security Architecture for Web Synchronization](../../relational-databases/replication/security/security-architecture-for-web-synchronization.md).  
  
## Konfigurieren des Computers, auf dem IIS ausgeführt wird  
 Für die Websynchronisierung ist es erforderlich, IIS zu installieren und zu konfigurieren. Sie benötigen die URL zur Replikationswebsite, bevor Sie eine Veröffentlichung zur Verwendung der Websynchronisierung konfigurieren können.  
  
 Websynchronisierung wird auf IIS ab Version 5.0, unterstützt. Der Assistent zum Konfigurieren der Websynchronisierung wird auf IIS Version 7.0 nicht unterstützt. Beginnend mit SQL Server 2012, verwenden Sie die Web-Sync-Komponente auf IIS-Server empfiehlt es sich Benutzer bei der Installation SQL Server mit der Replikation. Dies kann der kostenlosen SQL Server Express Edition sein.  
  
 SSL ist für die Websynchronisierung erforderlich. Sie benötigen ein von einer Zertifizierungsstelle ausgestelltes Sicherheitszertifikat. Nur zu Testzwecken können Sie ein selbst ausgestelltes Sicherheitszertifikat verwenden.  
   
  
 **So konfigurieren Sie IIS für die Websynchronisierung**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Configure IIS for Web Synchronization](../../relational-databases/replication/configure-iis-for-web-synchronization.md)  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Configure IIS 7 for Web Synchronization](../../relational-databases/replication/configure-iis-7-for-web-synchronization.md)  
  
## Erstellen eines Webgartens  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Replikationsüberwachung unterstützt zwei gleichzeitige Synchronisierungsvorgänge pro Thread. Das Überschreiten dieser Grenze kann dazu führen, dass die Replikationsüberwachung nicht mehr antwortet. Die Anzahl der replisapi.dll zugeordneten Threads wird von der Eigenschaft "Maximale Anzahl von Arbeitsprozessen" des Anwendungspools bestimmt. Standardmäßig ist diese Eigenschaft auf 1 festgelegt.  
  
 Erhöhen Sie den Wert der Eigenschaft "Maximale Anzahl von Arbeitsprozessen", um eine größere Anzahl gleichzeitiger Synchronisierungsvorgänge pro CPU zu unterstützen. Das horizontale Skalieren durch Erhöhen der Anzahl von Arbeitsprozessen pro CPU wird als Erstellen eines "Webgartens" bezeichnet.  
  
 Ein Webgarten lässt die gleichzeitige Synchronisierung von mehr als zwei Abonnenten zu. Er erhöht außerdem die CPU-Auslastung durch replisapi.dll, was sich negativ auf die Gesamtleistung des Servers auswirken kann. Diese Überlegungen müssen bei der Auswahl eines Werts für die Eigenschaft "Maximale Anzahl von Arbeitsprozessen" beachtet werden.  
  
#### So erhöhen Sie die maximale Anzahl von Arbeitsprozessen in IIS 7  
  
1.  Im **Internet Information Services (IIS) Manager**, erweitern Sie den lokalen Server-Knoten, und klicken Sie dann auf die **Anwendungspool** Knoten.  
  
2.  Wählen Sie den der Websynchronisierungswebsite zugeordneten Anwendungspool aus, und klicken Sie dann im Bereich **Aktionen** auf **Erweiterte Einstellungen** .  
  
3.  Klicken Sie im Dialogfeld **Erweiterte Einstellungen** unter der Überschrift **Prozessmodell**auf die Zeile mit der Bezeichnung Maximale Anzahl von Arbeitsprozessen. Ändern Sie den Eigenschaftswert, und klicken Sie dann auf **OK**.  
  
## Konfigurieren der Veröffentlichung  
 Erstellen Sie eine Veröffentlichung auf dieselbe Weise wie für eine standardmäßige Mergetopologie, um die Websynchronisierung zu verwenden. Weitere Informationen finden Sie unter [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
 Nachdem die Veröffentlichung erstellt wurde, aktivieren Sie die Option zur Synchronisierung von mithilfe einer der folgenden Methoden: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], oder Replikationsverwaltungsobjekten (RMO). Um die Websynchronisierung zu aktivieren, müssen Sie die Webserveradresse für Abonnentenverbindungen angeben.  
  
 Wenn Sie einen Verleger zum ersten Mal verwenden, müssen Sie auch einen Verteiler und eine Momentaufnahmefreigabe konfigurieren. Der Merge-Agent bei jedem Abonnenten muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen. Weitere Informationen finden Sie unter [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md) und [Sichern des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
 **gen** ist ein reserviertes Wort in Websync-Dateien (XML). Versuchen Sie nicht, Tabellen zu veröffentlichen, in denen Spalten mit dem Namen **gen**enthalten sind.  
  
## Konfigurieren des Abonnements  
 Nachdem Sie eine Veröffentlichung aktiviert und IIS konfiguriert haben, erstellen Sie ein Pullabonnement und geben an, dass es mithilfe von IIS synchronisiert werden soll. (Die Websynchronisierung wird nur für Pullabonnements unterstützt.)  
  
## Aktualisieren von einer früheren Version von SQL Server  
 Wenn eine vorhandene Websynchronisierungstopologie konfiguriert wurde und Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisieren, müssen Sie sicherstellen, dass die neueste Version von Replisapi.dll in das von der Websynchronisierung verwendete virtuelle Verzeichnis kopiert wird. Standardmäßig befindet sich die neueste Version von Replisapi.dll in c:\Programme\Microsoft SQL Server\\< Nnn\>\COM.  
  
## Replizieren großer Datenmengen  
 Um Speicherprobleme auf Abonnentencomputern zu vermeiden, verwendet die Websynchronisierung eine maximale Standardgröße von 100 MB für die XML-Datei zur Übertragung von Änderungen. Die Grenze kann in folgendem Registrierungsschlüssel erweitert werden:  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\Replication**  
  
 **WebSyncMaxXmlSize DWORD 2000000**  
  
 Der Bereich akzeptabler Werte für diesen Schlüssel ist 100 MB bis 4 GB. Der Wert wird in KB angegeben. Das Setzen diese Parameters auf einen hohen Wert bietet keine Garantie, dass Sie diese Datenmenge synchronisieren können. Die effektive Grenze ist davon abhängig, wie viel zusammenhängender Arbeitsspeicher auf dem Abonnentencomputer verfügbar ist. Falls Sie mehr als 100 MB benötigen, sollten Sie den Wert schrittweise erhöhen und den Speicherbedarf bei einer typischen Arbeitsauslastung auf dem Abonnentencomputer testen.  
  
 Die maximale Größe für die XML-Datei beträgt 4 GB, aber die Replikation synchronisiert die Änderungen aus dieser Datei batchweise. Die Batchgröße von Daten und Metadaten beträgt maximal 25 MB. Achten Sie daher darauf, dass die Daten in jedem Batch höchstens 20 MB ausmachen, damit ausreichend Platz für Metadaten und andere Komponenten vorhanden ist. Diese Grenze bringt die folgenden Auswirkungen mit sich:  
  
-   Es können keine Spalten repliziert werden, die bewirken, dass Daten und Metadaten 25 MB überschreiten. Dies möglicherweise ein Problem auf, wenn Sie Zeilen replizieren, die umfangreiche Datentypen, wie z. B. enthalten **varchar(max)**.  
  
-   Wenn Sie große Datenmengen replizieren, müssen Sie ggf. die Batchgröße des Merge-Agents anpassen.  
  
 Die Batchgröße für die Mergereplikation wird in *Generierungen*gemessen, bei denen es sich um Auflistungen von Änderungen pro Artikel handelt. Die Anzahl von Generierungen in einem Batch wird angegeben, mit dem –**DownloadGenerationsPerBatch** und –**unterstützt** Parameter des Merge-Agents. Weitere Informationen finden Sie unter [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md).  
  
 Geben Sie für große Datenmengen eine kleine Zahl für die einzelnen Batchverarbeitungsparameter an. Es wird empfohlen, mit dem Wert 10 zu beginnen und dann je nach Anwendungsanforderungen und -leistung diesen Wert zu optimieren. Normalerweise werden diese Parameter in einem Agentprofil angegeben. Weitere Informationen zu Profilen finden Sie unter [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## Bewährte Methoden bezüglich der Sicherheit bei der Websynchronisierung  
 Es gibt verschiedene Auswahlmöglichkeiten für die sicherheitsbezogenen Einstellungen bei der Websynchronisierung. Der folgende Ansatz ist empfehlenswert:  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verteiler und Verleger kann auf demselben Computer (eine Standardinstallation für die Mergereplikation). IIS sollte jedoch auf einem separaten Computer installiert werden.  
  
-   Verwenden Sie SSL (Secure Sockets Layer), um die Verbindung zwischen dem Abonnenten und dem Computer mit IIS zu verschlüsseln. Dies ist für die Websynchronisierung erforderlich.  
  
-   Verwenden Sie die Standardauthentifizierung für Verbindungen zwischen dem Abonnenten und IIS. Mithilfe der Standardauthentifizierung kann IIS Verbindungen zum Verleger/Verteiler im Namen des Abonnenten herstellen, ohne dass eine Delegierung erforderlich ist. Die Delegierung ist erforderlich, wenn Sie die integrierte Authentifizierung verwenden.  
  
    > [!NOTE]  
    >  Die Standardauthentifizierung ist die Methode, mit der Anmeldeinformationen an IIS weitergegeben werden. Die Standardauthentifizierung verhindert nicht die Angabe von Windows-Domänenkonten für zu IIS hergestellte Verbindungen.  
  
-   Geben Sie an, dass der Momentaufnahme-Agent unter einem Windows-Domänenkonto ausgeführt werden soll und dass der Agent als dieses Konto Verbindungen herstellen soll. (Dies ist die Standardkonfiguration.) Geben Sie an, dass jeder Merge-Agent unter dem Domänenkonto des Benutzers ausgeführt werden soll, der den Abonnentencomputer verwendet. Geben Sie zudem an, dass der Agent Verbindungen als dieses Konto herstellen soll.  
  
     Weitere Informationen zu den erforderlichen Berechtigungen für die Agents finden Sie unter [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Geben Sie das Domänenkonto der Merge-Agent verwendet, wenn Sie für ein Konto und Kennwort angeben der **Webserverinformationen** Seite des Assistenten für neue Abonnements oder bei der Angabe von Werten für die **@internet_url** und **@internet_login** Parameter [Sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Dieses Konto muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.  
  
-   Jede Veröffentlichung sollte ein separates virtuelles Verzeichnis für IIS verwenden.  
  
-   Das Konto, unter dem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Replikationsüberwachung (Replisapi.dll) ausgeführt wird, ist auch das Konto, das während der Synchronisierung eine Verbindung mit dem Verleger und dem Verteiler herstellt. Dieses Konto muss einem SQL-Anmeldekonto auf dem Verleger und dem Verteiler zugeordnet werden. Weitere Informationen finden Sie im Abschnitt "Einstellung Berechtigungen für die SQL-Replikationsüberwachung" in der [Konfigurieren von IIS für die Synchronisierung von](../../relational-databases/replication/configure-iis-for-web-synchronization.md).  
  
-   Sie können FTP verwenden, um die Momentaufnahme vom Verleger an den Computer mit IIS zu übermitteln. Die Momentaufnahme wird von dem Computer mit IIS immer mithilfe von HTTPS an den Abonnenten übermittelt. Weitere Informationen finden Sie unter [Momentaufnahmen über FTP übertragen](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
-   Wenn sich Server in der Replikationstopologie hinter einer Firewall befinden, müssen Sie möglicherweise Ports in der Firewall öffnen, um die Websynchronisierung zu aktivieren.  
  
    -   Der Abonnentencomputer stellt die Verbindung mit dem Computer, auf dem IIS ausgeführt wird, über HTTPS mithilfe von SSL her, das normalerweise für die Verwendung von Port 443 konfiguriert ist. [!INCLUDE[ssEW](../../includes/ssew-md.md)] -Abonnenten können die Verbindung auch über HTTP herstellen, das normalerweise für die Verwendung von Port 80 konfiguriert ist.  
  
    -   Der Computer, auf dem IIS ausgeführt wird, stellt die Verbindung mit dem Verleger oder Verteiler in der Regel über Port 1433 (Standardinstanz) her. Wenn der Verleger oder der Verteiler eine benannte Instanz auf einem Server mit einer anderen Standardinstanz ist, wird normalerweise die Verbindung mit der benannten Instanz über Port 1500 hergestellt.  
  
    -   Wenn der Computer, auf dem ISS ausgeführt wird, vom Verteiler durch eine Firewall getrennt ist und für die Momentaufnahmeübermittlung eine FTP-Freigabe verwendet wird, müssen die für FTP verwendeten Ports geöffnet sein. Weitere Informationen finden Sie unter [Momentaufnahmen über FTP übertragen](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
> [!IMPORTANT]  
>  Das Öffnen von Ports in der Firewall kann dazu führen, dass der Server böswilligen Angriffen ausgesetzt ist. Daher sollten Sie Ports grundsätzlich nur dann öffnen, wenn Sie sicher sind, dass Sie das Konzept von Firewallsystemen verstanden haben. Weitere Informationen finden Sie unter [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## Siehe auch  
 [Websynchronisierung für die Mergereplikation](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  