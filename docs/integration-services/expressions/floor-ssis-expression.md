---
title: FLOOR (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3cef2f4fd7de76e5b07ae5e5f79cb1a5b868e4bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="floor-ssis-expression"></a>FLOOR (SSIS-Ausdruck)
  Gibt die größte ganze Zahl zurück, die kleiner oder gleich einem numerischen Ausdruck ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der numerische Datentyp des expression-Arguments. Das Ergebnis ist der ganzzahlige Teil des berechneten Werts mit dem gleichen Datentyp wie *numeric_expression*.  
  
## <a name="remarks"></a>Remarks  
 FLOOR gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird die FLOOR-Funktion auf positive und negative Werte und auf Null angewendet.  
  
```  
FLOOR(123.45)  
```  
  
 Gibt 123.00 zurück.  
  
```  
FLOOR(-123.45)  
```  
  
 Gibt -124.00 zurück.  
  
```  
FLOOR(0.00)  
```  
  
 Gibt 0.00 zurück.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [CEILING &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
