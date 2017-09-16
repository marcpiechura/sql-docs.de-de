---
title: RecordCount-Eigenschaft (ADO) | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords:
- RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 402a481ef7db03e2d7197eb02010a1c93b974570
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="recordcount-property-ado"></a>RecordCount-Eigenschaft (ADO)
Gibt die Anzahl der Datensätze in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **lange** -Wert, der die Anzahl der Datensätze in der **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **RecordCount** Eigenschaft, um herauszufinden, wie viele Datensätze werden einem **Recordset** Objekt. Die Eigenschaft gibt-1 zurück, wenn ADO die Anzahl der Datensätze bestimmt werden kann oder wenn der Anbieter oder Cursor-Typ nicht unterstützt **RecordCount**. Lesen der **RecordCount** Eigenschaft für ein geschlossenes **Recordset** verursacht einen Fehler.  
  
 Wenn die **Recordset** Objekt unterstützt die ungefähre Positionierung oder Lesezeichen??? d. h. **unterstützt (AdApproxPosition)** oder **unterstützt (zulässt)**bzw. zurückgeben **"true"**??? Dieser Wert wird die genaue Anzahl von Datensätzen in der **Recordset**, unabhängig davon, ob diese vollständig aufgefüllt wurde. Wenn die **Recordset** Objekt unterstützt keine ungefähre Positionierung, diese Eigenschaft möglicherweise erhebliche zahlreiche Ressourcen, da alle Datensätze werden abgerufen und gezählt, um eine genaue zurückzugeben werden **RecordCount** Wert.  
  
> [!NOTE]
>  In ADO-Versionen mit 2,8 und früher, ruft der SQLOLEDB-Anbieter alle Datensätze bei ein serverseitigen Cursor trotz der Tatsache verwendet wird, die zurückgegebenen **"true"** für beide **unterstützt (AdApproxPosition)** und **Unterstützt (zulässt)**.  
  
 Cursor-Datentyp, der die **Recordset** Objekt auswirkt, ob die Anzahl der Datensätze bestimmt werden kann. Die **RecordCount** Eigenschaft-1 für einen Vorwärtscursor; die tatsächliche Anzahl der für einen statischen oder Keysetcursor; und entweder-1 oder die tatsächliche Anzahl der für einen dynamischen Cursor, abhängig von der Datenquelle zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Filter- und RecordCount Eigenschaften Beispiel (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [Filter- und RecordCount Eigenschaften (VC++-Beispiel)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 ["PageCount"-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
