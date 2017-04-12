---
title: "Importieren von Daten aus fr&#252;heren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Frühere Versionen [SQL Server], Import- und Exportdatenformate"
  - "-V (Schalter)"
  - "Datenformate [SQL Server], frühere Versionen"
  - "Vorherige Versionen [SQL Server], Import- und Exportdatenformate"
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# Importieren von Daten aus fr&#252;heren SQL Server-Versionen im systemeigenen Format oder im Zeichenformat
  Sie können **bcp** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwenden, um Daten im nativen Format oder im Zeichenformat mithilfe des Schalters **-V** aus [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] zu importieren. Der Schalter **-V** veranlasst [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Datentypen aus der angegebenen früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu verwenden. Zudem entspricht das Datendateiformat dem Format dieser früheren Version.  
  
 Um eine frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine Datendatei anzugeben, verwenden Sie den Schalter **-V** mit einem der folgenden Qualifizierer:  
  
|SQL Server-Version|Qualifizierer|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## Interpretation von Datentypen  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen bieten Unterstützung für einige neue Typen. Beim Importieren eines neuen Datentyps aus einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , muss der Dateityp in einem Format gespeichert sein, das von den älteren **bcp** -Clients gelesen werden kann. In der folgenden Tabelle finden Sie eine Übersicht, wie die neuen Datentypen konvertiert werden, damit sie mit den früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kompatibel sind.  
  
|Neue Datentypen in SQL Server 2005|Kompatible Datentypen in Version 6*x*|Kompatible Datentypen in Version 70|Kompatible Datentypen in Version 80|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|**bigint**|**decimal**|**decimal**|*|  
|**sql_variant**|**text**|**nvarchar(4000)**|*|  
|**varchar(max)**|**text**|**text**|**text**|  
|**nvarchar(max)**|**ntext**|**ntext**|**ntext**|  
|**varbinary(max)**|**image**|**image**|**image**|  
|XML|**ntext**|**ntext**|**ntext**|  
|UDT**|**image**|**image**|**image**|  
  
 *Dieser Typ wird nativ unterstützt.  
  
 **UDT gibt einen benutzerdefinierten Typ an.  
  
## Exportieren mit –V 80  
 Bei einem Massenexport von Daten mithilfe des **–V80**-Schalters werden Daten vom Typ **nvarchar(max)**, **varchar(max)**, **varbinary(max)**, XML und UDT – wie Daten vom Typ **text**, **image** und **ntext** – anstatt mit einem 8-Byte-Präfix mit einem 4-Byte-Präfix im einheitlichen Modus gespeichert. Dies ist der Standardwert für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen.  
  
## Kopieren von Datumswerten  
 Von**bcp** wird die ODBC-API für das Massenkopieren verwendet. Deshalb verwendet **bcp** zum Importieren von Datumswerten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das ODBC-Datumsformat (*jjjj-mm-tt hh:mm:ss*[*.f...*]).  
  
 Der Befehl **bcp** exportiert Datendateien im Zeichenformat immer mithilfe des ODBC-Standardformats für **datetime** - und **smalldatetime** -Werte. So wird beispielsweise eine **datetime**-Spalte mit dem Datum `12 Aug 1998` beim Massenkopieren in eine Datendatei als Zeichenfolge `1998-08-12 00:00:00.000` übertragen.  
  
> [!IMPORTANT]  
>  Achten Sie beim Importieren von Daten mit **bcp** in ein **smalldatetime**-Feld darauf, dass der Wert für Sekunden 00.000 ist; andernfalls ruft der Vorgang einen Fehler hervor. Der **smalldatetime** -Datentyp kann nur Werte beinhalten, die auf die volle Minute gerundet sind. BULK INSERT und INSERT ... SELECT * FROM OPENROWSET(BULK...) schlagen in diesem Fall nicht fehl, schneiden jedoch den Sekundenwert ab.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So verwenden Sie Datenformate für Massenimport oder Massenexport**  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## Siehe auch  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Abwärtskompatibilität des SQL Server-Datenbankmoduls](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  