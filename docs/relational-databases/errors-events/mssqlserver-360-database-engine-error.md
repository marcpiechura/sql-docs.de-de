---
title: MSSQLSERVER_360 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5ad1e35bd6f05bc6c2e14bb4e267e672bfbf2274
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|360|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DML_UPDATE_SPARSE_AND_COLSET|  
|Meldungstext|Die Zielspaltenliste einer INSERT-, UPDATE- oder MERGE-Anweisung kann nicht sowohl eine Sparsespalte als auch den Spaltensatz enthalten, in dem sich die Sparsespalte befindet. Schreiben Sie die Anweisung um, sodass entweder nur die Sparsespalte oder nur der Spaltensatz enthalten ist.|  
  
## <a name="explanation"></a>Erklärung  
Ein Spaltensatz ist eine nicht typisierte XML-Darstellung, in der einige Spalten einer Tabelle zu einer strukturierten Ausgabe zusammengefasst werden. Es wurde versucht, sowohl den Spaltensatz als auch eine Spalte aus dem Spaltensatz zu ändern, sodass zwei Verweise auf die gleiche Spalte entstanden.  
  
## <a name="user-action"></a>Benutzeraktion  
Schreiben Sie die Anweisung um, sodass Verweise auf entweder die Spalte mit geringer Dichte oder auf den Spaltensatz enthalten sind. Schließen Sie jedoch keinesfalls beide in die Anweisung ein.  
  
