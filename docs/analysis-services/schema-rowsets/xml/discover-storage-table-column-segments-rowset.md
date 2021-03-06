---
title: DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd9c481ea5d34dcf4b8dd478000c564ff6c996ab
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bietet Informationen zu den auf Spalten- und Segmentebene Speichertabellen, die von einer ausgeführten tabellarischen Analysis Services-Datenbank verwendet oder [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Modus. Dieses Rowset wird hauptsächlich für Problembehandlung und Analyse verwendet.  
  
 **Gilt für:** tabellarische Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** Rowset enthält die folgenden Spalten.  
  
|**Spaltenname**|**Typindikator**|**Einschränkung**|**Beschreibung**|  
|---------------------|------------------------|---------------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|ja|Gibt die tabellarische Datenbank an.<br /><br /> Die **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** Rowset kann mithilfe dieser Spalte eingeschränkt werden. Wenn die aktuelle Datenbank ausgelassen wird verwendet.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|ja|Der Name des Modells.<br /><br /> Das **DISCOVER_STORAGE_TABLES** -Rowset kann mithilfe dieser Spalte eingeschränkt werden.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|ja|Der Name der Measuregruppe.|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|ja|Der Name der Partition.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Der Name der Dimension.|  
|**TABLE_ID**|**DBTYPE_WSTR**||Die interne ID des Tabellensegments.|  
|**COLUMN_ID**|**DBTYPE_WSTR**||Die interne ID der Spalte.|  
|**SEGMENT _NUMBER**|**DBTYPE_I8**||Die Ordnungszahl des Tabellensegments.|  
|**TABLE_PARTTION_NUMBER**|**DBTYPE_I8**||Die Ordnungszahl der Partition.|  
|**RECORDS_COUNT**|**DBTYPE_I8**||Die Anzahl der Datensätze in der Partition.|  
|**ALLOCATED_SIZE**|**DBTYPE_UI8**||Dem Spaltensegment zugeordnete Größe in Byte.|  
|**USED_SIZE**|**DBTYPE_UI8**||Vom Spaltensegment verwendete Größe in Byte.|  
|**COMPRESSION_TYPE**|**DBTYPE_WSTR**||Typ der für das Spaltensegment verwendeten Komprimierung. Dieser Wert ist ausschließlich für die interne Verwendung und Kundensupportzwecke bestimmt. Microsoft veröffentlicht keine gültigen Werte oder Beschreibungen für diese Spalte.|  
|**BITS_COUNT**|**DBTYPE_I8**||Die Anzahl der Bits.|  
|**BOOKMARK_BITS_COUNT**|**DBTYPE_I8**||Die Anzahl der Lesezeichenbits.|  
|**VERTIPAQ_STATE**|**DBTYPE_WSTR**||Der Status der VertiPaq-Komprimierung für dieses Spaltensegment. Der Wert ist eine der folgenden:<br /><br /> SKIPPED – Die VertiPaq-Komprimierung wurde übersprungen.<br /><br /> COMPLETED – Gibt an, dass der Überprüfungsschritt erfolgreich abgeschlossen wurde.<br /><br /> TIMEBOXED – Der Zeitrahmen der VertiPaq-Komprimierung wurde festgelegt.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|Wert|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt die dem Modellattribut "LastName" zugeordneten Speichertabellensegmente in der aktuellen Datenbank zurück.  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Schemarowsets](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
