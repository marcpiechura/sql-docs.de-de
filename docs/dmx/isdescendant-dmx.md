---
title: IsDescendant (DMX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsDescendant
dev_langs:
- DMX
helpviewer_keywords:
- IsDescendant function
ms.assetid: d9fe7446-edb5-487b-8ea6-c9efaccf6d90
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4a1e7959a303b768851784af0ab9c88abd257674
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt an, ob der aktuelle Knoten ein untergeordneter Knoten des angegebenen Knotens ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein boolescher Typ.  
  
## <a name="remarks"></a>Hinweise  
 **IsDescendant** dient lediglich [SELECT FROM &#60; Modell &#62;. Inhalt &#40; DMX &#41; ](../dmx/select-from-model-content-dmx.md) und [SELECT FROM &#60; Modell &#62;. DIMENSION_CONTENT &#40; DMX &#41; ](../dmx/select-from-model-dimension-content-dmx.md) Abfragen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Fälle zurückgegeben, die Nachfolger des Knotens sind, der in der IsDescendant-Funktion angegeben ist.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40; DMX &#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
