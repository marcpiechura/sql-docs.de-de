---
title: Reservierte Wörter in MDX | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- reserved words [MDX]
- Multidimensional Expressions [Analysis Services], reserved words
- MDX [Analysis Services], reserved words
ms.assetid: 8d059a8c-d578-4713-a615-2404d94ce32d
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a271c129cee1549d74732d879eed82f5169ca106
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-reserved-words"></a>Reservierte Wörter in MDX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die folgende Tabelle enthält Wörter, die für die Verwendung durch MDX (Multidimensional Expressions) reserviert sind. Sie sollten diese Wörter nicht als Teil eines Bezeichners, z. B. eines Cubenamens oder des Namens einer benutzerdefinierten Funktion, in MDX verwenden.  
  
|||||  
|-|-|-|-|  
|ABSOLUTE|DESC|LEAVES|SELF_BEFORE_AFTER|  
|ACTIONPARAMETERSET|DESCENDANTS|LEVEL|SESSION|  
|ADDCALCULATEDMEMBERS|DESCRIPTION|LEVELS|SET|  
|AFTER|DIMENSION|LINKMEMBER|SETTOARRAY|  
|AGGREGATE|DIMENSIONS|LINREGINTERCEPT|SETTOSTR|  
|ALL|DISTINCT|LINREGPOINT|SORT|  
|ALLMEMBERS|DISTINCTCOUNT|LINREGR2|STDDEV|  
|ANCESTOR|DRILLDOWNLEVEL|LINREGSLOPE|STDDEVP|  
|ANCESTORS|DRILLDOWNLEVELBOTTOM|LINREGVARIANCE|STDEV|  
|AND|DRILLDOWNLEVELTOP|LOOKUPCUBE|STDABWEICHUNGAUFFÜLL|  
|AS|DRILLDOWNMEMBER|MAX|STORAGE|  
|ASC|DRILLDOWNMEMBERBOTTOM|MEASURE|STRIPCALCULATEDMEMBERS|  
|ASCENDANTS|DRILLDOWNMEMBERTOP|MEDIAN|STRTOMEMBER|  
|AVERAGE|DRILLUPLEVEL|MEMBER|STRTOSET|  
|AXIS|DRILLUPMEMBER|MEMBERS|STRTOTUPLE|  
|BASC|DROP|MEMBERTOSTR|STRTOVAL|  
|BDESC|EMPTY|MIN|STRTOVALUE|  
|BEFORE|END|MTD|SUBSET|  
|BEFORE_AND_AFTER|ERROR|NAME|SUM|  
|BOTTOMCOUNT|EXCEPT|NAMETOSET|TAIL|  
|BOTTOMPERCENT|EXCLUDEEMPTY|NEST|THIS|  
|BOTTOMSUM|EXTRACT|NEXTMEMBER|TOGGLEDRILLSTATE|  
|BY|FALSE|NO_ALLOCATION|TOPCOUNT|  
|CACHE|FILTER|NO_PROPERTIES|TOPPERCENT|  
|CALCULATE|FIRSTCHILD|NON|TOPSUM|  
|CALCULATION|FIRSTSIBLING|NONEMPTYCROSSJOIN|TOTALS|  
|CALCULATIONCURRENTPASS|FOR|NOT_RELATED_TO_FACTS|trEE|  
|CALCULATIONPASSVALUE|FREEZE|NULL|TRUE|  
|CALCULATIONS|FROM|ON|TUPLETOSTR|  
|CALL|GENERATE|OPENINGPERIOD|TYPE|  
|CELL|GLOBAL|OR|UNION|  
|CELLFORMULASETLIST|GROUP|PAGES|UNIQUE|  
|CHAPTERS|GROUPING|PARALLELPERIOD|UNIQUENAME|  
|CHILDREN|HEAD|PARENT|UPDATE|  
|CLEAR|HIDDEN|PASS|USE|  
|CLOSINGPERIOD|HIERARCHIZE|PERIODSTODATE|USE_EQUAL_ALLOCATION|  
|COALESCEEMPTY|HIERARCHY|POST|USE_WEIGHTED_ALLOCATION|  
|COLUMN|IGNORE|PREDICT|USE_WEIGHTED_INCREMENT|  
|COLUMNS|IIF|PREVMEMBER|USERNAME|  
|CORRELATION|INCLUDEEMPTY|PROPERTIES|VALIDMEASURE|  
|COUNT|INDEX|PROPERTY|VALUE|  
|COUSIN|INTERSECT|QTD|VARIANZ|  
|COVARIANCE|IS|RANK|VARIANCE|  
|COVARIANCEN|ISANCESTOR|RECURSIVE|VARIANCEP|  
|CREATE|ISEMPTY|RELATIVE|VARIANZAUFFÜLL|  
|CREATEPROPERTYSET|ISGENERATION|ROLLUPCHILDREN|VISUAL|  
|CREATEVIRTUALDIMENSION|ISLEAF|ROOT|VISUALTOTALS|  
|CROSSJOIN|ISSIBLING|ROWS|WHERE|  
|CUBE|ITEM|SCOPE|mit|  
|CURRENT|LAG|SECTIONS|WTD|  
|CURRENTCUBE|LASTCHILD|SELECT|XOR|  
|CURRENTMEMBER|LASTPERIODS|SELF|YTD|  
|DEFAULT_MEMBER|LASTSIBLING|SELF_AND_AFTER||  
|DEFAULTMEMBER|LEAD|SELF_AND_BEFORE||  
  
## <a name="see-also"></a>Siehe auch  
 [Reservierte Schlüsselwörter &#40;MDX-Syntax&#41;](../mdx/reserved-keywords-mdx-syntax.md)   
 [MDX-Sprachreferenz & #40; MDX & #41;](../mdx/mdx-language-reference-mdx.md)  
  
  