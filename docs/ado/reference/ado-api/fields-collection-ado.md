---
title: Fields-Auflistung (ADO) | Microsoft Docs
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
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 22fa67aeac9f4296133af93562299e4f5160d996
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="fields-collection-ado"></a>Fields-Auflistung (ADO)
Enthält alle der [Feld](../../../ado/reference/ado-api/field-object.md) Objekte von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oder [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Recordset** Objekt verfügt über eine **Felder** Auflistung bestehend aus **Feld** Objekte. Jede **Feld** -Objekt entspricht einer Spalte in der **Recordset**. Sie können Auffüllen der **Felder** Auflistung vor dem Öffnen der **Recordset** durch Aufrufen der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode für die Auflistung.  
  
> [!NOTE]
>  Finden Sie unter der **Feld** Objektthema für eine ausführlichere Erläuterung zur Verwendung **Feld** Objekte.  
  
 Die **Felder** Auflistung verfügt über ein [Anfügen](../../../ado/reference/ado-api/append-method-ado.md) -Methode, die vorläufig erstellt und fügt eine **Feld** Objekt der Auflistung und ein **aktualisieren**-Methode, die hinzugefügten oder gelöschten schließt ab.  
  
 Ein **Datensatz** Objekt verfügt über zwei spezielle Felder, die mit indizierbar [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) Konstanten. Eine Konstante greift auf ein Feld für den Standarddatenstrom der **Datensatz**, und die andere greift auf ein Feld, enthält die absolute URL-Zeichenfolge für die **Datensatz**.  
  
 Bestimmter Anbieter (z. B. die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) möglicherweise Auffüllen der **Felder** Auflistung mit einer Teilmenge der verfügbaren Felder für die **Datensatz** oder **Recordset**. Andere Felder werden der Auflistung nicht hinzugefügt werden, bis sie zunächst anhand des Namens verwiesen oder durch Ihren Code indiziert werden.  
  
 Wenn Sie versuchen, ein nicht vorhandenes Feld Namen verweisen, einen neuen **Feld** Objekt angefügt wird die **Felder** Auflistung mit einer [Status](../../../ado/reference/ado-api/status-property-ado-field.md) von ** AdFieldPendingInsert**. Beim Aufruf [Update](../../../ado/reference/ado-api/update-method.md), ADO erstellen ein neues Feld in der Datenquelle ab, wenn von Ihrem Anbieter zugelassen.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Sammlungseigenschaften Felder, Methoden und Ereignisse](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)