---
title: "URL-Zugriff (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "URL-Zugriff [Reporting Services]"
  - "Links [Reporting Services], URL-Zugriff"
  - "URL-Zugriff [Reporting Services], Informationen zum URL-Zugriff"
  - "Parameter [Reporting Services], URL-Zugriff"
  - "Berichtsserver [Reporting Services], URL-Zugriff"
  - "Links [Reporting Services]"
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# URL-Zugriff (SSRS)
  Durch den URL-Zugriff des Berichtsservers in SQL Server Reporting Services (SSRS) können Sie Befehle an den Berichtsserver über eine URL-Anforderung senden. Beispielsweise können Sie das Rendering eines Berichts auf einem Berichtsserver im einheitlichen Modus oder in einer SharePoint-Bibliothek anpassen. Möglicherweise haben Sie den Bericht unter Verwendung bestimmter Berichtsparameterwerte angezeigt oder eine bestimmte Berichtsseite gelesen, die für Sie von Interesse war. Diese Informationen können mithilfe vordefinierter URL-Zugriffsparameter in der URL gekapselt werden. Außerdem kann die Berichtsverarbeitung auf dem Berichtsserver weiter angepasst werden, indem Sie Parameter für Renderingformate oder für das Erscheinungsbild des Berichts-Viewers einbetten. Anschließend können Sie diese URL direkt in eine E-Mail oder Webseite einfügen, damit andere Benutzer im Browser auf die gleiche Weise auf den Bericht zugreifen können.  
  
 Weitere Aktionen, die über den URL-Zugriff ausgeführt werden können:  
  
-   Senden von Befehlen an den HTML-Viewer, z. B. zum Anpassen des Erscheinungsbilds  
  
-   Auflisten der untergeordneten Elemente eines Katalogordners  
  
-   Abrufen der XML-Definition eines Katalogelements  
  
-   Rendern einer bestimmten Berichtsverlaufs-Momentaufnahme  
  
-   Verwalten von Berichtssitzungen  
  
 Eine vollständige Liste der über URL-Zugriff verfügbaren Befehle und Einstellungen finden Sie unter [URL-Zugriffsparameterreferenz](../reporting-services/url-access-parameter-reference.md).  
  
## Konzepte für den URL-Zugriff  
 URL-Anforderungen an den Berichtsserver enthalten Parameter, die vom Berichtsserver verarbeitet werden. Wie URL-Anforderungen vom Berichtsserver behandelt werden, hängt von den Parametern, den Parameterpräfixen sowie den Elementtypen ab, die in der URL enthalten sind. Berichtsserver-URLs erfüllen die URL-Formatierungsrichtlinien, wie sie vom gemeinsamen Entwurfsstandard des World Wide Web Consortium W3C/IETF vorgeschlagen wurden. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -URL-Funktionen sind kompatibel mit den meisten Internetbrowsern oder -anwendungen, die Standard-URL-Adressen unterstützen.  
  
