---
title: "LOWER (SSIS-Ausdruck) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Konvertieren von Großbuchstaben in Kleinbuchstaben"
  - "LOWER-Funktion"
  - "Großbuchstaben [Integration Services]"
  - "Kleinbuchstaben"
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LOWER (SSIS-Ausdruck)
  Gibt einen Zeichenausdruck zurück, nachdem Großbuchstaben in Kleinbuchstaben konvertiert wurden.  
  
## Syntax  
  
```  
  
LOWER(character_expression)  
```  
  
## Argumente  
 *character_expression*  
 Ein Zeichenausdruck zum Konvertieren in Kleinbuchstaben.  
  
## Ergebnistypen  
 DT_WSTR  
  
## Hinweise  
 LOWER kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression*-Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor LOWER ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [SQL Server Integration Services-Datentypen](../../integration-services/data-flow/integration-services-data-types.md) und [CAST &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 LOWER gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Zeichenfolgenliteral in Kleinbuchstaben konvertiert. Als Ergebnis wird "new york" zurückgegeben.  
  
```  
LOWER("New York")  
```  
  
 In diesem Beispiel werden alle Zeichen in der **Color** -Eingabespalte in Kleinbuchstaben konvertiert, außer dem ersten Zeichen. Wenn Color gleich YELLOW ist, wird als Ergebnis "Yellow" zurückgegeben. Weitere Informationen finden Sie unter [SUBSTRING &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 In diesem Beispiel wird der Wert in der **CityName** -Variablen in Kleinbuchstaben konvertiert.  
  
```  
LOWER(@CityName)  
```  
  
## Siehe auch  
 [UPPER &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/upper-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  