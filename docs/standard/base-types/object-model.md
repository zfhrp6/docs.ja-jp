---
title: "正規表現のオブジェクト モデル"
description: "正規表現のオブジェクト モデル"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a1e611ec-c6a2-48c6-9c52-0ed845787621
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 4e8744c6c7a42c3803bf9716a3ae271b7284be3d
ms.lasthandoff: 03/02/2017

---

# <a name="the-regular-expression-object-model"></a>正規表現のオブジェクト モデル

ここでは、.NET の正規表現を扱うときに使用するオブジェクト モデルについて説明します。 このチュートリアルは、次のセクションで構成されています。

* [正規表現エンジン](#the-regular-expression-engine)

* [MatchCollection オブジェクトと Match オブジェクト](#the-matchcollection-and-match-objects)

* [GroupCollection](#the-group-collection)

* [キャプチャ グループ](#the-captured-group)

* [CaptureCollection](#the-capture-collection)

* [個々のキャプチャ](#the-individual-capture)

## <a name="the-regular-expression-engine"></a>正規表現エンジン

.NET の正規表現エンジンは、[Regex](xref:System.Text.RegularExpressions.Regex) クラスによって表されます。 正規表現エンジンは、正規表現の解析とコンパイル、および正規表現パターンと入力文字列を照合する操作を実行します。 エンジンは、.NET 正規表現のオブジェクト モデルの中核となるコンポーネントです。

正規表現エンジンは、次のいずれかの方法で使用できます。

* [Regex](xref:System.Text.RegularExpressions.Regex) クラスの静的メソッドを呼び出す。 メソッドのパラメーターには、入力文字列と正規表現パターンが含まれます。 静的メソッド呼び出しで使用した正規表現は、正規表現エンジンによってキャッシュされるので、同じ正規表現を使用する静的正規表現メソッドを繰り返し呼び出す場合、パフォーマンスが比較的向上します。

* 正規表現をクラス コンストラクターに渡して [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトをインスタンス化する。 この場合、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトは変更不可 (読み取り専用) で、単一の正規表現と密に結合された正規表現エンジンを表します。 Regex インスタンスによって使用される正規表現はキャッシュされないので、同じ正規表現で [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトを複数回インスタンス化しないでください。

[Regex](xref:System.Text.RegularExpressions.Regex) クラスのメソッドを呼び出すと、次のような処理を実行できます。 

* 文字列が正規表現パターンと一致するかどうかを確認する。

* 単一の一致または最初の一致を抽出する。

* すべての一致を抽出する。

* 一致した部分文字列を置換する。

* 単一の文字列を文字列配列に分割する。

ここでは、これらの操作について説明します。

### <a name="matching-a-regular-expression-pattern"></a>正規表現パターンの照合

[Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) メソッドは、文字列がパターンと一致する場合は `true` を返し、一致しない場合は `false` を返します。 [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) メソッドは、文字列入力を検証する場合によく使用されます。 たとえば、次のコードでは、文字列は米国の有効な社会保障番号と一致します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] values = { "111-22-3333", "111-2-3333"};
      string pattern = @"^\d{3}-\d{2}-\d{4}$";
      foreach (string value in values) {
         if (Regex.IsMatch(value, pattern))
            Console.WriteLine("{0} is a valid SSN.", value);
         else   
            Console.WriteLine("{0}: Invalid", value);
      }
   }
}
// The example displays the following output:
//       111-22-3333 is a valid SSN.
//       111-2-3333: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim values() As String = { "111-22-3333", "111-2-3333"}
      Dim pattern As String = "^\d{3}-\d{2}-\d{4}$"
      For Each value As String In values
         If Regex.IsMatch(value, pattern) Then
            Console.WriteLine("{0} is a valid SSN.", value)
         Else   
            Console.WriteLine("{0}: Invalid", value)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       111-22-3333 is a valid SSN.
'       111-2-3333: Invalid
```

この正規表現パターン `^\d{3}-\d{2}-\d{4}$` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`^` | 入力文字列の先頭と一致します。
`\d{3}` | 3 個の&10; 進数と一致します。
`-` | ハイフンと一致します。
`\d{2}` | 2 桁の&10; 進数と一致します。
`-` | ハイフンと一致します。
`\d{4}` | 4 桁の&10; 進数と一致します。
`$` | 入力文字列の末尾と一致します。
 
### <a name="extracting-a-single-match-or-the-first-match"></a>単一の一致または最初の一致の抽出

[Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) メソッドは、正規表現パターンに一致する最初の部分文字列の情報を含む [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを返します。 `Match.Success` プロパティが `true` (一致する文字列が見つかったことを示す) を返す場合は、[Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを呼び出すと後続の一致する文字列の情報を取得できます。 これらのメソッド呼び出しは、`Match.Success` プロパティによって `false` が返されるまで続行できます。 たとえば、次のコードでは、[Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) メソッドを使用して、重複する単語が文字列内で最初に出現する位置を検索します。 次に、[Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを呼び出してその他の出現位置を検索します。 この例では、メソッドを呼び出すごとに `Match.Success` プロパティを調べ、現在の一致が成功したかどうか、および続けて [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを呼び出す必要があるかどうかを確認します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      Match match = Regex.Match(input, pattern);
      while (match.Success)
      {
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
         match = match.NextMatch();
      }                       
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
         match = match.NextMatch()
      Loop                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

この正規表現パターン `\b(\w+)\W+(\1)\b` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から照合を開始します。
`(\w+)` | 1 つ以上の単語文字に一致します。 これが最初のキャプチャ グループです。
`\W+` | 1 個以上の単語文字に使用されない文字と一致します。
`(\1)` | 最初にキャプチャされた文字列と一致します。 これが&2; 番目のキャプチャ グループです。 
`\b` | ワード境界で照合を終了します。
 
### <a name="extracting-all-matches"></a>すべての一致の抽出

[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドは、入力文字列で正規表現エンジンによって検出されたすべての一致文字列の情報を含む [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトを返します。 たとえば、前の例を書き換えて、[Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) メソッドと [NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドではなく [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドを呼び出すことができます。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
      Next                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

### <a name="replacing-a-matched-substring"></a>一致した部分文字列の置換

[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) メソッドは、正規表現パターンに一致した各部分文字列を指定された文字列または正規表現パターンに置き換えて、置換が適用された入力文字列全体を返します。 たとえば、次のコードでは、文字列内の&10; 進数の前に米国の通貨記号が追加されます。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+\.\d{2}\b";
      string replacement = "$$$&"; 
      string input = "Total Cost: 103.64";
      Console.WriteLine(Regex.Replace(input, pattern, replacement));     
   }
}
// The example displays the following output:
//       Total Cost: $103.64
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+\.\d{2}\b"
      Dim replacement As String = "$$$&" 
      Dim input As String = "Total Cost: 103.64"
      Console.WriteLine(Regex.Replace(input, pattern, replacement))     
   End Sub
End Module
' The example displays the following output:
'       Total Cost: $103.64
```

この正規表現パターン `\b\d+\.\d{2}\b` の解釈を次の表に示します。

パターン | 説明
------- | ----------- 
`\b` | ワード境界から照合を開始します。
`\d+` | 1 個以上の&10; 進数と一致します。
`\.` | ピリオドと一致します。
`\d{2}` | 2 桁の&10; 進数と一致します。
`\b` | ワード境界で照合を終了します。
 
置換パターン `$$$&` の解釈を次の表に示します。

パターン | 置換文字列
------- | ------------------ 
`$$` | ドル記号 (**$**) 文字。
`$&` | 一致した部分文字列全体。
 
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>単一の文字列の文字列配列への分割

[Regex.Split](xref:System.Text.RegularExpressions.Regex.Split(System.String)) メソッドは、正規表現によって定義されている位置で、入力文字列を分割します。 たとえば、次のコードでは、番号付きリストの項目を文字列配列に配置します。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea";
      string pattern = @"\b\d{1,2}\.\s";
      foreach (string item in Regex.Split(input, pattern))
      {
         if (! String.IsNullOrEmpty(item))
            Console.WriteLine(item);
      }      
   }
}
// The example displays the following output:
//       Eggs
//       Bread
//       Milk
//       Coffee
//       Tea
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea"
      Dim pattern As String = "\b\d{1,2}\.\s"
      For Each item As String In Regex.Split(input, pattern)
         If Not String.IsNullOrEmpty(item) Then
            Console.WriteLine(item)
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       Eggs
'       Bread
'       Milk
'       Coffee
'       Tea
```

この正規表現パターン `\b\d{1,2}\.\s` の解釈を次の表に示します。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`\d{1,2}` | 1 桁または&2; 桁の&10; 進数と一致します。
`\.` | ピリオドと一致します。
`\s` | 空白文字と一致します。
 
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection オブジェクトと Match オブジェクト

[Regex](xref:System.Text.RegularExpressions.Regex) メソッドは、正規表現のオブジェクト モデルに含まれる [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) と [Match](xref:System.Text.RegularExpressions.Match) の&2; つのオブジェクトを返します。 

### <a name="the-match-collection"></a>MatchCollection

[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドは、正規表現エンジンによって検出されたすべての一致文字列を入力文字列に出現する順序で表す [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを含む [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトを返します。 一致がない場合、このメソッドは、メンバーのない [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを含む [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトを返します。 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` プロパティを使用すると、コレクションの個々のメンバーに、0 から [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) プロパティの値より&1; 小さい値までの範囲のインデックスでアクセスできます。 'Item` は、コレクションのインデクサー (C# の場合) および既定のプロパティ (Visual Basic の場合) です。

既定では、[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドを呼び出すと、遅延評価を使用して [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトに値が設定されます。 値の設定が完了しているコレクションを必要とするプロパティ ([MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) プロパティや `Item` プロパティなど) にアクセスする場合は、パフォーマンスが低下する可能性があります。 そのため、[MatchCollection.GetEnumerator](xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator) メソッドによって返される [IEnumerator](xref:System.Collections.IEnumerator) オブジェクトを使用してコレクションにアクセスすることをお勧めします。 個々の言語は、C# の `foreach` やコレクションの IEnumerator](xref:System.Collections.IEnumerator) インターフェイスをラップする Visual Basic の `For Each' など、構成体を提供します。

次の例では、[Regex.Matches(String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) メソッドを使用して、入力文字列の中で見つかったすべての一致を [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトに設定します。 この例では、コレクションを列挙して一致文字列を文字列配列にコピーし、文字位置を整数配列に記録します。

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
       MatchCollection matches;
       List<string> results = new List<string>();
       List<int> matchposition = new List<int>();

       // Create a new Regex object and define the regular expression.
       Regex r = new Regex("abc");
       // Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd");
       // Enumerate the collection to retrieve all matches and positions.
       foreach (Match match in matches)
       {
          // Add the match string to the string array.
           results.Add(match.Value);
           // Record the character position where the match was found.
           matchposition.Add(match.Index);
       }
       // List the results.
       for (int ctr = 0; ctr < results.Count; ctr++)
         Console.WriteLine("'{0}' found at position {1}.", 
                           results[ctr], matchposition[ctr]);  
   }
}
// The example displays the following output:
//       'abc' found at position 3.
//       'abc' found at position 7.
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
       Dim matches As MatchCollection
       Dim results As New List(Of String)
       Dim matchposition As New List(Of Integer)

       ' Create a new Regex object and define the regular expression.
       Dim r As New Regex("abc")
       ' Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd")
       ' Enumerate the collection to retrieve all matches and positions.
       For Each match As Match In matches
          ' Add the match string to the string array.
           results.Add(match.Value)
           ' Record the character position where the match was found.
           matchposition.Add(match.Index)
       Next
       ' List the results.
       For ctr As Integer = 0 To results.Count - 1
         Console.WriteLine("'{0}' found at position {1}.", _
                           results(ctr), matchposition(ctr))  
       Next
   End Sub
End Module
' The example displays the following output:
'       'abc' found at position 3.
'       'abc' found at position 7.
```

### <a name="the-match"></a>Match

[Match](xref:System.Text.RegularExpressions.Match) クラスは、1 回の正規表現検索に一致した結果を表します。 [Match](xref:System.Text.RegularExpressions.Match) オブジェクトには&2; つの方法でアクセスできます。

* Regex.Matches メソッドから返される [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトから取得する。 個々の [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを取得するには、`foreach` 構成体 (C# の場合) または `For Each...Next` 構成体 (Visual Basic の場合) を使用してコレクションを反復処理するか、[MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` プロパティを使用してインデックスまたは名前で特定の [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを取得します。 また、0 からコレクションのオブジェクト数より&1; 小さい値までの範囲のインデックスでコレクションを反復処理して、コレクションから個々の [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを取得することもできます。 ただし、このメソッドは [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) プロパティにアクセスするので、遅延評価を活用できません。 

  次の例では、`foreach` 構成体を使用してコレクションを反復処理することで、個々の [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) オブジェクトから取得します。 この正規表現は、単純に入力文字列内の文字列 "abc" と一致します。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        foreach (Match match in Regex.Matches(input, pattern))
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        For Each match As Match In Regex.Matches(input, pattern)
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
        Next                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

* 文字列または文字列の一部で最初に一致する文字列を表す [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを返す [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) メソッドを呼び出す。 `Match.Success` プロパティの値を取得すると、一致文字列が見つかったかどうかを確認できます。 後続の一致する文字列を表す [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを取得するには、返された [Match](xref:System.Text.RegularExpressions.Match) オブジェクトの `Success` プロパティが `false` になるまで [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを繰り返し呼び出します。 

  次の例では、入力文字列内の文字列 "abc" と一致する [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) メソッドと [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを使用します。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        Match match = Regex.Match(input, pattern);
        while (match.Success)
        {
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
           match = match.NextMatch();                  
        }                     
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        Dim match As Match = Regex.Match(input, pattern)
        Do While match.Success
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
           match = match.NextMatch()                  
        Loop                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

[Match](xref:System.Text.RegularExpressions.Match) クラスの&2; つのプロパティによってコレクション オブジェクトが返されます。

* [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティは、正規表現パターンのキャプチャ グループに一致する部分文字列の情報を含む [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトを返します。 

* `Match.Captures` プロパティは、用途が限定された [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトを返します。 [Match](xref:System.Text.RegularExpressions.Match) オブジェクトの `Success` プロパティが `false` の場合、コレクションに値は設定されません。 それ以外の場合は、[Match](xref:System.Text.RegularExpressions.Match) オブジェクトと同じ情報を含む単一の [Capture](xref:System.Text.RegularExpressions.Capture) オブジェクトが格納されます。 

これらのオブジェクトの詳細については、このトピックで後述する「[GroupCollection](#the-group-collection)」および「[CaptureCollection](#the-capture-collection)」を参照してください。

[Match](xref:System.Text.RegularExpressions.Match) クラスの&2; つの追加プロパティに、一致文字列の情報が保持されます。 `Match.Value` プロパティは、正規表現パターンに一致する入力文字列内の部分文字列を返します。 `Match.Index` プロパティは、入力文字列内の一致する文字列の&0; から始まる開始位置を返します。

[Match](xref:System.Text.RegularExpressions.Match) クラスには、2 つのパターン一致メソッドもあります。

* [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドは、現在の [Match](xref:System.Text.RegularExpressions.Match) オブジェクトで表される一致文字列の後の一致文字列を検索し、その一致文字列を表す [Match](xref:System.Text.RegularExpressions.Match) オブジェクトを返します。

* [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドは、一致した文字列に対して指定された置換操作を実行し、その結果を返します。 


次の例では、[Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) メソッドを使用して、2 桁の小数部を含むすべての数値の前に **$** 記号および空白を付加します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+(,\d{3})*\.\d{2}\b";
      string input = "16.32\n194.03\n1,903,672.08"; 

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Result("$$ $&"));
   }
}
// The example displays the following output:
//       $ 16.32
//       $ 194.03
//       $ 1,903,672.08
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+(,\d{3})*\.\d{2}\b"
      Dim input As String = "16.32" + vbCrLf + "194.03" + vbCrLf + "1,903,672.08" 

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Result("$$ $&"))
      Next
   End Sub
End Module
' The example displays the following output:
'       $ 16.32
'       $ 194.03
'       $ 1,903,672.08
```

正規表現パターン `\b\d+(,\d{3})*\.\d{2}\b` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`\d+` | 1 個以上の&10; 進数と一致します。
`(,\d{3})*` | コンマの後に&3; 桁の&10; 進数字が続くパターンの&0; 回以上の出現と一致します。
`\.` | 小数点文字と一致します。
`\d{2} | 2 桁の&10; 進数と一致します。
`\b` | ワード境界で照合を終了します。
 
置換パターン **$$ $&** は、一致した部分文字列がドル記号 (**$**) (`$$` パターン)、空白、および一致文字列の値 (`$&` パターン) に置き換えられることを示します。

## <a name="the-group-collection"></a>GroupCollection

[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティは、単一の一致でキャプチャされたグループを表す [Group](xref:System.Text.RegularExpressions.Group) オブジェクトを含む [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトを返します。 コレクション内の最初の [Group](xref:System.Text.RegularExpressions.Group) オブジェクト (インデックス 0 の位置にあるオブジェクト) は、一致した文字列全体を表します。 後続の各オブジェクトは、1 つのキャプチャ グループによるキャプチャの結果を表します。 

コレクション内の個々の [Group](xref:System.Text.RegularExpressions.Group) オブジェクトを取得するには、[GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) プロパティを使用します。 名前のないグループはコレクション内の順序位置で取得でき、名前付きグループは名前または順序位置で取得できます。 名前のないキャプチャはコレクションの最初に位置し、正規表現パターンで定義されている順序で左から右にインデックスが付けられます。 名前付きキャプチャは、名前のないキャプチャの後に、正規表現パターンで定義されている順序で左から右にインデックスが付けられます。 特定の正規表現一致メソッドで返されたコレクションで使用可能な番号付きグループを判別するには、インスタンス [Regex.GetGroupNumbers](xref:System.Text.RegularExpressions.Regex.GetGroupNumbers) メソッドを呼び出すことができます。 コレクションで使用可能な名前付きグループを判別するには、インスタンス R[Regex.GetGroupNames](xref:System.Text.RegularExpressions.Regex.GetGroupNames) メソッドを呼び出すことができます。 どちらのメソッドも、正規表現によって検出された一致を分析する汎用ルーチンで特に役立ちます。 

[GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) プロパティは、コレクションのインデクサー (C# の場合) およびコレクション オブジェクトの既定のプロパティ (Visual Basic の場合) です。 つまり、個々の [Group](xref:System.Text.RegularExpressions.Group) オブジェクトには、次のようにインデックスで (または名前付きグループの場合は名前で) アクセスできます。 

```csharp
Group group = match.Groups[ctr];
```

```vb
Dim group As Group = match.Groups(ctr)
```

次の例では、グループ化構成体を使用して日付の月、日、および年をキャプチャする正規表現を定義します。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s(\d{1,2}),\s(\d{4})\b";
      string input = "Born: July 28, 1989";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
         for (int ctr = 0; ctr <  match.Groups.Count; ctr++)
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups[ctr].Value);
    }
}
// The example displays the following output:
//       Group 0: July 28, 1989
//       Group 1: July
//       Group 2: 28
//       Group 3: 1989
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s(\d{1,2}),\s(\d{4})\b"
      Dim input As String = "Born: July 28, 1989"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         For ctr As Integer = 0 To match.Groups.Count - 1
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups(ctr).Value)
         Next      
      End If   
   End Sub
End Module
' The example displays the following output:
'       Group 0: July 28, 1989
'       Group 1: July
'       Group 2: 28
'       Group 3: 1989
```

正規表現パターン `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\b` | ワード境界から照合を開始します。
`(\w+)` | 1 つ以上の単語文字に一致します。 これが最初のキャプチャ グループです。
`\s` | 空白文字と一致します。
`(\d{1,2})` | 1 桁または&2; 桁の&10; 進数と一致します。 これが&2; 番目のキャプチャ グループです。
`,` | コンマに一致します。
`\s` | 空白文字と一致します。
`(\d{4})` | 4 桁の&10; 進数と一致します。 これが&3; 番目のキャプチャ グループです。
`\b` | ワード境界で照合を終了します。
 
## <a name="the-captured-group"></a>キャプチャ グループ

[Group](xref:System.Text.RegularExpressions.Group) クラスは、1 つのキャプチャ グループによるキャプチャの結果を表します。 正規表現で定義されているキャプチャ グループを表す [Group](xref:System.Text.RegularExpressions.Group) オブジェクトは、[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) プロパティによって返される [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) オブジェクトの [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) プロパティによって返されます。 [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) プロパティは、[Group](xref:System.Text.RegularExpressions.Group) クラスのインデクサー (C# の場合) および既定のプロパティ (Visual Basic の場合) です。 `foreach` 構成体を使用してコレクションを反復処理することで、個々のメンバーを取得することもできます。 例については、前のセクションを参照してください。

次の例では、入れ子にしたグループ化構成体を使用して部分文字列をキャプチャし、グループ化します。 正規表現パターン `(a(b))c` は、文字列 "abc" と一致します。 部分文字列 "ab" を最初のキャプチャ グループに代入し、部分文字列 "b" を&2; 番目のキャプチャ グループに代入します。

```csharp
List<int> matchposition = new List<int>();
List<string> results = new List<string>();
// Define substrings abc, ab, b.
Regex r = new Regex("(a(b))c"); 
Match m = r.Match("abdabc");
for (int i = 0; m.Groups[i].Value != ""; i++) 
{
   // Add groups to string array.
   results.Add(m.Groups[i].Value); 
   // Record character position.
   matchposition.Add(m.Groups[i].Index); 
}

// Display the capture groups.
for (int ctr = 0; ctr < results.Count; ctr++)
   Console.WriteLine("{0} at position {1}", 
                     results[ctr], matchposition[ctr]);
// The example displays the following output:
//       abc at position 3
//       ab at position 3
//       b at position 4
```

```vb
Dim matchposition As New List(Of Integer)
 Dim results As New List(Of String)
 ' Define substrings abc, ab, b.
 Dim r As New Regex("(a(b))c") 
 Dim m As Match = r.Match("abdabc")
 Dim i As Integer = 0
 While Not (m.Groups(i).Value = "")    
    ' Add groups to string array.
    results.Add(m.Groups(i).Value)     
    ' Record character position. 
    matchposition.Add(m.Groups(i).Index) 
     i += 1
 End While

 ' Display the capture groups.
 For ctr As Integer = 0 to results.Count - 1
    Console.WriteLine("{0} at position {1}", _ 
                      results(ctr), matchposition(ctr))
 Next                     
' The example displays the following output:
'       abc at position 3
'       ab at position 3
'       b at position 4
```

次の例では、名前付きグループ化構成体を使用して、"DATANAME:VALUE" 形式のデータを含む文字列から部分文字列をキャプチャします。この正規表現は、コロン (:) でデータを分割します。

```csharp
Regex r = new Regex("^(?<name>\\w+):(?<value>\\w+)");
Match m = r.Match("Section1:119900");
Console.WriteLine(m.Groups["name"].Value);
Console.WriteLine(m.Groups["value"].Value);
// The example displays the following output:
//       Section1
//       119900
```

```vb
Dim r As New Regex("^(?<name>\w+):(?<value>\w+)")
Dim m As Match = r.Match("Section1:119900")
Console.WriteLine(m.Groups("name").Value)
Console.WriteLine(m.Groups("value").Value)
' The example displays the following output:
'       Section1
'       119900
```

正規表現パターン `^(?<name>\w+):(?<value>\w+)` は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`^` | 入力文字列の先頭から照合を開始します。
`(?<name>\w+)` | 1 つ以上の単語文字に一致します。 このキャプチャ グループの名前は name です。
`:` | コロンと一致します。
`(?<value>\w+)` | 1 つ以上の単語文字に一致します。 このキャプチャ グループの名前は value です。
 
[Group](xref:System.Text.RegularExpressions.Group) クラスのプロパティには、キャプチャ グループの情報が保持されます。キャプチャされた部分文字列が `Group.Value` プロパティに含まれ、キャプチャ グループの入力テキスト内での開始位置が `Group.Index` プロパティによって示され、キャプチャされたテキストの長さが `Group.Length` プロパティに含まれ、部分文字列がキャプチャ グループによって定義されたパターンと一致したかどうかが `Group.Success` プロパティによって示されます。

量指定子をグループに適用する場合 (詳細については、「[正規表現での量指定子](quantifiers.md)」を参照)、キャプチャ グループごとに&1; つのキャプチャという関係が&2; つの方法で変更されます。

* __*__ または __*?__ 量指定子 (0 回以上の一致を指定する) をグループに適用した場合、キャプチャ グループには入力文字列で一致した文字列が含まれない可能性があります。 キャプチャされたテキストがない場合、[Group](xref:System.Text.RegularExpressions.Group) オブジェクトのプロパティは次の表に示すように設定されます。

  Group プロパティ | [値]
  -------------- | ----- 
  `Success` | `false`
  `Value` | [String.Empty](xref:System.String.Empty) 
  `Length` | 0
 
  具体的な例を次に示します。 正規表現パターン `aaa(bbb)*ccc` では、最初のキャプチャ グループ (部分文字列 "bbb") は&0; 回以上一致できます。 入力文字列 "aaaccc" はパターンに一致するので、キャプチャ グループには一致文字列が含まれません。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "aaa(bbb)*ccc";
        string input = "aaaccc";
        Match match = Regex.Match(input, pattern);
        Console.WriteLine("Match value: {0}", match.Value);
        if (match.Groups[1].Success)
           Console.WriteLine("Group 1 value: {0}", match.Groups[1].Value);
        else
           Console.WriteLine("The first capturing group has no match.");
     }
  }
  // The example displays the following output:
  //       Match value: aaaccc
  //       The first capturing group has no match.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "aaa(bbb)*ccc"
        Dim input As String = "aaaccc"
        Dim match As Match = Regex.Match(input, pattern)
        Console.WriteLine("Match value: {0}", match.Value)
        If match.Groups(1).Success Then
           Console.WriteLine("Group 1 value: {0}", match.Groups(1).Value)
        Else
           Console.WriteLine("The first capturing group has no match.")
       End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match value: aaaccc
  '       The first capturing group has no match.
  ```

* 量指定子は、キャプチャ グループによって定義されたパターンの複数回の出現と一致できます。 この場合、[Group](xref:System.Text.RegularExpressions.Group) オブジェクトの `Value` プロパティと `Length` プロパティには、最後にキャプチャされた部分文字列の情報のみが保持されます。 たとえば、次の正規表現は、ピリオドで終わる&1; 文と一致します。 この正規表現では&2; つのグループ化構成体が使用されています。最初のグループ化構成体は個々の単語および空白文字をキャプチャし、2 番目のグループ化構成体は個々の単語をキャプチャします。 この例の出力結果が示すように、正規表現では文全体が正常にキャプチャされますが、2 番目のキャプチャ グループでは最後の単語のみがキャプチャされます。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = @"\b((\w+)\s?)+\.";
        string input = "This is a sentence. This is another sentence.";
        Match match = Regex.Match(input, pattern);
        if (match.Success)
        {
           Console.WriteLine("Match: " + match.Value);
           Console.WriteLine("Group 2: " + match.Groups[2].Value);
        }   
     }
  }
  // The example displays the following output:
  //       Match: This is a sentence.
  //       Group 2: sentence
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "\b((\w+)\s?)+\."
        Dim input As String = "This is a sentence. This is another sentence."
        Dim match As Match = Regex.Match(input, pattern)
        If match.Success Then
           Console.WriteLine("Match: " + match.Value)
           Console.WriteLine("Group 2: " + match.Groups(2).Value)
        End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match: This is a sentence.
  '       Group 2: sentence
  ```

## <a name="the-capture-collection"></a>CaptureCollection

[Group](xref:System.Text.RegularExpressions.Group) オブジェクトには、最後のキャプチャの情報のみが格納されます。 ただし、キャプチャ グループによって行われたキャプチャのセット全体は、[Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) プロパティによって返される [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトから取得できます。 コレクションの各メンバーは、キャプチャ グループによって行われたキャプチャを表す [Capture](xref:System.Text.RegularExpressions.Capture) オブジェクトです。キャプチャされた順序 (したがって、キャプチャされた文字列が左から右に入力文字列と照合された順序) で並びます。 コレクション内の個々の [Capture](xref:System.Text.RegularExpressions.Capture) オブジェクトは、次のいずれかの方法で取得できます。 

* `foreach` (C# の場合) や `For Each` (Visual Basic の場合) などの構成体を使用してコレクションを反復処理する。

* [CaptureCollection.Item](xref:System.Text.RegularExpressions.CaptureCollection.Item(System.Int32)) プロパティを使用して特定のオブジェクトをインデックスで取得する。 Item プロパティは、[CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトの既定のプロパティ (Visual Basic の場合) またはインデクサー (C# の場合) です。


量指定子がキャプチャ グループに適用されない場合、[CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトには [Group](xref:System.Text.RegularExpressions.Group) オブジェクトと同じ一致文字列の情報が保持されるので、関心の低い単一の [Capture](xref:System.Text.RegularExpressions.Capture) オブジェクトが含まれます。 量指定子がキャプチャ グループに適用される場合、[CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトにはキャプチャ グループによって行われたすべてのキャプチャが含まれ、コレクションの最後のメンバーは [Group](xref:System.Text.RegularExpressions.Group) オブジェクトと同じキャプチャを表します。 

たとえば、正規表現パターン `((a(b))c)+` (量指定子 `+` は&1; つ以上の文字列が一致することを指定) を使用して文字列 "abcabcabc" から一致する文字列をキャプチャする場合、各 [Group](xref:System.Text.RegularExpressions.Group) オブジェクトの [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) オブジェクトには、3 個のメンバーが含まれることになります。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "((a(b))c)+";
      string input = "abcabcabc";

      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Match: '{0}' at position {1}",  
                           match.Value, match.Index);
         GroupCollection groups = match.Groups;
         for (int ctr = 0; ctr < groups.Count; ctr++) {
            Console.WriteLine("   Group {0}: '{1}' at position {2}", 
                              ctr, groups[ctr].Value, groups[ctr].Index);
            CaptureCollection captures = groups[ctr].Captures;
            for (int ctr2 = 0; ctr2 < captures.Count; ctr2++) {
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", 
                                 ctr2, captures[ctr2].Value, captures[ctr2].Index);
            }                     
         }
      }
   }
}
// The example displays the following output:
//       Match: 'abcabcabc' at position 0
//          Group 0: 'abcabcabc' at position 0
//             Capture 0: 'abcabcabc' at position 0
//          Group 1: 'abc' at position 6
//             Capture 0: 'abc' at position 0
//             Capture 1: 'abc' at position 3
//             Capture 2: 'abc' at position 6
//          Group 2: 'ab' at position 6
//             Capture 0: 'ab' at position 0
//             Capture 1: 'ab' at position 3
//             Capture 2: 'ab' at position 6
//          Group 3: 'b' at position 7
//             Capture 0: 'b' at position 1
//             Capture 1: 'b' at position 4
//             Capture 2: 'b' at position 7
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example dosplays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

次の例では、正規表現 `(Abc)+` を使用して、文字列 "XYZAbcAbcAbcXYZAbcAb" の中から文字列 "Abc" の連続した出現を&1; つ以上検索します。 この例は、[Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) プロパティを使用して、キャプチャした部分文字列の複数のグループを返す方法を示しています。

```csharp
{
   int counter;
   Match m;
   CaptureCollection cc;
   GroupCollection gc;

   // Look for groupings of "Abc".
   Regex r = new Regex("(Abc)+"); 
   // Define the string to search.
   m = r.Match("XYZAbcAbcAbcXYZAbcAb"); 
   gc = m.Groups;

   // Display the number of groups.
   Console.WriteLine("Captured groups = " + gc.Count.ToString());

   // Loop through each group.
   for (int i=0; i < gc.Count; i++) 
   {
      cc = gc[i].Captures;
      counter = cc.Count;

      // Display the number of captures in this group.
      Console.WriteLine("Captures count = " + counter.ToString());

      // Loop through each capture in the group.
      for (int ii = 0; ii < counter; ii++) 
      {
         // Display the capture and its position.
         Console.WriteLine(cc[ii] + "   Starts at character " + 
              cc[ii].Index);
      }
   }
}
// The example displays the following output:
//       Captured groups = 2
//       Captures count = 1
//       AbcAbcAbc   Starts at character 3
//       Captures count = 3
//       Abc   Starts at character 3
//       Abc   Starts at character 6
//       Abc   Starts at character 9  
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

## <a name="the-individual-capture"></a>個々のキャプチャ

[Capture](xref:System.Text.RegularExpressions.Capture) クラスには、単一の部分式キャプチャの結果が含まれます。 一致したテキストが [Capture.Value](xref:System.Text.RegularExpressions.Capture.Value) プロパティに含まれ、一致した部分文字列の入力文字列内での開始位置 (起点を&0; とする) が [Capture.Index](xref:System.Text.RegularExpressions.Capture.Index) プロパティによって示されます。 

次の例では、選択した都市の気温の入力文字列を解析します。 都市とその気温を区切るためにコンマ (",") が使用され、各都市のデータを区切るためにセミコロン (";") が使用されています。 入力文字列全体が単一の一致を表します。 文字列の解析に使用される正規表現パターン `((\w+(\s\w+)*),(\d+);)+` では、都市名が&2; 番目のキャプチャ グループに代入され、気温が&4; 番目のキャプチャ グループに代入されます。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;"; 
      string pattern = @"((\w+(\s\w+)*),(\d+);)+";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Current temperatures:");
         for (int ctr = 0; ctr < match.Groups[2].Captures.Count; ctr++)
            Console.WriteLine("{0,-20} {1,3}", match.Groups[2].Captures[ctr].Value, 
                              match.Groups[4].Captures[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Current temperatures:
//       Miami                 78
//       Chicago               62
//       New York              67
//       San Francisco         59
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;" 
      Dim pattern As String = "((\w+(\s\w+)*),(\d+);)+"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Current temperatures:")
         For ctr As Integer = 0 To match.Groups(2).Captures.Count - 1
            Console.WriteLine("{0,-20} {1,3}", match.Groups(2).Captures(ctr).Value, _
                              match.Groups(4).Captures(ctr).Value)
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Current temperatures:
'       Miami                 78
'       Chicago               62
'       New York              67
'       San Francisco         59
```

正規表現は、次の表に示すように定義されています。

パターン | 説明
------- | -----------
`\w+` | 1 つ以上の単語文字に一致します。
`(\s\w+)*` | 空白文字の後に&1; 個以上の単語文字が続くパターンの&0; 回以上の出現と一致します。 このパターンは、複数の単語で構成される都市名と一致します。 これが&3; 番目のキャプチャ グループです。
`(\w+(\s\w+)*)` | 1 個以上の単語文字の後に空白文字および&1; 個以上の単語文字の&0; 回以上の出現が続くパターンと一致します。 これが&2; 番目のキャプチャ グループです。
`,` | コンマに一致します。
`(\d+)` | 1 桁以上の数字と一致します。 これが&4; 番目のキャプチャ グループです。
`;` | セミコロンと一致します。
`((\w+(\s\w+)*),(\d+);)+` | 単語、追加の単語、コンマ、1 桁以上の数字、およびセミコロンが&1; 回以上続くパターンと一致します。 これが最初のキャプチャ グループです。 
 
## <a name="see-also"></a>関連項目

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[.NET 正規表現](regular-expressions.md)

[正規表現言語 - クイック リファレンス](quick-ref.md)


