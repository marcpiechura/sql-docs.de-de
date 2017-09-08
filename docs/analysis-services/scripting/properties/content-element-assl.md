---
title: Content-Element (ASSL) | Microsoft Docs
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
- Content Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Content
helpviewer_keywords:
- Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c42c6d4af398dd08021b8b9e308155f2d23b11cb
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="content-element-assl"></a>Content-Element (ASSL)
  Beschreibt den Inhalt der Spalte in der [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Diese Enumeration beschreibt den Inhaltstyp, der von einer Miningstrukturspalte dargestellt wird, und kann je nach Bedarf durch Mining-Algorithmusanbieter erweitert werden. Weitere Informationen zu Inhaltstypen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](../../../analysis-services/data-mining/content-types-data-mining.md).  
  
 Die in der folgenden Tabelle aufgelisteten Werte werden i. d. R. von allen Mining-Algorithmusanbietern unterstützt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Diskrete*|Diese Spalte enthält diskrete Werte.|  
|*Fortlaufende*|Die Werte für die Spalte definieren einen fortlaufenden Satz von numerischen Daten.|  
|*Diskretisiert*|Die Werte in der Spalte stellen Gruppen (oder Buckets) von Werten dar, die von einer kontinuierlichen Spalte abgeleitet sind.|  
|*Sortiert*|Die Werte für die Spalte definieren eine geordnete Menge.|  
|*Zyklisch*|Die Werte für die Spalte definieren eine zyklisch geordnete Menge.|  
|*Wahrscheinlichkeit*|Die Werte für die Spalte geben eine Wahrscheinlichkeit für die Spalten in der [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md) Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*Variance*|Die Werte für die Spalte geben eine Varianz für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*StdDev*|Die Werte für die Spalte geben eine Standardabweichung für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*ProbabilityVariance*|Die Werte für die Spalte geben eine Varianz der Wahrscheinlichkeit für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*ProbabilityStdDev*|Die Werte für die Spalte geben eine Standardabweichung der Wahrscheinlichkeit für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*Unterstützung*|Die Werte für die Spalte geben Supportinformationen für die Spalte in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.<br /><br /> Hinweis: Diese Spalte wird als Teil des Standards für Mining-Algorithmusanbietern von Drittanbietern bereitgestellt. Von Microsoft bereitgestellte Algorithmen nehmen Sie keine dieser Spalte verwenden.|  
|*Key*|Die Spalte ist eine Schlüsselspalte.<br /><br /> Hinweis: Dieser Inhaltstyp gilt nur für Schlüsselspalten in dem die **IsKey** -Elementgruppe ist **"true"**.|  
  
 Zusätzlich zu diesen Standardwerten mining-Algorithmusanbietern enthaltene [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützen die Werte in der folgenden Tabelle.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Tastenkombination*|Diese Spalte ist eine Schlüsselspalte, und die Werte für diese Spalte stellen eine Folge von Ereignissen dar.<br /><br /> Hinweis: Dieser Inhaltstyp gilt nur für Schlüsselspalten in dem die **IsKey** -Elementgruppe ist **"true"**.|  
|*Die Schlüsselzeit*|Diese Spalte ist eine Schlüsselspalte, und die Werte für diese Spalte stellen Zeitmaßeinheiten dar.<br /><br /> Hinweis: Dieser Inhaltstyp gilt nur für Schlüsselspalten in dem die **IsKey** -Elementgruppe ist **"true"**.|  
|*Sequenz*|Die Werte für diese Spalte stellen eine Folge von Ereignissen dar.|  
|*Uhrzeit*|Die Werte für die Spalte stellen Zeitmaßeinheiten dar.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende **Content** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [ClassifiedColumns-Element &#40; ASSL &#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [Datenbankeigenschaften &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  