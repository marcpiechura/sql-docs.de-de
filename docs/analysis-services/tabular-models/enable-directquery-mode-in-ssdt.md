---
title: Aktivieren des DirectQuery-Modus in SSDT | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1d2a1ced9638a48dc02729c0f224b883974a7dde
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="enable-directquery-mode-in-ssdt"></a>Aktivieren des DirectQuery-Modus in SSDT
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In diesem Abschnitt wird die Aktivierung des DirectQuery-Modus für ein tabellarisches Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]erklärt.  
  
Wenn Sie den DirectQuery-Modus für ein tabellarisches Modell aktivieren, entwerfen Sie in SSDT:
-   Funktionen, die mit dem DirectQuery-Modus inkompatibel sind, werden deaktiviert.  
-   Das vorhandene Modell wird überprüft. Warnungen werden angezeigt, wenn Funktionen mit dem DirectQuery-Modus inkompatibel sind.  
-   Wenn die Daten bereits vor der Aktivierung des DirectQuery-Modus importiert wurden, wird der Cache des Arbeitsmodells geleert.  
  
### <a name="enable-directquery"></a>Aktivieren von DirectQuery  
  
Ändern Sie in SSDT im Bereich **Eigenschaften** für die Datei **Model.bim** die Eigenschaft **DirectQuery-Modus**auf **On**.  

![Aktivieren des DirectQuery-Modus in SSDT](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
Wenn Ihr Modell bereits eine Verbindung zu einer Datenquelle sowie mit vorhandene Daten hergestellt hat, werden Sie aufgefordert, Datenbankanmeldeinformationen zur Verbindung mit der relationalen Datenbank einzugeben. Bereits vorhandene Daten innerhalb des Modells werden aus dem In-Memory-Cache entfernt.  
  
Wenn Ihr Modell vor der Aktivierung des DirectQuery-Modus teilweise oder zu 100 % abgeschlossen ist, erhalten Sie möglicherweise Fehler in Bezug auf nicht kompatible Funktionen. Öffnen Sie in Visual Studio die **Fehlerliste** , und beheben Sie alle Probleme, durch die verhindert werden würde, dass das Modell in den DirectQuery-Modus wechselt.  


### <a name="whats-next"></a>Wie geht es weiter? 
Sie können nun Daten mit dem Tabellenimport-Assistenten zum Abrufen von Metadaten für das Modell importieren. Sie erhalten keine Datenzeilen, aber Tabellen, Spalten und Beziehungen als Grundlage für Ihr Modell. 

Sie können für jede Tabelle eine Beispielpartition erstellen und Beispieldaten hinzufügen, damit Sie Modellverhalten bei der Erstellung überprüfen können. Beispieldaten, die Sie hinzufügen, werden in **Analysieren für Excel** oder in anderen Clienttools verwendet, die eine Verbindung mit der Arbeitsbereichsdatenbank herstellen können. Einzelheiten finden Sie unter [Hinzufügen von Beispieldaten zu einem DirectQuery-Modell im Entwurfsmodus](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) .  
  
> [!TIP]  
    >  Selbst im DirectQuery-Modus bei einem leeren Modell können Sie sich immer für jede Tabelle ein kleines eingebautes Rowset anzeigen lassen. Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf **Tabelle** > **Tabelleneigenschaften** , um das Dataset mit 50 Zeilen anzuzeigen.  
  
  
## <a name="see-also"></a>Siehe auch  
[Aktivieren des DirectQuery-Modus in SSMS](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Hinzufügen von Beispieldaten zu einem DirectQuery-Modell im Entwurfsmodus](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  
