---
title: DatabaseName-Element (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DatabaseName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.databasename
- http://schemas.microsoft.com/analysisservices/2003/engine#DatabaseName
- urn:schemas-microsoft-com:xml-analysis#DatabaseName
helpviewer_keywords:
- DatabaseName element
ms.assetid: 5cfd9a1f-da53-497a-b677-c51be4641bd0
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 999ffdf13c208c7bfd67118d1c692b1c1f70cf3b
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="databasename-element-xmla"></a>DatabaseName-Element (XMLA)
  Identifiziert die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] vom übergeordneten Element wiederhergestellt werden [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das **DatabaseName** -Element identifiziert die Datenbank, in die der **Restore** -Befehl eine Sicherungsdatei wiederherstellt. Wenn dieses Element nicht angegeben ist oder eine leere Zeichenfolge enthält, wird der Name der Datenbank verwendet, die in der Sicherungsdatei enthalten ist.  
  
 Wenn die Datenbank bereits auf einer Zielinstanz besteht, tritt ein Fehler auf, es sei denn, das **AllowOverwrite** -Element für den **Restore** -Befehl ist auf **True**gesetzt.  
  
## <a name="see-also"></a>Siehe auch  
 [AllowOverwrite-Element &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Datenbankeigenschaften &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  