---
title: Integritätsregeln Verweis (PowerPivot für SharePoint) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3beb9b320044ce76ff7e6302e81041f44b600d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="health-rules-reference-power-pivot-for-sharepoint"></a>Referenz zu Integritätsregeln (Power Pivot für SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In diesem Referenzthema werden die SharePoint-Integritätsregeln beschrieben, die durch eine [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Installation hinzugefügt werden. Diese Regeln werden verwendet, um Probleme mit dem Serverzustand, der Verfügbarkeit oder der Konfiguration einer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Dienstanwendung bzw. einer zugeordneten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz zu melden.  
  
 In der folgenden Tabelle werden die Regeln in der Reihenfolge aufgeführt, in der sie in der SharePoint-Zentraladministration auf der Seite Regeldefinitionen der Integritätsanalyse angezeigt werden. Bei konfigurierbaren Regeln können Sie die Schwellenwerte ändern, bei denen die Regel ausgelöst wird. Weitere Informationen finden Sie unter [Konfigurieren von Power Pivot-Integritätsregeln](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md). Unter "Automatische Reparatur" wird angegeben, ob es eine integrierte Abhilfemaßnahme gibt. Falls ja, können Sie auf der Seite der Problemberichte auf diese klicken, um das Problem zu beheben.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **Hinweis:** Durch [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] werden verschiedene Sätze von Integritätsregeln für unterschiedliche SharePoint-Versionen installiert. Sie finden die Version der installierten Regeln in der Spalte "Version" der folgenden Tabelle oder indem Sie den folgenden Windows PowerShell-Befehl ausführen.  
  
```  
Get-SPHealthAnalysisRule | select name, enabled, summary | where {$_.summary -like “*power*”}  | format-table -property * -autosize | out-default  
```  
  
|Rule|Konfigurierbar|Automatische Reparatur|Version|Description|  
|----------|------------------|-----------------|-------------|-----------------|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Der Analysis Services OLE DB-Anbieter ist nicht auf diesem Computer installiert.|nein|nein|SharePoint 2010|Der OLE DB-Anbieter für Analysis Services ist entweder auf dem Server nicht installiert oder weist die falsche Version auf. Diese Regel wird angezeigt, wenn die SharePoint-Farm Instanzen von Excel Services auf Anwendungsservern enthält, für die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint nicht verfügbar ist. Die Regel warnt Sie, dass der OLE DB-Anbieter für Analysis Services nicht installiert ist, der von Excel Services zum Herstellen einer Verbindung mit [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Daten verwendet wird. Um dieses Problem zu beheben, installieren Sie den OLE DB-Anbieter auf jedem Excel Services-Server, auf dem der OLE DB-Anbieter für Analysis Services nicht vorhanden ist. Sie können den OLE DB-Anbieter für Analysis Services im Microsoft Download Center herunterladen und installieren. Weitere Informationen finden Sie unter [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Registrierungseinstellungen für Microsoft.AnalysisServices.ChannelTransport.dll sind nach der Installation der SQL Server 2008 R2-Version des MSOLAP-Anbieters auf diesem Computer nicht mehr gültig.|nein|ja|SharePoint 2010|Dies ist ein Serverkonfigurationsproblem. Höchstwahrscheinlich wurde die Datei "ChannelTransport.dll" nicht in der globalen Assembly registriert. Führen Sie die automatische Reparatur für diese Regel aus, um die DLL-Datei auf jedem Server zu registrieren, auf dem [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint installiert ist. Alternativ können Sie "regasm.exe" ausführen, um die Datei manuell zu registrieren. Wenn Sie den SharePoint-Timerdienst nicht als lokaler Administrator ausführen, ist ggf. eine manuelle Registrierung erforderlich. Wenn Sie die Registrierungseinstellungen nicht aktualisieren, hat dies eine langsamere Serverkommunikation zwischen Excel Services und dem [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Systemdienst zur Folge, was in bestimmten Sicherheitskonfigurationen Verbindungsfehler auslösen kann.|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendung verfügt nicht über die Berechtigung, den Vorgang abzuschließen.|nein|nein|SharePoint 2010|Diese Regel überprüft, ob die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendungsidentität Datenbankbesitzer der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Serveranwendungsdatenbank ist und über Administratorberechtigungen für die lokale SQL Server Analysis Services-Instanz verfügt. Diese Berechtigungen werden während der Installation und Bereitstellung automatisch gewährt. Wenn dieser Schritt jedoch nicht abgeschlossen wurde, tritt diese Integritätsregel ein.|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendungsidentität sollte nicht der lokalen Administratorgruppe angehören.|nein|nein|SharePoint 2010|Dies ist eine Best Practice, die die Gesamtsicherheit der Bereitstellung verbessert. Wenn Sie die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendung so konfiguriert haben, dass sie unter einem Konto der lokalen Administratorgruppe ausgeführt werden soll, sollten Sie das Dienstkonto in ein Konto ändern, das nicht zu dieser Gruppe gehört. Es wird empfohlen, ein spezielles Konto mit möglichst wenigen Berechtigungen für jeden Dienst zu verwenden. Sie erzielen so eine Dienstisolation und vereinfachen die Überwachung von Anmeldungen. Weitere Informationen zum Ändern des Dienstkontos finden Sie unter [Konfigurieren von Power Pivot-Dienstkonten](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Die Analysis Services-Instanz wird im tabellarischen Modus ausgeführt, aber die Konfigurationseinstellung, die diesen Modus angibt, ist deaktiviert.|nein|nein|SharePoint 2010|Diese Regel überprüft, ob in der SQL Server Analysis Services-Instanz in einer [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Installation die **DeploymentMode** -Servereigenschaft auf 1 festgelegt ist. Wenn die Eigenschaft auf einen anderen Wert festgelegt ist oder wenn der SharePoint-Timerdienst, der die Regelprüfung ausführt, nicht über die Berechtigung zum Öffnen der Datei verfügt, schlägt diese Regel fehl. Weitere Informationen zur Bereitstellungsmoduseigenschaft finden Sie unter [Bestimmen des Servermodus einer Analysis Services-Instanz](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Zeitgeberauftrag für die Datenaktualisierung ist deaktiviert.|nein|nein|SharePoint 2013<br /><br /> SharePoint 2010|Überprüfen Sie die Einstellungen für den Zeitgeberauftrag, um sicherzustellen, dass dieser aktiviert wurde. Wenn Sie die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Datenaktualisierungsfunktion nicht verwenden, können Sie diese Regel ignorieren. Weitere Informationen finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2010](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:Die SQL Server Analysis Services ([!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)])-Dienstkontoinformationen, die vom SQL Server-Konfigurations-Manager verwaltet werden, unterscheiden sich von den Kontoinformationen, die von der Zentraladministration verwaltet werden.|nein|nein|SharePoint 2010|Diese Regel überprüft, ob die Dienstkontoinformationen im SQL Server-Konfigurations-Manager mit den Informationen des verwalteten Kontos in der Zentraladministration für die gleiche Analysis Services-Instanz übereinstimmen. Wenn sich die Konten unterscheiden, wird dem Problem- und Lösungsbericht ein Eintrag hinzugefügt, damit Sie die Dienstkontoinformationen im SQL Server-Konfigurations-Manager auf das in der Zentraladministration angegebene Konto zurücksetzen können. Der SQL Server-Konfigurations-Manager ist kein unterstütztes Tool zum Ändern des Benutzernamens und Kennworts von Dienstkonten in einer [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Installation. Bei Verwendung der Zentraladministration kann die Funktion für verwaltete Konten von SharePoint genutzt werden. Wenn die Farm mehrere [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Server beinhaltet, können inkonsistente Dienstkontoeinstellungen die Verarbeitungs- und Abfrageoperationen auf dem Server beeinträchtigen, der falsche Dienstinformationen aufweist.<br /><br /> Wenn diese Regel ausgelöst wurde, können auf einem einzelnen Server [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Arbeitsmappen vorübergehend genutzt werden. Es wird jedoch empfohlen, das Problem so schnell wie möglich zu beheben. Datenbank- und Dateisystemberechtigungen werden anhand der Kontoinformationen in der Zentraladministration aktualisiert.|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Die bereitgestellte Farmlösung ist nicht auf dem neuesten Stand.|nein|ja|SharePoint 2010|Eine [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Installation verwendet eine Lösung auf Farmebene und eine Lösung auf Webanwendungsebene, um die Funktionen zu installieren. Diese Regel gibt an, dass die Farmlösung relativ zur Version, dem Server oder möglicherweise der Weblösung nicht aktuell ist. Höchstwahrscheinlich handelt es sich hierbei um ein Serverbereitstellungsproblem. Zur Behebung dieses Problems können Sie das SQL Server-Setup ausführen, um eine der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Installationen in der Farm zu reparieren. Weitere Informationen zu Lösungen für eine [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Installation finden Sie unter [Bereitstellen von Power Pivot-Lösungen in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Die CPU-Gesamtauslastung ist zu hoch.|ja|nein|SharePoint 2010|Diese Regel meldet den CPU-Verbrauch auf Systemebene. Die CPU-Gesamtauslastung wird überwacht, da der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Systemdienst diese als Measure des Serverstatus für den zustandsbasierten Lastenausgleich auf mehreren [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Servern in einer Farm verwendet. Erwägen Sie, der Farm einen weiteren Anwendungsserver hinzuzufügen und CPU-intensive Anwendungen auf diesen Server zu verschieben.|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Analysis Services verfügt nicht über genügend CPU-Ressourcen, um die angeforderten Vorgänge auszuführen.|ja|nein|SharePoint 2010|Die Menge der verfügbaren CPU-Ressourcen für den Analysis Services-Prozess (msmdsrv.exe) reicht für den Grad der Aktivität auf diesem Server nicht aus. Erwägen Sie, der Farm einen weiteren [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Server hinzuzufügen. Weitere Informationen finden Sie unter [Prüfliste für die Bereitstellung: Horizontales Skalieren durch Hinzufügen von PowerPivot-Servern zu einer SharePoint 2010-Farm](http://msdn.microsoft.com/library/2dbddcc7-427a-4537-a8e2-56d99b9d967d).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Analysis Services verfügt nicht über genügend Arbeitsspeicher, um die angeforderten Vorgänge auszuführen.|nein|nein|SharePoint 2010|Diese Regel wird ausgelöst, wenn nur noch 5 % des Speichers für Analysis Services verfügbar ist. Auf einem SharePoint-Anwendungsserver sollte eine SQL Server Analysis Services-Instanz immer über einen kleinen Arbeitsspeicher als Reserve verfügen, der nie verwendet wird. Da der Server für die meisten Vorgänge arbeitsspeichergebunden ist, läuft er am besten, wenn er nicht ganz bis zur oberen Grenze ausgeführt wird.<br /><br /> Standardmäßig werden Warnungen aufgrund von unzureichendem Arbeitsspeicher ausgegeben, wenn der verfügbare Speicher auf 5 % gefallen ist. Sie können diesen Wert in einen höheren oder niedrigeren Wert ändern, indem Sie die Einstellungen für die Analysis Services-Instanz anpassen. Weitere Informationen finden Sie unter [Konfigurieren von Power Pivot-Integritätsregeln](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md).<br /><br /> Die 5 % nicht verwendeter Arbeitsspeicher werden als Prozentsatz des Arbeitsspeichers berechnet, der den Analysis Services zugeordnet wird. Wenn der gesamte Speicher z. B. 200 GB beträgt und Analysis Services davon 80 % (oder 160 GB) belegt, dann entsprechen die 5 % nicht verwendeter Speicher 5 % von 160 GB (oder 8 GB).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Die hohe Verbindungsanzahl weist darauf hin, dass weitere Server zur Bewältigung der aktuellen Arbeitslast bereitgestellt werden sollten.|ja|nein|SharePoint 2010|Standardmäßig wird diese Integritätsregel ausgelöst, wenn die Anzahl einzelner Benutzerverbindungen 100 überschreitet. Dieser Standardwert ist ein beliebiger Wert (basiert nicht auf den Hardwarespezifikationen des Servers oder auf der Benutzeraktivität), damit Sie den Wert abhängig von der Serverkapazität und Benutzeraktivität in der Umgebung herauf- oder herabsetzen können. Weitere Informationen finden Sie unter [Konfigurieren von Power Pivot-Integritätsregeln](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Das Verhältnis zwischen Ladeereignissen und Verbindungen ist zu hoch.|ja|nein|SharePoint 2013<br /><br /> SharePoint 2010|Standardmäßig wird diese Integritätsregel ausgelöst, wenn der Prozentsatz der Ladeereignissen im Verhältnis zu Verbindungsereignissen im Verlauf des ganzen Datensammlungszeitraums (standardmäßig 4 Stunden) 50 % überschreitet. Ein Verhältnis in dieser Höhe deutet auf eine sehr hohe Anzahl von Verbindungen zu eindeutigen Arbeitsmappen oder auf zu drastische Cachereduzierungseinstellungen hin (Arbeitsmappen werden schnell entladen und aus dem System entfernt, während Anforderungen für diese Daten noch aktiv sind). Um falsche Positivmeldungen zu vermeiden, müssen in einem Zeitraum von 4 Stunden mindestens 20 Verbindungen vorhanden sein, damit das Verhältnis berechnet werden kann. Sie können als Grundlage dieser Integritätsregel auch ein anderes Verhältnis festlegen. Weitere Informationen finden Sie unter [Konfigurieren von Power Pivot-Integritätsregeln](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md). Weitere Informationen zum Konfigurieren des Caches finden Sie unter [Konfigurieren der Speicherplatzverwendung &#40;Power Pivot für SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Mindestens eine Minidump-Datei wurde im Protokollverzeichnis gefunden, was auf einen Programmabsturz hinweist.|nein|nein|SharePoint 2013<br /><br /> SharePoint 2010|Während eines Programmabsturzes werden Minidump-Dateien generiert, um Informationen über den Status der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendung kurz vor dem Absturz zu erfassen. Diese Informationen können an Microsoft gesendet und für die Problembehandlung verwendet werden. Diese Regel wird ausgelöst, wenn .dmp-Dateien auf dem Server erkannt werden. Die Regel stellt einen Link zu der Datei bereit, die sich im Ordner „\OLAP\Log“ der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint-Instanz befindet. Beachten Sie, dass Sie den Inhalt der Datei nicht mithilfe eines Texteditors anzeigen können. Um eine Minidump-Datei anzuzeigen, müssen Sie ein separates Debugtool herunterladen und installieren. Weitere Informationen finden Sie unter [Debugtools für Windows](http://go.microsoft.com/fwlink/?linkID=208266).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Das Laufwerk, auf dem [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Daten zwischengespeichert werden, verfügt über unzureichenden Speicherplatz.|ja|nein|SharePoint 2010|Standardmäßig wird diese Integritätsregel ausgelöst, wenn der Speicherplatz auf dem Laufwerk mit dem Sicherungsordner geringer als 5 % ist. Weitere Informationen zum Festlegen dieses Prozentsatzes finden Sie unter [Konfigurieren von Power Pivot-Integritätsregeln](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md). Weitere Informationen zur Datenträgernutzung finden Sie unter [Konfigurieren der Speicherplatzverwendung &#40;Power Pivot für SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Verwendungsdaten werden nicht mit der erwarteten Häufigkeit aktualisiert.|ja|nein|SharePoint 2013<br /><br /> SharePoint 2010|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint erfasst Metriken zur Datenaktualisierung, zu Verbindungen und Abfrageantwortzeiten mithilfe des integrierten Systems für die Sammlung von Verwendungsdaten. Diese Verwendungsdaten werden in der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendungs-Datenbank gespeichert, die dann wiederum zum Aktualisieren einer [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Arbeitsmappe ([!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Management Data.xlsx) dient, die Daten für Berichte im [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Management-Dashboard bereitstellt. Diese Regel gibt an, dass Verwendungsdaten nicht mit ausreichender Häufigkeit in die Datei „ [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Management Data.xlsx“ verschoben werden. Die Regel verwendet den Zeitstempel in der XLSX-Datei als Nachweis, dass die Datei aktualisiert wurde. Weitere Probleme im Verwendungsdatensammlungssystem, die die Genauigkeit der Daten beeinträchtigen, werden durch diese Regel nicht erkannt. Überprüfen Sie zum Beheben dieses Fehlers, ob die Zeitgeberaufträge ausgeführt werden. Weitere Informationen zur Sammlung von Verwendungsdaten finden Sie unter [Konfigurieren der Sammlung von Verwendungsdaten für Power Pivot für SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Das MidTier-Prozesskonto sollte die Berechtigung „Alles lesen“ für alle zugeordneten SPWebApplications besitzen.|nein|ja|SharePoint 2013<br /><br /> SharePoint 2010|Die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendungsidentität muss über die Berechtigung **Alles lesen** verfügen, um im Namen von Benutzern, die über die Berechtigung „Nur anzeigen“ für ein Dokument verfügen, auf die SharePoint-Inhaltsdatenbanken zuzugreifen.<br /><br /> Öffnen Sie die Seite [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Dienstkonten konfigurieren **in der Zentraladministration, um zu bestimmen, welches Konto als** -Dienstanwendungsidentität verwendet wird. Höchstwahrscheinlich wird die Dienstanwendung entweder im Dienstanwendungspool des **SharePoint-Webdienstsystems** oder einem dedizierten Anwendungspool ausgeführt.<br /><br /> Obwohl diese Regel die Option **Automatisch reparieren** anbietet, erzielen Sie bessere Ergebnisse, wenn Sie die Berechtigungen manuell gewähren:<br /><br /> <br /><br /> 1) Klicken Sie in der Zentraladministration auf **Webanwendungen verwalten**.<br /><br /> 2) Wählen Sie eine Website aus, und klicken Sie anschließend auf **Benutzerrichtlinie**.<br /><br /> 3) Klicken Sie auf **Benutzer hinzufügen**.<br /><br /> 4) Wählen Sie (Alle-Zonen) aus, und klicken Sie auf **Weiter**.<br /><br /> 5) Geben Sie unter „Benutzer“ die [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Dienstanwendungsidentität ein, und klicken Sie anschließend auf das Kontrollkästchen **Alles lesen** . Klicken Sie auf **6) Fertig stellen**.<br /><br /> 6) Überprüfen Sie die Reparatur. Klicken Sie in Monitoring auf **Regeldefinitionen überprüfen**. Suchen und öffnen Sie die Regel [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] . Klicken Sie auf **Jetzt ausführen**. Gehen Sie zurück zu **Probleme und Lösungen überprüfen** , um sicherzustellen, dass die Regel nicht mehr angezeigt wird.|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Der sekundäre Anmeldedienst (Seclogon) ist deaktiviert|nein|nein|SharePoint 2013<br /><br /> SharePoint 2010|Der sekundäre Anmeldedienst wird verwendet, um Miniaturbilder der [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Arbeitsmappen im [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Katalog zu generieren. Standardmäßig ist der sekundäre Anmeldedienst auf manuellen Start festgelegt. Wenn der Dienst deaktiviert ist, tritt beim Generieren von Miniaturansichten ein Fehler auf. Darüber hinaus enthalten die ULS-Protokolle die Fehlermeldung, dass die Ursache für den Fehler 1058 auf die Deaktivierung des Windows-Diensts "Sekundäre Anmeldung" zurückzuführen ist.<br /><br /> Um die Dienstkonfiguration zu überprüfen, verwenden Sie die Konsolenanwendungsdienste, um Sekundäre Anmeldung zu suchen und deren **Starttyp** in **Manuell**zu ändern. Wenn Sie den Dienst nicht aktivieren können, verfügt Ihre Organisation möglicherweise über eine Gruppenrichtlinie zum Deaktivieren. Fragen Sie einen Administrator, ob dies der Fall ist.<br /><br /> Wenn Sie den Dienst aktiviert haben, werden die Miniaturansichts- oder Momentaufnahmebilder nach und nach aktualisiert. Sie können auch eine Aktualisierung erzwingen, indem Sie den Dienst erneut starten und dann die Eigenschaftenseiten eines bestimmten Berichts öffnen und erneut speichern. Weitere Informationen finden Sie unter [Verwenden des Power Pivot-Katalogs](http://go.microsoft.com/fwlink/?LinkId=246462).|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: ADOMD.NET ist nicht auf einem eigenständigen WFE installiert, das für die Zentraladministration konfiguriert ist|nein|nein|SharePoint 2013<br /><br /> SharePoint 2010|ADOMD.NET ist eine Analysis Services-Clientbibliothek, die Verbindungen mit einer Analysis Services-Datenbank unterstützt. In einer Bereitstellung von [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] für SharePoint ermöglicht ADOMD.NET den Zugriff auf die integrierten Berichte im [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Management-Dashboard der Zentraladministration. Integrierte Berichte sind eigentlich [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] -Arbeitsmappen, die eingebettete Analysis Services-Daten enthalten. Das Management-Dashboard sendet mithilfe von ADOMD.NET eine Verbindungsanforderung an den Server, der in der Arbeitsmappe enthaltene Daten lädt.<br /><br /> In Topologien mit Zentraladministration, die auf einem eigenständigen Web-Front-End-Server ausgeführt wird, müssen Sie ADOMD.NET manuell installieren, wenn Sie diese Berichte im Management-Dashboard anzeigen möchten. Weitere Informationen finden Sie unter [Installieren von ADOMD.NET auf Web-Front-End-Servern, auf denen die Zentraladministration ausgeführt wird](http://msdn.microsoft.com/en-us/c2372180-e847-4cdb-b267-4befac3faf7e).|  
  
  