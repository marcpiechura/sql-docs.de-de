---
title: Agent XPs (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 34863e78d2210b8c5860258dd5ade1f7aeb241c2
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="agent-xps-server-configuration-option"></a>Agent XPs (Serverkonfigurationsoption)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mithilfe der Option **Agent XPs** können Sie die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents auf diesem Server aktivieren. Wenn diese Option nicht aktiviert ist, ist der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nicht verfügbar.  
  
 Wenn Sie den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Agent-Dienst mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools starten, werden diese erweiterten gespeicherten Prozeduren automatisch aktiviert. Weitere Informationen finden Sie unter [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Wenn diese erweiterten gespeicherten Prozeduren nicht aktiviert sind, wird der Inhalt des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Knotens im Objekt-Explorer von Management Studio, unabhängig vom Status des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Diensts, nicht angezeigt.  
  
 Die folgenden Werte sind möglich:  
  
-   **0**gibt an, dass die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents nicht verfügbar sind (Standardeinstellung).  
  
-   **1**gibt an, dass die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verfügbar sind.  
  
 Die Einstellung tritt ohne Beenden und Neustarten des Servers sofort in Kraft.  
  
## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die erweiterten gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents aktiviert.  

1. Stellen Sie von Microsoft SQL Server Management Studio eine Verbindung mit dem Datenbankmodul her.

2.  Klicken Sie auf der Standardleiste auf **Neue Abfrage**.

3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. 
  
```tsql 
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  
