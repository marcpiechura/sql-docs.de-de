---
title: "Quellen-Editor f&#252;r SAP BW (Seite Verbindungs-Manager) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sapbwsource.connection.f1"
ms.assetid: 2a6dc531-85ca-43c5-a65f-3ad3f7d537c4
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Quellen-Editor f&#252;r SAP BW (Seite Verbindungs-Manager)
  Auf der Seite **Verbindungs-Manager** des Dialogfelds **Quellen-Editor für SAP BW** können Sie den SAP BW-Verbindungs-Manager für die SAP BW-Quelle auswählen. Auf dieser Seite wählen Sie außerdem den Ausführungsmodus und die Parameter aus, mit denen Sie die Daten aus dem SAP NetWeaver BW-System extrahieren.  
  
 Weitere Informationen zur SAP BW-Quellkomponente von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Quelle](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
 **So öffnen Sie die Seite "Verbindungs-Manager"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem die SAP BW-Quelle enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die SAP BW-Quelle.  
  
3.  Klicken Sie im **Quellen-Editor für SAP BW**auf **Verbindungs-Manager** , um die Seite **Verbindungs-Manager** des Editors zu öffnen.  
  
## Statische Optionen  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration der Quelle erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 **SAP BW-Verbindungs-Manager**  
 Wählen Sie einen vorhandenen Verbindungs-Manager aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu** klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **SAP BW-Verbindungs-Manager** einen neuen Verbindungs-Manager.  
  
 Weitere Informationen zu diesem Dialogfeld finden Sie unter [SAP BW Connection Manager Editor](../../integration-services/connection-manager/sap-bw-connection-manager-editor.md).  
  
 **OHS-Ziel**  
 Wählen Sie das OHS (Open Hub Service)-Ziel aus, das zum Extrahieren von Daten aus der Quelle verwendet werden soll.  
  
 **Ausführungsmodus**  
 Gibt die Methode zum Extrahieren von Daten aus der Quelle an.  
  
|Option|Description|  
|------------|-----------------|  
|**P - Prozesskette auslösen**|Lösen Sie eine Prozesskette aus. In diesem Fall wird der Extrahierungsprozess vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket gestartet.|  
|**W - Benachrichtigung abwarten**|Warten Sie auf die Benachrichtigung vom SAP NetWeaver BW-System, um mit dem Extrahieren von Daten zu beginnen. In diesem Fall wird der Extrahierungsprozess vom SAP NetWeaver BW-System gestartet.|  
|**E - Nur extrahieren**|Rufen Sie die Daten ab, die einer bestimmten Anforderungs-ID zugeordnet sind. In diesem Fall hat das SAP NetWeaver BW-System die Daten bereits in eine interne Tabelle extrahiert, und die Daten werden gerade vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket gelesen.|  
  
 **Vorschau**  
 Öffnen Sie das Dialogfeld **Vorschau**, in dem Sie eine Vorschau der Ergebnisse anzeigen können. Weitere Informationen finden Sie unter [Preview](../../integration-services/data-flow/preview.md).  
  
> [!IMPORTANT]  
>  Die Daten werden tatsächlich mithilfe der Option **Vorschau** extrahiert, die im Quellen-Editor für SAP BW auf der Seite **Verbindungs-Manager** verfügbar ist. Wenn Sie SAP NetWeaver BW so konfiguriert haben, dass nur Daten extrahiert werden, die sich seit der letzten Extrahierung geändert haben, schließen Sie die in der Vorschau angezeigten Daten durch Auswahl von **Vorschau** aus der nachfolgenden Extrahierung aus.  
  
 Wenn Sie auf **Vorschau**klicken, wird gleichzeitig das Dialogfeld **Anforderungsprotokoll** geöffnet. Sie können dieses Dialogfeld verwenden, um die Ereignisse anzuzeigen, die protokolliert werden, während Beispieldaten vom SAP NetWeaver BW-System angefordert werden. Weitere Informationen finden Sie unter [Request Log](../../integration-services/data-flow/request-log.md).  
  
## Optionen für den dynamischen Ausführungsmodus  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration der Quelle erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
### Ausführungsmodus = P - Prozesskette auslösen  
  
#### Optionen für "RFC-Ziel"  
 Diese Werte müssen nicht im Voraus bekannt sein und eingegeben werden. Verwenden Sie die Schaltfläche **Suchen** , um das entsprechende RFC-Ziel zu suchen und auszuwählen. Nachdem Sie ein RFC-Ziel ausgewählt haben, werden die entsprechenden Werte für diese Optionen von der Komponente eingegeben.  
  
 **Gatewayhost**  
 Geben Sie den Servernamen oder die IP-Adresse des Gatewayhosts ein. Normalerweise ist der Name oder die IP-Adresse identisch mit dem SAP-Anwendungsserver.  
  
 **Gatewaydienst**  
 Geben Sie den Namen des Gatewaydiensts im Format **sapgwNN** ein, wobei **NN** der Systemnummer entspricht.  
  
 **Programm-ID**  
 Geben Sie die Programm-ID ein, die dem RFC-Ziel zugeordnet ist.  
  
 **Suchen**  
 Suchen Sie das RFC-Ziel mithilfe des Dialogfelds **RFC-Ziel suchen**. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up RFC Destination](../../integration-services/data-flow/look-up-rfc-destination.md).  
  
