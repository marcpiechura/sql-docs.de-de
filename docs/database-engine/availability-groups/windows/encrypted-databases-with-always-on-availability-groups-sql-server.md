---
title: "Verschl&#252;sselte Datenbanken bei Always On-Verf&#252;gbarkeitsgruppen (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Transparent Data Encryption, AlwaysOn-Verfügbarkeitsgruppen"
  - "TDE, AlwaysOn-Verfügbarkeitsgruppen"
  - "Verfügbarkeitsgruppen [SQL Server], Interoperabilität"
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# Verschl&#252;sselte Datenbanken bei Always On-Verf&#252;gbarkeitsgruppen (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Dieses Thema enthält Informationen zur Verwendung aktuell verschlüsselter oder vor kurzem entschlüsselter Datenbanken mit [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **In diesem Thema:**  
  
-   [Einschränkungen](#Restrictions)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn eine Datenbank verschlüsselt ist oder sogar einen Datenbankverschlüsselungs-Schlüssel (DEK) enthält, können Sie die Datenbank nicht mithilfe von [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] oder [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] einer Verfügbarkeitsgruppe hinzufügen. Selbst wenn eine verschlüsselte Datenbank entschlüsselt wurde, enthalten ihre Protokollsicherungen möglicherweise verschlüsselte Daten. In diesem Fall ist es unter Umständen nicht möglich, die anfängliche Datensynchronisierung vollständig auf der Datenbank durchzuführen. Grund hierfür ist die Tatsache, dass für den Wiederherstellungsprotokollvorgang eventuell das Zertifikat erforderlich ist, das von den Datenbank-Verschlüsselungsschlüsseln (DEKs) verwendet wurde, und dieses Zertifikat möglicherweise nicht verfügbar ist.  
  
     So machen Sie eine entschlüsselte Datenbank verfügbar für das Hinzufügen zu einer Verfügbarkeitsgruppe mithilfe des Assistenten:  
  
    1.  Erstellen Sie eine Protokollsicherung von der primären Datenbank.  
  
    2.  Erstellen Sie eine vollständige Datenbanksicherung der primären Datenbank.  
  
    3.  Stellen Sie die Datenbanksicherung auf der Serverinstanz wieder her, die das sekundäre Replikat hostet.  
  
    4.  Erstellen Sie eine neue Protokollsicherung aus der primären Datenbank.  
  
    5.  Stellen Sie diese Protokollsicherung in der sekundären Datenbank wieder her.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-database-to-availability-group-wizard-sql-server-management-studio.md)  
  
## Siehe auch  
 [Übersicht über Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Transparente Datenverschlüsselung &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
  
  