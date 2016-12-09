---
title: "方法: URL からプロトコルとポート番号を抽出する"
description: "方法: URL からプロトコルとポート番号を抽出する"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d2462fb4-6d61-44ab-8466-73f1f06c3058
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 72e0c9401406dcac4eb693b056b88a531f2a0748

---

# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>方法: URL からプロトコルとポート番号を抽出する

次の例では、URL からプロトコルとポート番号を抽出します。 

## <a name="example"></a>例

例では [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) メソッドを使用して、後にコロンとポート番号が続くプロトコルを返します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string url = "http://www.contoso.com:8080/letters/readme";

      Regex r = new Regex(@"^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                          RegexOptions.None, TimeSpan.FromMilliseconds(150));
      Match m = r.Match(url);
      if (m.Success)
         Console.WriteLine(r.Match(url).Result("${proto}${port}")); 
   }
}
// The example displays the following output:
//       http:8080
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim url As String = "http://www.contoso.com:8080/letters/readme.html" 
      Dim r As New Regex("^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                         RegexOptions.None, TimeSpan.FromMilliseconds(150))

      Dim m As Match = r.Match(url)
      If m.Success Then
         Console.WriteLine(r.Match(url).Result("${proto}${port}"))
      End If   
   End Sub
End Module
' The example displays the following output:
'       http:8080
```

この正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`^` | 文字列の先頭から照合を開始します。
`(?<proto>\w+)` | 1 つ以上の単語文字に一致します。 このグループに proto と名前を付けます。
`://` | 後に 2 つのスラッシュ記号が続くコロンと一致します。
`[^/]+?` | スラッシュ記号以外の任意の文字の 1 回以上の (ただし、可能な限り少ない) 出現と一致します。
`(?<port>:\d+)?` | 後に 1 桁以上の文字が続くコロンの 0 回または 1 回の出現と一致します。 このグループに port と名前を付けます。
`/` | スラッシュ記号に一致します。
 
[Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) メソッドは、正規表現パターンでキャプチャされた 2 つの名前付きグループの値を連結する、`${proto}${port}` 置換シーケンスを展開します。 これは、[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティによって返されたコレクション オブジェクトから取得した文字列を明示的に連結するための便利な代替です。

例では、[Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) メソッドを 2 つの置換 `${proto}` と `${port}` とともに使用して、キャプチャされたグループを出力文字列に含めます。 代わりに、次のコードに示されているように、一致の [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトから、キャプチャされたグループを取得することができます。

```csharp
Console.WriteLine(m.Groups["proto"].Value + m.Groups["port"].Value); 
```

```vb
Console.WriteLine(m.Groups("proto").Value + m.Groups("port").Value)
```

## <a name="see-also"></a>関連項目

[.NET 正規表現](regular-expressions.md)

[正規表現の例](regex-examples.md)



<!--HONumber=Nov16_HO3-->