#### Optionen für "Prozesskette"  
 Diese Werte müssen nicht im Voraus bekannt sein und eingegeben werden. Verwenden Sie die Schaltfläche **Suchen** , um die entsprechende Prozesskette zu suchen und auszuwählen. Nachdem Sie eine Prozesskette ausgewählt haben, wird der entsprechende Wert für die Option von der Komponente eingegeben.  
  
 **Prozesskette**  
 Geben Sie den Namen der Prozesskette ein, die von der Quelle ausgelöst werden soll.  
  
 **Suchen**  
 Suchen Sie die Prozesskette mithilfe des Dialogfelds **Prozesskette suchen**. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up Process Chain](../../integration-services/data-flow/look-up-process-chain.md).  
  
### Ausführungsmodus = W - Benachrichtigung abwarten  
  
#### Optionen für "RFC-Ziel"  
 Diese Werte müssen nicht im Voraus bekannt sein und eingegeben werden. Verwenden Sie die Schaltfläche **Suchen** , um das entsprechende RFC-Ziel zu suchen und auszuwählen. Nachdem Sie ein RFC-Ziel ausgewählt haben, werden die entsprechenden Werte für die Optionen von der Komponente eingegeben.  
  
 **Gatewayhost**  
 Geben Sie den Servernamen oder die IP-Adresse des Gatewayhosts ein. Normalerweise ist der Name oder die IP-Adresse identisch mit dem SAP-Anwendungsserver.  
  
 **Gatewaydienst**  
 Geben Sie den Namen des Gatewaydiensts im Format **sapgwNN** ein, wobei **NN** der Systemnummer entspricht.  
  
 **Programm-ID**  
 Geben Sie die Programm-ID ein, die dem RFC-Ziel zugeordnet ist.  
  
 **Suchen**  
 Suchen Sie das RFC-Ziel mithilfe des Dialogfelds **RFC-Ziel suchen**. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up RFC Destination](../../integration-services/data-flow/look-up-rfc-destination.md).  
  
### Ausführungsmodus = E - Nur extrahieren  
 **Anforderungs-ID**  
 Geben Sie die Anforderungs-ID ein, die der Extrahierung zugeordnet ist.  
  
## Siehe auch  
 [Quellen-Editor für SAP BW &#40;Seite Spalten&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Quellen-Editor für SAP BW &#40;Seite Fehlerausgabe&#41;](../../integration-services/data-flow/sap-bw-source-editor-error-output-page.md)   
 [Quellen-Editor für SAP BW &#40;Seite Erweitert&#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [F1-Hilfe zum Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  