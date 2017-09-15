---
title: Member-Element (XMLA) | Microsoft Docs
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
- Member Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Member
- microsoft.xml.analysis.member
- http://schemas.microsoft.com/analysisservices/2003/engine#Member
helpviewer_keywords:
- Member element
ms.assetid: 5cc33a1f-192e-4821-a4ef-9a5f2bb7a9f0
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 233938a1018a48dfaa8f7513fc88c65361b5f55a
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="member-element-xmla"></a>Member-Element (XMLA)
  Stellt ein einzelnes Element in einem übergeordneten [Elemente](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md) oder [Tupel](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Mitglieder](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md), [Tupel](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
|Untergeordnete Elemente|[Caption](../../../analysis-services/xmla/xml-elements-properties/caption-element-xmla.md), [DisplayInfo](../../../analysis-services/xmla/xml-elements-properties/displayinfo-element-xmla.md), [LName](../../../analysis-services/xmla/xml-elements-properties/lname-element-xmla.md), [LNum](../../../analysis-services/xmla/xml-elements-properties/lnum-element-xmla.md), [UName](../../../analysis-services/xmla/xml-elements-properties/uname-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Hierarchie|Erforderliches **String** -Attribut (nur für übergeordnete **Tuple** -Elemente). Der Name der Hierarchie, zu der das Element, das vom **Member** -Element dargestellt wird, gehört.|  
  
## <a name="remarks"></a>Hinweise  
 Das **Member** -Element enthält die Informationen, die benötigt werden, um ein Element innerhalb einer gegebenen Hierarchie zu identifizieren und anzuzeigen. Für übergeordnete **Members** -Elemente wird die Hierarchie bereits vom **Hierarchy** -Attribut des übergeordneten Elements angegeben. Für übergeordnete **Tuple** -Elemente wird die Hierarchie mithilfe des **Hierarchy** -Attributs des **Member** -Elements angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  