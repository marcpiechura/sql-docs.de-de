---
title: "Anwenden von Datenqualitätsregeln auf eine Datenquelle | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e7db6b5fc01c5d85b75ebdd6c78ba004a94135bf
ms.contentlocale: de-de
ms.lasthandoff: 08/03/2017

---
# <a name="apply-data-quality-rules-to-data-source"></a>Anwenden von Datenqualitätsregeln auf eine Datenquelle
  Sie können mit Data Quality Services (DQS) Daten im Paketdatenfluss korrigieren, indem Sie eine Verbindung zwischen der DQS-Bereinigungstransformation und der Datenquelle herstellen. Weitere Informationen zu DQS finden Sie unter [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Weitere Informationen zu der Transformation finden Sie unter [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Wenn Sie Daten mit der DQS-Bereinigungstransformation verarbeiten, wird ein Data Quality-Projekt auf dem Data Quality-Server erstellt. Das Projekt wird mit dem Data Quality Client verwaltet. Weitere Informationen finden Sie unter [Öffnen, Entsperren, Umbenennen, Löschen von Data Quality-Projekten](https://msdn.microsoft.com/library/hh510417.aspx).  
  
### <a name="to-correct-data-in-the-data-flow"></a>So korrigieren Sie Daten im Datenfluss  
  
1.  Erstellen eines Pakets.  
  
2.  Fügen Sie die DQS-Bereinigungstransformation hinzu, und konfigurieren Sie sie. Weitere Informationen finden Sie unter [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Verbinden Sie die DQS-Bereinigungstransformation mit einer Datenquelle.  
  
  