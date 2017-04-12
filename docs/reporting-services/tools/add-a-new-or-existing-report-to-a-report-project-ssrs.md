---
title: "Hinzuf&#252;gen eines neuen oder vorhandenen Berichts zu einem Berichtsprojekt (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Berichte [Reporting Services], erstellen"
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Hinzuf&#252;gen eines neuen oder vorhandenen Berichts zu einem Berichtsprojekt (SSRS)
  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] können Sie einen neuen paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]-Bericht hinzufügen, indem Sie den Berichts-Assistenten nutzen oder dem Projekt einen neuen, leeren Bericht hinzufügen. Darüber hinaus können Sie einen vorhandenen Bericht hinzufügen. Nachdem Sie einen Bericht hinzugefügt haben, wird der Name des Berichts im Ordner **Berichte** Ihres Projekts aufgelistet.  
  
> [!NOTE]  
>  Um eine Vorschau eines Berichts mit vorhandenen Datenquellen einzusehen, müssen Sie über die Berechtigung zur Datenquelle von Ihrem Berichtserstellungsclient verfügen. Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen (Berichts-Generator und SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 Nachdem Sie einen Bericht hinzugefügt haben, können Sie Datenquellen und Datasets definieren und ein Berichtslayout entwerfen. Informationen zum Einstieg finden Sie unter [Erstellen eines einfachen Tabellenberichts &#40;SSRS-Lernprogramm&#41;](../../reporting-services/create-a-basic-table-report-ssrs-tutorial.md) oder [Tabellen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md).  
  
## So fügen Sie einen neuen Bericht über den Berichts-Assistenten hinzu  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner „Berichte“, und klicken Sie dann auf **Neuen Bericht hinzufügen**. Das Dialogfeld **Berichts-Assistent** wird geöffnet.  
  
     Der Assistent führt Sie durch die Erstellung einer Datenquelle, die Erstellung eines Datasets mit Abfrage, die Definition von Gruppen, das Festlegen eines Layouts, die Auswahl eines Stils, inklusive Farbe und Schriftart, und die Erstellung des Berichts. Die Schritte umfassen Folgendes:  
  
    -   **Wählen Sie eine Datenquelle aus.** Der erste Schritt beim Erstellen eines Berichts besteht im Definieren einer Datenquelle. Der Berichts-Assistent stellt eine Liste aller freigegebenen Datenquellen in dem Berichtsprojekt bereit und bietet außerdem die Option, eine neue Datenquelle zu erstellen.  
  
    -   **Entwerfen Sie eine Abfrage.** Im nächsten Schritt muss eine Abfrage entworfen werden. Sie können die Zeichenfolge der Abfrage eingeben, diese mithilfe des Abfrage-Designers erstellen oder eine Abfrage aus einem anderen Bericht importieren. Weitere Informationen über den Abfrage-Designer finden Sie unter [Reporting Services Query Designers](../Topic/Reporting%20Services%20Query%20Designers.md).  
  
    -   **Wählen Sie einen Berichtstyp aus.** Als Nächstes muss der gewünschte Berichtstyp ausgewählt werden. Sie können zwischen einem tabellarischen Bericht und einem Matrixbericht auswählen. Ein tabellarischer Bericht verfügt über eine feste Anzahl von Spalten. Ein Matrix- oder Kreuztabellenbericht verfügt über eine variable Anzahl von Spalten, die vom Ergebnis der Abfrage abhängt. In einem Kartenbericht werden Analysedaten vor einem geografischen Hintergrund dargestellt.  
  
    -   **Wählen Sie ein Format aus.** Im nächsten Schritt wird mithilfe einer Formatvorlage ein Format auf den Bericht angewendet. Wählen Sie eine Vorlage aus, um Formate wie Schriftart, Farbe und Rahmenart auf den Bericht anzuwenden. Der Berichts-Designer stellt sechs Formatvorlagen bereit: Schiefer, Wald, Geschäftlich, Fett, Ozean und Generisch. Darüber hinaus können Sie weitere Formatvorlagen hinzufügen.  
  
        > [!NOTE]  
        >  Sie können vorhandene Vorlagen ändern oder neue hinzufügen, indem Sie die Datei „StyleTemplates.xml“ im Ordner „\Programme\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\>“ bearbeiten, wobei \<lang> die Sprache ist, die Sie verwenden. Beispiel: Wenn Sie die englische Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verwenden, lautet der entsprechende Ordnername „EN“. Dieser Ordner befindet sich auf dem Computer, auf dem Berichts-Designer installiert ist. Von der Datei StyleTemplates.xml sind zwei Kopien verfügbar. Um die mithilfe des Berichts-Assistenten angewendeten Formate zu ändern, müssen Sie die Datei bearbeiten, die in dem für die verwendete Sprache erstellten Ordner gespeichert wurde.  
  
    -   **Geben Sie einen Namen für den Bericht ein.**  Der letzte Schritt besteht darin, einen Namen für den Bericht anzugeben und die Felder zu überprüfen, die in dem Bericht enthalten sein werden. Nach Abschluss aller Schritte wird der Bericht von Berichts-Designer erstellt und zum Berichtsserverprojekt hinzugefügt.  
  
## So fügen Sie einen neuen, leeren Bericht hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie in **Vorlagen**auf **Bericht**.  
  
3.  Klicken Sie auf **Hinzufügen**.  
  
     Dem Projekt wird ein neuer, leerer Bericht hinzugefügt und auf der Entwurfsoberfläche angezeigt.  
  
## So fügen Sie einen vorhandenen Bericht hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Hinzufügen**und dann auf  **Vorhandenes Element hinzufügen**.  
  
2.  Navigieren Sie zum Speicherort der RDL-Datei, markieren Sie die Datei, und klicken Sie dann auf **Hinzufügen**.  
  
     Der Bericht wird dem Projekt im Ordner **Berichte** hinzugefügt. Wenn Sie das Projekt schließen und erneut öffnen, sind die Berichte alphabetisch geordnet.  
  
## Siehe auch  
 [Reporting Services-Tutorials &#40;SSRS&#41;](../../reporting-services/reporting-services-tutorials-ssrs.md)  
  
  