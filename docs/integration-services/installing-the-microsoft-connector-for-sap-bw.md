---
title: "Installieren von Microsoft Connector f&#252;r SAP BW | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Installieren von Microsoft Connector f&#252;r SAP BW
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW für SQL Server 2016 ist eine Komponente des SQL Server 2016 Feature Pack. Zum Installieren des Connectors für SAP BW und der zugehörigen Dokumentation laden Sie das Installationsprogramm von der [SQL Server 2016 Feature Pack-Website](http://go.microsoft.com/fwlink/?LinkId=746297) herunter, und führen Sie es aus.  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector für SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
> [!IMPORTANT]  
>  Das Extrahieren von Daten aus SAP NetWeaver BW erfordert zusätzliche SAP-Lizenzen. Stimmen Sie diese Anforderungen mit SAP ab.  
  
## Erforderliche SAP-Dateien  
 Wenn Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW verwenden möchten, müssen Sie die SAP-Front-End-Software (SAP GUI) nicht auf dem lokalen Computer installieren.  
  
 Sie müssen jedoch die SAP .NET-Connector-Datei librfc32.dll im Ordner Windows in den Unterordner system kopieren. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\system32**.)  
  
## Überlegungen für 64-Bit-Computer  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW bietet uneingeschränkte Unterstützung der 64-Bit-Version von [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Auf einem 64-Bit-Computer gelten für [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector für SAP BW folgende zusätzliche Anforderungen:  
  
-   Wenn Sie Pakete im 64-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die 64-Bit-Version der SAP GUI-Datei „librfc32.dll“ in den Unterordner **system32** des Windows-Ordners. (In der Regel ist der Speicherort dieser Datei **C:\Windows\system32**.)  
  
-   Wenn Sie Pakete im 32-Bit-Modus auf einem 64-Bit-Windows-Betriebssystem ausführen möchten, kopieren Sie die SAP GUI-Datei „librfc32.dll“ in den Unterordner **SysWow64** des Windows-Ordners. (In der Regel ist der Speicherort dieses Ordners **C:\Windows\SysWow64**.)  
  
  