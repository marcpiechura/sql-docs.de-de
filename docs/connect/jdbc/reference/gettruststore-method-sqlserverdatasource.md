---
title: GetTrustStore-Methode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 523ae02799c14c2b55d1bd6144758952930cf190
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="gettruststore-method-sqlserverdatasource"></a>getTrustStore-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Pfad (einschließlich Dateiname) zur trustStore-Zertifikatsdatei zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Zeichenfolge** , enthält den Pfad (einschließlich des Dateinamens) der TrustStore-Zertifikatsdatei, oder Null, wenn kein Wert festgelegt ist.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die TrustStore-Eigenschaft nicht festgelegt ist, die [GetTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) Methode gibt null zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
