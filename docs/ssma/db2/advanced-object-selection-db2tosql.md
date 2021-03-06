---
title: Erweiterte Objektauswahl (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ca098c15-c343-4d7d-a284-c2fc405eb991
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dc3ef79d40d412289dadcd64cb5370f69818d16a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="advanced-object-selection-db2tosql"></a>Erweiterte Objektauswahl (DB2ToSQL)
Die **Objektabschnitt erweiterte** Dialogfeld können Sie die Datenbankobjekte mithilfe von Zeichenfolgen und Teilzeichenfolgen in Objektnamen, Filtern und dann zu aktivieren oder deaktivieren diese Objekte. SSMA führt konvertieren und Migrieren von Vorgängen für ausgewählte Objekte.  
  
Um auf dieses Dialogfeld zuzugreifen, eine Metadaten-Explorer mit der rechten Maustaste, und wählen Sie dann **Objektauswahl erweiterte**.  
  
Wenn Sie das Dialogfeld zum ersten Mal öffnen, klicken Sie auf **Unterkategorien Elemente anzeigen** um alle Objekte anzuzeigen, die Metadaten, die in das Projekt geladen haben. Sie können Zeichenfolgen zum Filtern der Elemente anschließend eingeben. Geben Sie beispielsweise die Zeichenfolge "Company" werden alle Elemente mit Namen angezeigt, die diese Zeichenfolge enthalten.  
  
Bevor Sie dieses Dialogfeld verwenden, empfiehlt es sich, erzwingen von SSMA alle Metadaten durch Konvertieren von Schemas oder speichern das Projekt geladen.  
  
## <a name="options"></a>enthalten  
**Überprüfen Sie alle Elemente**  
Fügt ein Häkchen neben allen Elementen. Diese Elemente werden sofort in den Metadaten-Explorer ausgewählt werden.  
  
**Deaktivieren Sie alle Elemente**  
Entfernt das Häkchen neben allen Elementen. Diese Elemente werden in den Metadaten-Explorer sofort gelöscht werden.  
  
**Der Listenansichtsmodus**  
Zeigt gefilterte Elemente in einer Liste.  
  
**Tabelle-Ansichtsmodus**  
Zeigt gefilterte Elemente in einer Tabelle.  
  
**Nur die geladenen Elemente angezeigt**  
Schaltet die Anzeige der Kategorien oder Elemente an. Wenn diese Schaltfläche ausgewählt wird, zeigt SSMA alle Elemente, die die Filterkriterien, und solche, die zuvor geladene entsprechen. Wenn diese Schaltfläche nicht aktiviert ist, zeigt SSMA die Kategorie-Ordner.  
  
**Filter**  
Geben Sie die Zeichenfolge, die Sie verwenden, um Elemente zu filtern möchten. Geben Sie beispielsweise zum Suchen aller verfügbaren Elemente beziehen, die Zeichenfolge enthalten "ID" in der Elementname, die Zeichenfolge "ID" in der **Filter** Feld.  
  
Wenn Elemente den Filterkriterien entsprechen, werden der Kategorien oder die Elemente angezeigt, während der Eingabe der Zeichenfolge. Um die übereinstimmenden Elemente angezeigt werden, wird empfohlen, dass Sie auf die **nur geladen Elemente angezeigt** Schaltfläche.  
  
**Filter löschen**  
Löscht die **Filter** Feld.  
  
