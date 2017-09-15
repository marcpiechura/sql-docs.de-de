---
title: Massenkopieren von Daten mit SQL Server on Linux | Microsoft Docs
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: a4fa8a4080a8483aba8494dd1195c7fbb1aec67a
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Massenkopieren von Daten mithilfe von Bcp zum SQL Server on Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In diesem Thema zeigt, wie die [Bcp](https://msdn.microsoft.com/en-us/library/ms162802.aspx) -Befehlszeilen-Hilfsprogramm zum Massenkopieren von Daten zwischen einer Instanz von SQL Server 2017 RC2 unter Linux und einer Datendatei in eine vom Benutzer angegebenes Format.

Sie können `bcp` großen Anzahl von Zeilen in SQL Server-Tabellen importieren oder Exportieren von Daten aus SQL Server-Tabellen in Datendateien. Außer in Verbindung mit der Option Queryout `bcp` erfordert keine Kenntnisse von Transact-SQL. Die `bcp` -Befehlszeilen-Hilfsprogramm funktioniert nur mit Microsoft SQL Server lokal oder in der Cloud unter Linux, Windows oder Docker und Azure SQL-Datenbank und Azure SQL Data Warehouse.

In diesem Thema erfahren Sie, wie auf:
- Importieren von Daten in einer Tabelle mit den `bcp in` Befehl
- Exportieren von Daten aus einer Tabelle Einzelhandelsabonnements der `bcp out` Befehl

## <a name="install-the-sql-server-command-line-tools"></a>Installieren Sie die SQL Server-Befehlszeilentools

`bcp`ist Teil der SQL Server-Befehlszeilentools, die mit SQL Server on Linux nicht automatisch installiert werden. Wenn Sie die SQL Server-Befehlszeilentools noch nicht auf dem Linux-Computer installiert haben, müssen Sie sie installieren. Weitere Informationen zum Installieren auswählen der Tools Ihrer Linux-Distribution aus der folgenden Liste:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Importieren von Daten mithilfe von bcp

In diesem Lernprogramm erstellen Sie eine Beispieldatenbank und die Tabelle in der lokalen SQL Server-Instanz (**"localhost"**) und dann `bcp` , in der Beispieltabelle aus einer Textdatei auf dem Datenträger zu laden.

### <a name="create-a-sample-database-and-table"></a>Erstellen einer Beispieldatenbank und der Tabelle

Zunächst erstellen eine Beispieldatenbank mit einer einfachen Tabelle, die im übrigen Teil dieses Lernprogramms verwendet wird.

1. Öffnen Sie auf die Box Linux einen Befehl Terminal ein.

2. Kopieren Sie die nachfolgenden Befehle in der terminal-Fenster. Diese Befehle verwenden das **Sqlcmd** -Befehlszeilen-Hilfsprogramm, um eine Beispieldatenbank zu erstellen (**BcpSampleDB**) und eine Tabelle (**TestEmployees**) in der lokalen SQL Server-Instanz (**"localhost"**). Denken Sie daran, ersetzen Sie die `username` und `<your_password>` vor dem Ausführen der Befehle nach Bedarf.

Erstellen Sie die Datenbank **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Erstellen Sie die Tabelle **TestEmployees** in der Datenbank **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Erstellen Sie die Quelldatendatei
Kopieren Sie den Befehl unten in der terminal-Fenster. Wir verwenden die integrierte `cat` Befehl zum Erstellen der Beispieldatendatei Text mit 3 Datensätze speichern Sie die Datei in Ihrem Basisverzeichnis als **~/test_data.txt**. Die Felder in den Datensätzen werden durch ein Komma getrennt.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Sie können überprüfen, dass die Datendatei ordnungsgemäß erstellt wurde, indem Sie den Befehl unten in der terminal-Fenster ausführen:
```bash 
cat ~/test_data.txt
```

Es wird Folgendes in die terminal-Fenster angezeigt:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Importieren von Daten aus der Quelldatendatei
Kopieren Sie die nachfolgenden Befehle in der terminal-Fenster. Dieser Befehl verwendet `bcp` für die Verbindung mit der lokalen SQL Server-Instanz (**"localhost"**) und importieren Sie die Daten aus der Datendatei (**~/test_data.txt**) in der Tabelle (**TestEmployees**) in der Datenbank (**BcpSampleDB**). Denken Sie daran, den Benutzernamen zu ersetzen und `<your_password>` vor dem Ausführen der Befehle nach Bedarf.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Hier ist eine kurze Übersicht über die Befehlszeilenparameter, die wir mit `bcp` in diesem Beispiel:
- `-S`: Gibt die Instanz von SQL Server für die Verbindung
- `-U`: Gibt die Anmelde-ID verwendet, um die Verbindung mit SQL Server
- `-P`: Gibt das Kennwort für die Anmelde-ID
- `-d`: Gibt die Datenbank für die Verbindung
- `-c`: führt Vorgänge mit einem Zeichendatentyp
- `-t`: Gibt das Feldabschlusszeichen. Verwenden wir `comma` als Feldabschlusszeichen für die Datensätze in unserer Datendatei

> [!NOTE]
> Wir sind nicht in diesem Beispiel, benutzerdefiniertes Zeilenabschlusszeichen angibt. Zeilen in der Textdatendatei ordnungsgemäß mit beendet wurden `newline` wird verwendet, wenn die `cat` Befehl aus, um zuvor Erstellung der Datendatei.

Sie können überprüfen, ob die Daten erfolgreich importiert wurde, indem Sie den Befehl unten in der terminal-Fenster ausführen. Denken Sie daran, ersetzen Sie die `username` und `<your_password>` vor Ausführung des Befehls nach Bedarf.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Daraufhin sollten die folgenden Ergebnisse angezeigt:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Exportieren von Daten mithilfe von bcp

In diesem Lernprogramm verwenden Sie `bcp` zum Exportieren von Daten aus der Beispieltabelle, die wir zuvor erstellt haben, eine neue Datei.

Kopieren Sie die nachfolgenden Befehle in der terminal-Fenster. Diese Befehle verwenden das `bcp` -Befehlszeilen-Hilfsprogramm zum Exportieren von Daten aus der Tabelle **TestEmployees** in den in der Datenbank **BcpSampleDB** in eine neue Datendatei namens **~/test_export.txt**.  Denken Sie daran, den Benutzernamen zu ersetzen und `<your_password>` vor Ausführung des Befehls nach Bedarf.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Sie können überprüfen, ob die Daten ordnungsgemäß exportiert wurde, indem Sie den Befehl unten in der terminal-Fenster ausführen:
```bash 
cat ~/test_export.txt
```

Es wird Folgendes in die terminal-Fenster angezeigt:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>Siehe auch
- [bcp (Hilfsprogramm)](https://msdn.microsoft.com/en-us/library/ms162802.aspx)
- [Datenformate für die Kompatibilität bei Verwendung von bcp](https://msdn.microsoft.com/en-us/library/ms190759.aspx)
- [Importieren von Massendaten mithilfe von BULK INSERT](https://msdn.microsoft.com/en-us/library/ms175915.aspx)
- [BULK INSERT (Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms188365.aspx)
