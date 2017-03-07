---
title: "方法: 日付と時刻の値をラウンドトリップさせる"
description: "日付と時刻の値をラウンドトリップさせる方法"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 15690f18-1bb9-4bb8-bc11-0b737e2f0859
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 79c4da0cc6b4436fcbd5b345e23b387f2ad933d1
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-round-trip-date-and-time-values"></a>方法: 日付と時刻の値をラウンドトリップさせる

ある特定の時点を明確に表すように日付と時刻の値を保つことは、多くのアプリケーションに共通する要件です。 このトピックでは、[DateTime](xref:System.DateTime) 値と [DateTimeOffset](xref:System.DateTimeOffset) 値を保存して、保存した日時とまったく同じ時点を表すように復元する方法について説明します。

## <a name="to-round-trip-a-datetime-value"></a>DateTime 値をラウンドトリップさせるには

1. [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) メソッドを "o" 書式指定子と共に呼び出して、[DateTime](xref:System.DateTime) 値を対応する文字列形式に変換します。

2. [DateTime](xref:System.DateTime) 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界を通過させます。

3. [DateTime](xref:System.DateTime) 値を表す文字列を取得します。

4. [DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) メソッドを呼び出し、*DateTimeStyles* パラメーターの値として [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) を渡します。

[DateTime](xref:System.DateTime) 値をラウンドトリップさせる方法を次の例に示します。

```csharp
const string fileName = @".\DateFile.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTime dateToSave = DateTime.SpecifyKind(new DateTime(2008, 6, 12, 18, 45, 15), 
                                           DateTimeKind.Local);
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} ({1}) to {2}.", 
                  dateToSave.ToString(), 
                  dateToSave.Kind.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTime restoredDate;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), 
                                              fileName, 
                                              restoredDate.Kind.ToString());
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
//    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
//    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

```vb
Const fileName As String = ".\DateFile.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As Date = DateTime.SpecifyKind(#06/12/2008 6:45:15 PM#, _
                                              DateTimeKind.Local)
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} ({1}) to {2}.", dateToSave.ToString(), _
                  dateToSave.Kind.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDate As Date

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDate = DateTime.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), _
                  fileName, restoredDAte.Kind.ToString())
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
'    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
'    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

[DateTime](xref:System.DateTime) 値をラウンドトリップさせる場合、この方法により、あらゆる現地時刻と協定世界時刻を適切に保存できます。 たとえば、現地時刻の [DateTime](xref:System.DateTime) 値が米国太平洋標準時タイム ゾーンのシステムで保存され、米国中部標準時タイム ゾーンのシステムで復元された場合、復元された日付と時刻は&2; つのタイム ゾーンの時差を反映し、元の時刻より&2; 時間後になります。 ただし、タイム ゾーンが指定されていない時刻の場合、この方法では必ずしも正確な結果を得られるわけではありません。 [Kind](xref:System.DateTime.Kind) プロパティが [Unspecified](xref:System.DateTimeKind.Unspecified) である [DateTime](xref:System.DateTime) 値はすべて現地時刻として扱われます。 それ以外では、[DateTime](xref:System.DateTime) は間違った時点を示すことになります。 この制限を回避するには、日付と時刻の値と該当するタイム ゾーンを確実に関連付けてから保存操作と復元操作を行います。

## <a name="to-round-trip-a-datetimeoffset-value"></a>DateTimeOffset 値をラウンドトリップさせるには

[DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) メソッドを "o" 書式指定子と共に呼び出して、[DateTimeOffset](xref:System.DateTimeOffset) 値を対応する文字列形式に変換します。

2. [DateTimeOffset](xref:System.DateTimeOffset) 値の文字列形式をファイルに保存するか、プロセス、アプリケーション ドメイン、またはマシン境界を通過させます。

3. [DateTimeOffset](xref:System.DateTimeOffset) 値を表す文字列を取得します。

4. [DateTimeOffset.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTimeOffset.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) メソッドを呼び出し、*styles* パラメーターの値として [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) を渡します。

[DateTimeOffset](xref:System.DateTimeOffset) 値をラウンドトリップさせる方法を次の例に示します。

```csharp
const string fileName = @".\DateOff.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTimeOffset dateToSave = new DateTimeOffset(2008, 6, 12, 18, 45, 15, 
                                               new TimeSpan(7, 0, 0));
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTimeOffset restoredDateOff;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDateOff = DateTimeOffset.Parse(dateString, null, 
                                       DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), 
                  fileName);
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
//    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
//    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

```vb
Const fileName As String = ".\DateOff.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As New DateTimeOffset(2008, 6, 12, 18, 45, 15, _
                                     New TimeSpan(7, 0, 0))
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDateOff As DateTimeOffset

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDateOff = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), fileName)
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
'    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
'    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

この方法により、[DateTimeOffset](xref:System.DateTimeOffset) 値は常にある特定の時点として明確に識別されます。 その後、[DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) メソッドを呼び出すことによって、この値を世界協定時刻 (UTC) に変換できます。また、[DateTimeOffset.ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) メソッドまたは [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo) メソッドを呼び出すことによって、特定のタイム ゾーンの時刻に変換することもできます。 この方法には、特定のタイム ゾーンの時刻を表す [DateTimeOffset](xref:System.DateTimeOffset) 値に対して日付と時刻の演算を行ったときに、そのタイム ゾーンにおける正確な結果を得ることができない場合があるという重要な制限があります。 これは、[DateTimeOffset](xref:System.DateTimeOffset) 値をインスタンス化すると、対応するタイム ゾーンとの関連付けが解除されるためです。 したがって、日付と時刻の計算を実行した場合、タイム ゾーンの調整規則は適用されなくなります。 この問題を回避するには、日付と時刻の値、および付随するタイム ゾーンの両方を保持するカスタム型を定義します。

## <a name="see-also"></a>関連項目

[書式設定操作の実行](performing-formatting-operations.md)

[標準の日時書式指定文字列](standard-datetime.md)


