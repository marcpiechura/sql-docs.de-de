---
title: GetSQLXML-Methode (Int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a1b32d3a-d7c9-4086-ae2b-fc1da96949b1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d243e355f90741c294957484caab29f23a8c1341
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="getsqlxml-method-int"></a>getSQLXML-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters als Berücksichtigung des parameterindexes SQLXML-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.sql.SQLXML getSQLXML(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *parameterIndex*  
  
 Ein **Int** , der die Indexnummer des Parameters angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese GetSQLXML-Methode wird von der GetSQLXML-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [GetSQLXML-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
