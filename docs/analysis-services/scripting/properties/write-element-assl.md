---
title: Write-Element (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Write Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Write element
ms.assetid: d8f7a367-d7bf-4b40-acb4-19c8bc8c6c20
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5f72e90c9975f0cf0dd1d16eeaabdb6eb378781
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="write-element-assl"></a>Write-Element (ASSL)
  Bestimmt, ob Daten oder Metadaten für geschrieben werden, kann eine bestimmte [CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md) oder [Berechtigung](../../../analysis-services/scripting/data-type/permission-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Write>...</Write>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubeDimensionPermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [Berechtigung](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Keine*|Das übergeordnete Objekt lässt keinen Zugriff auf Daten oder Metadaten zu.|  
|*Zulässig*|Das übergeordnete Objekt lässt Schreibzugriff auf Daten und Metadaten zu.|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen **schreiben** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.CubeDimensionPermission> und <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension-Element &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Datenbankeigenschaften &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  