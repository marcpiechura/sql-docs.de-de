---
title: TYPE-Direktive in FOR XML-Abfragen | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1e060f93c4aa26d86fbd6683099a66821c38e9b2
ms.contentlocale: de-de
ms.lasthandoff: 06/22/2017

---
# <a name="type-directive-in-for-xml-queries"></a>TYPE-Direktive in FOR XML-Abfragen
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt [xml &#40;Transact-SQL&#41;](../../t-sql/xml/xml-transact-sql.md) und ermöglicht es Ihnen damit, durch Angeben der TYPE-Direktive optional anzufordern, dass das Ergebnis einer FOR XML-Abfrage als **xml**-Datentyp zurückgegeben wird. Dies ermöglicht Ihnen, das Ergebnis einer FOR XML-Abfrage auf dem Server zu verarbeiten. So können Sie beispielsweise eine XQuery dafür angeben, das Ergebnis einer Variablen vom Typ **xml** zuweisen oder [geschachtelte FOR XML-Abfragen](../../relational-databases/xml/use-nested-for-xml-queries.md)dafür schreiben.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt Instanzdaten des xml-Datentyps als Ergebnis verschiedener Serverkonstrukte wie FOR XML-Abfragen mit Verwendung der TYPE-Direktive an den Client zurück. Wenn der **xml** -Datentyp verwendet wird, gibt SQL Server XML-Instanzdatenwerte aus SQL-Tabellenspalten und -Ausgabeparametern zurück. Im Code der Clientanwendung erfordert der ADO.NET-Anbieter, dass die Informationen vom XML-Datentyp im Binärcode vom Server gesendet werden. Wenn Sie jedoch FOR XML ohne die TYPE-Direktive verwenden, werden die XML-Daten als Zeichenfolgentyp zurückgesendet. Der Clientanbieter ist in jedem Fall fähig, beide XML-Formate zu verarbeiten. Beachten Sie, dass FOR XML der obersten Ebene ohne die TYPE-Direktive nicht mit Cursorn verwendet werden kann.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen die Verwendung der TYPE-Direktive für FOR XML-Abfragen.  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>Abrufen von FOR XML-Abfrageergebnissen als XML-Typ  
 Die folgende Abfrage ruft Informationen zu Kundenkontakten aus der `Contacts` -Tabelle auf. Da die `TYPE` -Direktive in `FOR XML`angegeben ist, wird das Ergebnis als **xml** -Typ zurückgegeben.  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 Dies ist das Teilergebnis:  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>Zuweisen von FOR XML-Abfrageergebnissen zu einer Variablen vom Typ XML  
 Im folgenden Beispiel wird das Ergebnis einer FOR XML-Abfrage `@x` zugewiesen, einer Variablen vom Typ **xml**. Die Abfrage ruft Kontaktinformationen wie z.B. `BusinessEntityID`, `FirstName`, `LastName` sowie zusätzliche Telefonnummern aus der `AdditionalContactInfo`-Spalte mit `TYPE` **xml** ab. Da die `FOR XML`-Klausel die `TYPE`-Direktive angibt, werden die XML-Daten als **xml**-Typ zurückgegeben und einer Variablen zugewiesen.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>Abfragen von Ergebnissen einer FOR XML-Abfrage  
 FOR XML-Abfragen geben XML-Daten zurück. Folglich können Sie Methoden vom Typ **xml** wie **query()** und **value()**auf das von FOR XML-Abfragen zurückgegebene XML-Ergebnis anwenden.  
  
 In der folgenden Abfrage wird die `query()`-Methode des **xml**-Datentyps verwendet, um das Ergebnis der `FOR XML`-Abfrage abzufragen. Weitere Informationen finden Sie unter [query&#40;&#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/query-method-xml-data-type.md).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 Die innere `SELECT … FOR XML`-Abfrage gibt ein Ergebnis vom Typ **xml** zurück, auf das die äußere `SELECT`-Abfrage die `query()`-Methode vom Typ **xml** anwendet. Beachten Sie, dass die `TYPE` -Direktive angegeben ist.  
  
 Dies ist das Ergebnis:  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 In der folgenden Abfrage wird die `value()`-Methode des Datentyps **xml** verwendet, um einen Wert aus dem XML-Ergebnis einer `SELECT…FOR XML`-Abfrage abzurufen. Weitere Informationen finden Sie unter [value&#40;&#41;-Methode &#40;xml-Datentyp&#41;](../../t-sql/xml/value-method-xml-data-type.md).  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 Der XQuery-Pfadausdruck in der `value()`-Methode ruft die erste Telefonnummer des Kundenkontakts mit der `BusinessEntityID` `1` ab.  
  
> [!NOTE]  
>  Wenn die TYPE-Direktive nicht angegeben ist, wird das Ergebnis der FOR XML-Abfrage als **nvarchar(max)**zurückgegeben.  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>Verwenden von FOR XML-Abfrageergebnissen in INSERT-, UPDATE- und DELETE-Anweisungen (Transact-SQL-DML)  
 Das folgende Beispiel stellt dar, wie FOR XML-Abfragen in DML-Anweisungen (DML, Data Manipulation Language) verwendet werden können. In diesem Beispiel gibt die `FOR XML` -Abfrage eine Instanz vom Typ **xml** zurück. Die `INSERT` -Anweisung fügt diese XML-Daten in eine Tabelle ein.  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
  
  