### URL-Zugriffssyntax  
 URL-Anforderungen können mehrere Parameter enthalten, die in beliebiger Reihenfolge aufgelistet werden. Parameter werden durch das kaufmännische Und-Zeichen (&) getrennt, Name/Wert-Paare werden durch das Gleichheitszeichen (=) getrennt.  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### Syntaxbeschreibung  
 *rswebserviceurl*  
 Die Webdienst-URL des Berichtsservers. Im einheitlichen Modus ist dies die Webdienst-URL der im Konfigurations-Manager für Reporting Services konfigurierten Berichtsserverinstanz. Weitere Informationen finden Sie unter [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md). Beispiel:  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 Im integrierten SharePoint-Modus entspricht sie der URL des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Proxys auf einer in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]integrierten SharePoint-Website. Beispiel:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  Es ist wichtig, dass die URL die `_vti_bin` -Proxysyntax zur Weiterleitung der Anforderung über SharePoint sowie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -HTTP-Proxy enthält. Durch den Proxy wird der HTTP-Anforderung Kontext hinzugefügt. Dieser ist erforderlich, damit der Bericht auf Berichtsservern im SharePoint-Modus ordnungsgemäß ausgeführt wird.  
  
 *pathinfo*  
 Der relative Pfadname des Elements in der Berichtsserver-Datenbank im einheitlichen Modus oder die vollqualifizierte URL des Elements in einem SharePoint-Katalog.  
  
 Der Pfad des Katalogelements. Im einheitlichen Modus ist dies der relative Pfad des Elements in der Berichtsserver-Datenbank, der mit einem Schrägstrich (**/**) beginnt. Beispiel:  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 Im integrierten SharePoint-Modus ist dies die vollqualifizierte URL des Elements in der SharePoint-Bibliothek, einschließlich der Elementerweiterung. Beispiel:  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 **&**  
 Wird verwendet, um Namen- und Wertpaare von URL-Zugriffsparametern zu trennen.  
  
 **Präfix**  
 Optional. Ein Präfix für den URL-Zugriffsparameter (z.B. `rs:` oder `rc:`), durch das auf einen bestimmten im Berichtsserver ausgeführten Prozess zugegriffen wird.  
  
> [!NOTE]  
>  Wenn das Präfix für einen URL-Zugriffsparameter nicht enthalten ist, wird der Parameter vom Berichtsserver als Berichtsparameter verarbeitet. Bei Berichtsparametern wird kein Parameterpräfix verwendet und nach Groß-/Kleinschreibung unterschieden.  
  
 **param**  
 Der Name des Parameters.  
  
 *value*  
 URL-Text, der dem Wert des Parameters entspricht, der verwendet wird.  
  
 **Hinweis:** Eine Liste der verfügbaren URL-Zugriffsparameter finden Sie unter [URL Access Parameter Reference](../reporting-services/url-access-parameter-reference.md). Beispiele für die Übergabe von Berichtsparametern mit der URL finden Sie unter [Pass a Report Parameter Within a URL](../reporting-services/pass-a-report-parameter-within-a-url.md).  
  
## Verwandte Aufgaben  
  
|Taskbeschreibungen|Links|  
|-----------------------|-----------|  
|Zugreifen auf Berichtserverelemente, z. B. Berichte, freigegebene Datenquellen und Ressourcen|[Zugreifen auf Berichtsserverelemente über den URL-Zugriff](../reporting-services/access-report-server-items-using-url-access.md)|  
|Übergeben von Berichtsparametern an einen Bericht|[Übergeben von Berichtsparametern innerhalb einer URL](../reporting-services/pass-a-report-parameter-within-a-url.md)|  
|Festlegen des Gebietsschemas der Berichtsparameter in der URL-Zugriffszeichenfolge, durch die die gebietsschemaspezifische Interpretation von Datumsangaben, Währungen usw. festgelegt wird|[Festlegen der Sprache für Berichtsparameter in einer URL](../reporting-services/set-the-language-for-report-parameters-in-a-url.md)|  
|Senden spezifischer Einstellungen für Renderingerweiterungen, durch die das Rendern des Berichts angepasst wird|[Angeben von Geräteinformationseinstellungen in einer URL](../reporting-services/specify-device-information-settings-in-a-url.md)|  
|Direktes Exportieren eines Berichts in ein Dateiformat, ohne ihn im Browser anzuzeigen|[Exportieren von Berichten über URL-Zugriff](../reporting-services/export-a-report-using-url-access.md)|  
|Öffnen eines Berichts und direktes Navigieren zur Position einer Zeichenfolge|[Suchen eines Berichts mithilfe von URL-Zugriff](../reporting-services/search-a-report-using-url-access.md)|  
|Rendern einer bestimmten Berichtsverlaufs-Momentaufnahme|[Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff](../reporting-services/render-a-report-history-snapshot-using-url-access.md)|  
  
## Siehe auch  
 [Übergeben von Berichtsparametern innerhalb einer URL](../reporting-services/pass-a-report-parameter-within-a-url.md)   
 [URL-Zugriffsparameterverweis](../reporting-services/url-access-parameter-reference.md)   
 [Integrieren von Reporting Services mit URL-Zugriff](../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Suchen, Anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS&#41;](../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  