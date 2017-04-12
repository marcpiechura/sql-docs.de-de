---
title: "YEAR (SSIS-Ausdruck) | Microsoft Docs"
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
  - "Datumsangaben [Integration Services], YEAR"
  - "YEAR-Funktion"
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# YEAR (SSIS-Ausdruck)
  Gibt eine ganze Zahl zurück, die den datepart-Wert für die Jahresangabe in einem Datum darstellt.  
  
## Syntax  
  
```  
  
YEAR(date)  
```  
  
## Argumente  
 *Datum*  
 Ein Datum in einem beliebigen Datumsformat.  
  
## Ergebnistypen  
 DT_I4  
  
## Hinweise  
 YEAR gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Ein Datumsliteral muss explizit in einen der date-Datentypen umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Der Ausdruck wird nicht überprüft, wenn ein Datumsliteral explizit in einen der folgenden Datumsdatentypen umgewandelt wird: DT_DBTIMESTAMPOFFSET oder DT_DBTIMESTAMP2.  
  
 Die YEAR-Funktion entspricht bezüglich der Verwendung der DATEPART("Year", date)-Funktion, ist jedoch schneller.  
  
## Beispiele für Ausdrücke  
 In diesem Beispiel wird die Jahreszahl eines Datumsliterals zurückgegeben. Falls das Datum das Format mm/dd/yyyy aufweist, wird "2002" zurückgegeben.  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die das Jahr in der **ModifiedDate** -Spalte darstellt.  
  
```  
YEAR(ModifiedDate)  
```  
  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die das Jahr des aktuellen Datums darstellt.  
  
```  
YEAR(GETDATE())  
```  
  
## Siehe auch  
 [DATEADD &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  