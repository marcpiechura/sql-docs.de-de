---
title: "Transformations-Editor f&#252;r Suche (Seite &#39;Allgemein&#39;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.lookuptransformation.general.f1"
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Transformations-Editor f&#252;r Suche (Seite &#39;Allgemein&#39;)
  Auf der Seite **Allgemein** des Dialogfelds Transformations-Editor für Suche können Sie den Cachemodus und den Verbindungstyp auswählen sowie angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
## enthalten  
 **Vollcache**  
 Das Verweisdataset wird generiert und in den Cache geladen, bevor die Transformation für Suche ausgeführt wird.  
  
 **Teilcache**  
 Das Verweisdataset wird während der Ausführung der Transformation für Suche generiert. Die Zeilen mit übereinstimmenden Einträgen im Verweisdataset und die Zeilen ohne übereinstimmende Einträge im Dataset werden in den Cache geladen.  
  
 **Kein Cache**  
 Das Verweisdataset wird während der Ausführung der Transformation für Suche generiert. Es werden keine Daten in den Zwischenspeicher geladen.  
  
 **Cacheverbindungs-Manager**  
 Die Transformation für Suche wird für die Verwendung eines Cacheverbindungs-Managers konfiguriert. Diese Option ist nur verfügbar, wenn die Option Vollcache ausgewählt ist.  
  
 **OLE DB-Verbindungs-Manager**  
 Die Transformation für Suche wird für die Verwendung eines OLE DB-Verbindungs-Managers konfiguriert.  
  
 **Angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen**  
 Wählen Sie eine Option für die Behandlung von Zeilen aus, die nicht mindestens einem Eintrag im Verweisdataset entsprechen.  
  
 Wenn Sie **Zeilen an Ausgabe nicht übereinstimmender Einträge umleiten**auswählen, werden die Zeilen an eine Ausgabe nicht übereinstimmender Einträge weitergeleitet und nicht als Fehler behandelt. Die Option **Fehler** auf der Seite **Fehlerausgabe** des Dialogfelds **Transformations-Editor für Suche** ist nicht verfügbar.  
  
 Wenn Sie im Listenfeld **Angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen** eine andere Option auswählen, werden die Zeilen als Fehler behandelt. In diesem Fall ist die Option **Fehler** auf der Seite **Fehlerausgabe** verfügbar.  
  
## Externe Ressourcen  
 Blogeintrag [Lookup cache modes](http://go.microsoft.com/fwlink/?LinkId=219518) (Suchcachemodi) auf blogs.msdn.com  
  
## Siehe auch  
 [Cacheverbindungs-Manager](../../../integration-services/data-flow/transformations/cache-connection-manager.md)   
 [Transformations-Editor für Suche &#40;Seite „Verbindung“&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Spalten“&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-columns-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Erweitert“&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-advanced-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Fehlerausgabe“&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-error-output-page.md)  
  
  