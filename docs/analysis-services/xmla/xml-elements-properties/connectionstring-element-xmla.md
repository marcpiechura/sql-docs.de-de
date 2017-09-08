---
title: ConnectionString-Element (XMLA) | Microsoft Docs
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
- ConnectionString Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6c6227db17c74b4c33d07abfcd809ae01bc3a9a
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="connectionstring-element-xmla"></a>ConnectionString-Element (XMLA)
  Enthält eine Verbindungszeichenfolge, die vom übergeordneten Element verwendeten [Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) oder [Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Cardinality|Finden Sie in der folgenden Tabelle aus.|  
  
|Vorgänger oder übergeordnetes Element|Cardinality|  
|------------------------|-----------------|  
|[Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|[Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [Quelle](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Für **Location** -Elemente enthält das **ConnectionString** -Element die Verbindungszeichenfolge, die vom **Restore** - oder **Synchronize** -Befehl entweder zum Aktualisieren einer lokalen Datenquelle oder zum Verbinden mit einer Remoteinstanz verwendet wird.  
  
 Für **Source** -Elemente enthält das **ConnectionString** -Element die Verbindungszeichenfolge, die vom **Synchronize** -Befehl zum Verbinden mit der Quellinstanz verwendet wird.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen, und Synchronisieren von Datenbanken &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Restore-Element &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronisieren Sie-Element &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Datenbankeigenschaften &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  