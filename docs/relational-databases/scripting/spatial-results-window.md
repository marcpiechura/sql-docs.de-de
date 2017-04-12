---
title: "Fenster &quot;R&#228;umliche Ergebnisse&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Fenster &quot;R&#228;umliche Ergebnisse&quot;
  Im Fenster **Räumliche Ergebnisse** werden visuelle Zuordnungstools zum Anzeigen räumlicher Daten bereitgestellt. Zum Anzeigen von Ergebnissen für räumliche Daten müssen die Abfrageergebnisse eine räumliche Spalte mit Geometrie- oder Geografiedaten enthalten.  
  
> [!NOTE]  
>  Das Fenster **Räumliche Ergebnisse** ist nur verfügbar, wenn die Ergebnisse im Fenster **Ergebnisse** in ein Raster zurückgegeben werden. Wenn Sie angeben, dass die Ergebnisse als Text zurückgegeben werden, ist dieses Fenster nicht verfügbar.  
  
## Optionen  
 **Räumliche Spalte auswählen**  
 Geben Sie die räumliche Spalte an, die Sie in den Abfrageergebnissen in den räumlichen Spalten anzeigen möchten. Es kann nur jeweils eine Spalte ausgewählt werden.  
  
 **Bezeichnungsspalte auswählen**  
 Geben Sie die nicht räumliche Spalte in den Spalten an, die in den Abfrageergebnissen zurückgegeben wurden, um die räumlichen Daten zu beschriften. Es kann nur jeweils eine Spalte ausgewählt werden.  
  
 Diese Option ist nicht verfügbar, wenn in einer Abfrage nur Instanzen zurückgegeben werden.  
  
 **Projektion auswählen**  
 Sie können Geografiedaten in einer von vier Projektionen anzeigen: Equirectangular, Mercator, Robinson oder Bonne.  
  
 Diese Option ist für Geometriedaten nicht verfügbar.  
  
 **Zoom**  
 Stellen Sie die Zuordnungsanzeige auf einer exponentiellen Skala ein.  
  
 **Gitternetzlinien anzeigen**  
 Sie können Koordinatengitternetzlinien aktivieren oder deaktivieren.  
  
 Bei polygonen Formen wird die Bezeichnung nur angezeigt, wenn die Form groß genug ist, um den Bezeichnungstext aufzunehmen. Um Bezeichnungen für kleine Formen anzuzeigen, passen Sie den Zoom an.  
  
> [!NOTE]  
>  Punktinstanzen können nicht bezeichnet werden.  
  
## Siehe auch  
 [Anzeigen räumlicher Daten im Objekt-Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Abfrage-Editor des Datenbankmoduls &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  