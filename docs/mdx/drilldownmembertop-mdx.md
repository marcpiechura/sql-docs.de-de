---
title: DrilldownMemberTop (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DRILLDOWNMEMBERTOP
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownMemberTop function
ms.assetid: b6575544-1fd3-4fa1-aa2e-272d307c7750
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: da7f8a1c315d9ff3eb60c69e88726b521a59d17d
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="drilldownmembertop-mdx"></a>DrilldownMemberTop (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt einen Drilldown bei Elementen in einer angegebenen Menge aus, die in einer angegebenen zweiten Menge vorhanden sind, wobei das Resultset auf eine angegebene Anzahl von Elementen beschränkt wird. Alternativ können Sie diese Funktion einen Drilldown für eine Menge von Tupeln unter Verwendung der ersten tupelhierarchie oder der optional angegebenen Hierarchie.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillDownMemberTop(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expression>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *Hierarchie*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Rekursive*  
 Ein Schlüsselwort, das einen rekursiven Vergleich von Mengen angibt.  
  
 *Include_Calc_Members*  
 Ein Schlüsselwort, durch das berechnete Elemente in Drilldownergebnisse eingeschlossen werden können.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben wird, die **DrilldownMemberTop** Funktion sortiert in absteigender Reihenfolge der untergeordneten Elemente jedes Elements in der ersten Menge entsprechend dem Wert des numerischen Ausdrucks, ausgewertet über der Menge der untergeordneten Elemente. Wenn kein numerischer Wert angegeben wird, sortiert die Funktion die untergeordneten Elemente jedes Elements in der ersten Menge absteigend nach den Werten der durch die Menge der untergeordneten Elemente dargestellten Zellen, bestimmt durch den Abfragekontext. Dieses Verhalten ähnelt dem der TopCount-Funktion und der Head (MDX)-Funktion, die eine Menge untergeordneter Elemente in natürlicher Reihenfolge ohne Sortierung zurückgeben.  
  
 Nach dem Sortieren der **DrilldownMemberTop** -Funktion eine Menge, die die übergeordneten Elemente und die Anzahl der untergeordneten Elemente im angegebenen enthält zurück *Count* mit dem höchsten Wert, der in beiden Mengen enthaltenen.  
  
 Wenn **REKURSIVE** angegeben wird, sortiert die Funktion die erste Menge wie oben beschrieben, und vergleicht dann rekursiv die Elemente der ersten Menge in einer Hierarchie mit der zweiten Menge organisiert*.* Die Funktion ruft die Anzahl die oberste untergeordneten Elemente für jedes Element in der ersten Menge, die auch in der zweiten Menge vorhanden ist.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
 Die **DrilldownMemberTop** Funktion ist vergleichbar mit der [DrilldownMember](../mdx/drilldownmember-mdx.md) funktionieren jedoch INSTEAD OF including alle untergeordneten Elemente für jedes Element in der ersten Menge, die auch ist vorhanden, in der zweiten Menge der **DrilldownMemberTop** Funktion gibt die Anzahl die oberste untergeordneten Elemente für jedes Element zurück.  
  
 Abfrage der XMLA-Eigenschaft MdpropMdxDrillFunctions können Sie den Grad der Unterstützung, die der Server die drillingfunktionen bereitgestellt; finden Sie unter [unterstützten XMLA-Eigenschaften &#40; XMLA &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) für Details.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Drilldown in die Bekleidungskategorie durchgeführt, damit die drei Unterkategorien von Bekleidung mit den meisten gelieferten Bestellungen zurückgegeben werden.  
  
```  
SELECT DrilldownMemberTop   ({[Product].[Product Categories].[All Products],        
[Product].[Product Categories].[Category].Bikes,        
[Product].[Product Categories].[Category].Clothing},     
{[Product].[Product Categories].[Category].Clothing},     
3,     
[Measures].[Reseller Order Quantity])     
ON 0     
FROM [Adventure Works]     
WHERE [Measures].[Reseller Order Quantity]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
