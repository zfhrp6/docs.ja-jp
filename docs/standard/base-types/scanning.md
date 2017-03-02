---
title: "正規表現の例: HREF のスキャン"
description: "正規表現の例: HREF のスキャン"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6484880-bdac-47cd-b5e5-9419c9ed14cd
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 7dfc48e03a275522a48a49dbb44ce1d0f8b05e75
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expression-example-scanning-for-hrefs"></a>正規表現の例: HREF のスキャン

次の例では、入力文字列を検索して、文字列中のすべての href="…" 値とその場所を表示します。 

## <a name="the-regex-object"></a>Regex オブジェクト

`DumpHRefs` メソッドは、ユーザー コードから複数回呼び出される可能性があるため、`static` [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) メソッドを使用します。 これにより、正規表現エンジンが正規表現をキャッシュできるようになり、メソッドを呼び出すたびに新しい [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化するオーバーヘッドを回避できます。 [Match](xref:System.Text.RegularExpressions.Match) オブジェクトは、文字列内のすべての一致を反復処理するために使用されます。 

```csharp
private static void DumpHRefs(string inputString) 
{
   Match m;
   string HRefPattern = "href\\s*=\\s*(?:[\"'](?<1>[^\"']*)[\"']|(?<1>\\S+))";

   try {
      m = Regex.Match(inputString, HRefPattern, 
                      RegexOptions.IgnoreCase | RegexOptions.Compiled, 
                      TimeSpan.FromSeconds(1));
      while (m.Success)
      {
         Console.WriteLine("Found href " + m.Groups[1] + " at " 
            + m.Groups[1].Index);
         m = m.NextMatch();
      }   
   }
   catch (RegexMatchTimeoutException) {
      Console.WriteLine("The matching operation timed out.");
   }
}
```

```vb
Private Sub DumpHRefs(inputString As String) 
   Dim m As Match
   Dim HRefPattern As String = "href\s*=\s*(?:[""'](?<1>[^""']*)[""']|(?<1>\S+))"

   Try
      m = Regex.Match(inputString, HRefPattern, _ 
                      RegexOptions.IgnoreCase Or RegexOptions.Compiled,
                      TimeSpan.FromSeconds(1))
      Do While m.Success
         Console.WriteLine("Found href {0} at {1}.", _
                           m.Groups(1), m.Groups(1).Index)
         m = m.NextMatch()
      Loop   
   Catch e As RegexMatchTimeoutException
      Console.WriteLine("The matching operation timed out.")
   End Try
End Sub
```

`DumpHRefs` メソッドを呼び出す例を次に示します。

```csharp
public static void Main()
{
   string inputString = "My favorite web sites include:</P>" +
                        "<A HREF=\"http://msdn2.microsoft.com\">" +
                        "MSDN Home Page</A></P>" +
                        "<A HREF=\"http://www.microsoft.com\">" +
                        "Microsoft Corporation Home Page</A></P>" +
                        "<A HREF=\"http://blogs.msdn.com/bclteam\">" +
                        ".NET Base Class Library blog</A></P>";
   DumpHRefs(inputString);                     

}
// The example displays the following output:
//       Found href http://msdn2.microsoft.com at 43
//       Found href http://www.microsoft.com at 102
//       Found href http://blogs.msdn.com/bclteam at 176
```

```vb
Public Sub Main()
   Dim inputString As String = "My favorite web sites include:</P>" & _
                               "<A HREF=""http://msdn2.microsoft.com"">" & _
                               "MSDN Home Page</A></P>" & _
                               "<A HREF=""http://www.microsoft.com"">" & _
                               "Microsoft Corporation Home Page</A></P>" & _
                               "<A HREF=""http://blogs.msdn.com/bclteam"">" & _
                               ".NET Base Class Library blog</A></P>"
   DumpHRefs(inputString)                     
End Sub
' The example displays the following output:
'       Found href http://msdn2.microsoft.com at 43
'       Found href http://www.microsoft.com at 102
'       Found href http://blogs.msdn.com/bclteam/) at 176
```

この正規表現パターン `href\s*=\s*(?:["']&#40;?<1>[^"']*)["']|(?<1>\S+))` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`href` | リテラル文字列 "href" と一致します。 一致では、大文字と小文字を区別しません。
`\s*` | 0 個以上の空白文字と一致します。
`=` |等号と一致します。
`\s*` | 0 個以上の空白文字と一致します。
`(?:["']&#40;?<1>[^"']*)"&#124;(?<1>\S+))` | 次のいずれかと一致し、キャプチャ グループに結果を代入しません: 引用符またはアポストロフィ、引用符またはアポストロフィ以外の任意の文字の&0; 回以上の繰り返し、引用符またはアポストロフィの順に続く文字列。 このパターンには `1` という名前のグループが含まれています。 または、1 個以上の空白以外の文字。 このパターンには `1` という名前のグループが含まれています。
`(?<1>[^"']*)` | 引用符またはアポストロフィ以外の任意の文字の&0; 回以上の繰り返しを `1` という名前のキャプチャ グループに代入します。
`"(?<1>\S+)` | 1 個以上の空白以外の文字を `1` という名前のキャプチャ グループに代入します。
 
## <a name="match-result-class"></a>Match 結果クラス

検索結果は [Match](xref:System.Text.RegularExpressions.Match) クラス内に格納されます。これにより、検索処理によって抽出されたすべての部分文字列にアクセスできます。 このクラスは、検索対象となった文字列や、使用された正規表現も記憶しているため、[Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを呼び出して、最後の検索が終了した位置から別の検索を実行することができます。

## <a name="explicitly-named-captures"></a>明示的に指定したキャプチャ

従来の正規表現では、キャプチャするかっこに自動的に連番が割り当てられます。 その結果、2 つの問題が発生します。 1 つ目の問題は、かっこのペアの挿入や削除を行って正規表現が修正されると、新しい番号を反映するために、番号付きのキャプチャを参照するコードをすべて書き直す必要があることです。 2 つ目の問題は、ある文字列の検索用に&2; つの代替表現を指定する際、異なるかっこのペアを使用することが多いため、実際にどちらの代替表現から結果が返されたのかを判断するのが難しい場合があることです。

これらの問題に対処するために、[Regex](xref:System.Text.RegularExpressions.Regex) クラスでは指定されたスロットに一致文字列をキャプチャするための構文 `(?<name>…)` をサポートしています (スロットには、文字列または整数の名前を付けることができます。整数の名前を付けた方が、よりすばやく再呼び出しできます)。 これにより、同じ文字列に対する代替表現の一致結果をすべて同じ場所に渡すことができます。 競合が発生する場合は、スロットにキャプチャされた最後の一致文字列が、適切な一致であると見なされます。 (ただし、1 つのスロットで複数の一致文字列の完全なリストを使用することもできます。 詳細については、[Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) コレクションを参照してください。)

## <a name="see-also"></a>関連項目

[.NET 正規表現](regular-expressions.md)

[正規表現の例](regex-examples.md)


