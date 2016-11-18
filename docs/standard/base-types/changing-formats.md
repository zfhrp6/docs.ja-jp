---
title: "正規表現の例: 日付形式の変更"
description: "正規表現の例: 日付形式の変更"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3e196697-981c-4c1d-93dd-c3b236ef36dd
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 65cdec2c8bc8caf44329ee44bd574e612723be11

---

# <a name="regular-expression-example-changing-date-formats"></a>正規表現の例: 日付形式の変更

次のコード例では、[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドを使用して、*/mm/dd/yy* 形式の日付を *dd-mm-yy* 形式の日付に置き換えます。

## <a name="example"></a>例

```csharp
static string MDYToDMY(string input) 
{
   try {
      return Regex.Replace(input, 
            "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
            "${day}-${month}-${year}", RegexOptions.None,
            TimeSpan.FromMilliseconds(150));
   }         
   catch (RegexMatchTimeoutException) {
      return input;
   }
}
```

```vb
Function MDYToDMY(input As String) As String
   Try
      Return Regex.Replace(input, _
             "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
             "${day}-${month}-${year}", RegexOptions.None,
             TimeSpan.FromMilliseconds(150))
    Catch e As RegexMatchTimeoutException
       Return input
    End Try         
End Function
```

次のコードは、アプリケーションで `MDYToDMY` メソッドを呼び出す方法を示しています。 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string dateString = DateTime.Today.ToString("d", 
                                        DateTimeFormatInfo.InvariantInfo);
      string resultString = MDYToDMY(dateString);
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString);
   }

   static string MDYToDMY(string input) 
   {
      try {
         return Regex.Replace(input, 
               "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
               "${day}-${month}-${year}", RegexOptions.None,
               TimeSpan.FromMilliseconds(150));
      }         
      catch (RegexMatchTimeoutException) {
         return input;
      }
   }

}
// The example displays the following output to the console if run on 8/21/2007:
//      Converted 08/21/2007 to 21-08-2007.
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module DateFormatReplacement
   Public Sub Main()
      Dim dateString As String = Date.Today.ToString("d", _
                                           DateTimeFormatInfo.InvariantInfo)
      Dim resultString As String = MDYToDMY(dateString)
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString)
   End Sub

    Function MDYToDMY(input As String) As String
       Try
          Return Regex.Replace(input, _
                 "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
                 "${day}-${month}-${year}", RegexOptions.None,
                 TimeSpan.FromMilliseconds(150))
        Catch e As RegexMatchTimeoutException
           Return input
        End Try         
    End Function
End Module
' The example displays the following output to the console if run on 8/21/2007:
'      Converted 08/21/2007 to 21-08-2007.
```

## <a name="comments"></a>コメント

この正規表現パターン `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から照合を開始します。
`(?<month>\d{1,2})` | 1 桁または 2 桁の 10 進数と一致します。 これは、`month` キャプチャ グループです。
`/` | スラッシュ マークと一致します。
`(?<day>\d{1,2})` | 1 桁または 2 桁の 10 進数と一致します。 これは、`day` キャプチャ グループです。
`/` | スラッシュ マークと一致します。
`(?<year>\d{2,4})` | 2 ～ 4 の 10 進数と一致します。 これは、`year` キャプチャ グループです。
`\b` | ワード境界で照合を終了します。
 
パターン `${day}-${month}-${year}` は、次の表に示すように置換文字列を定義します。

パターン | 説明
------- | ----------- 
`$(day)` | `day` キャプチャ グループによってキャプチャされた文字列を追加します。
`-` | ハイフンを追加します。
`$(month)` | `month` キャプチャ グループによってキャプチャされた文字列を追加します。
`-` | ハイフンを追加します。
`$(year)` | `year` キャプチャ グループによってキャプチャされた文字列を追加します。
 
## <a name="see-also"></a>関連項目

[.NET 正規表現](regular-expressions.md)

[正規表現の例](regex-examples.md)



<!--HONumber=Nov16_HO3-->


