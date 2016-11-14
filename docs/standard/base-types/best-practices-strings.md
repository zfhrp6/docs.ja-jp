---
title: "文字列を使用するためのベスト プラクティス"
description: "文字列を使用するためのベスト プラクティス"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b3cefaa4-0a3f-4a96-aba9-1de30fb07c29
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e

---

# <a name="best-practices-for-using-strings"></a>文字列を使用するためのベスト プラクティス

.NET には、ローカライズされたアプリケーションやグローバル化されたアプリケーションを開発するための広範なサポートが用意されており、文字列の並べ替えや表示などの一般的な操作を実行するときに、現在のカルチャの規則や特定のカルチャの規則を簡単に適用できるようになっています。 しかし、文字列の並べ替えや比較の操作は、必ずしもカルチャに依存するとは限りません。 たとえば、アプリケーションが内部で使用する文字列は、通常、すべてのカルチャで同じように処理される必要があります。 XML タグ、HTML タグ、ユーザー名、ファイル パス、システム オブジェクトの名前などのカルチャに依存しない文字列データがカルチャに依存するかのように解釈されると、アプリケーション コードで軽度のバグが発生したり、パフォーマンスが低下したり、場合によってはセキュリティの問題を引き起こしたりする可能性があります。

ここでは、.NET の文字列の並べ替え、比較、および大文字と小文字の区別のメソッドについて検討し、適切な文字列処理メソッドを選択するための推奨事項と、文字列処理メソッドに関する追加情報を紹介します。 また、数値データ、日時データなど、書式付きデータを表示および格納のために処理する方法についても説明します。 

この記事は、次のセクションで構成されています。

* [文字列の使用に関する推奨事項](#recommendations-for-string-usage)

* [文字列比較の明示的な指定](#specifying-string-comparisons-explicitly)

* [文字列比較の詳細](#the-details-of-string-comparison)

* [メソッド呼び出しに使用する StringComparison メンバーの選択](#choosing-a-stringcomparison-member-for-your-method-call)

* [一般的な文字列比較メソッド](#common-string-comparison-methods)

* [間接的に文字列比較を実行するメソッド](#methods-that-perform-string-comparison-indirectly)

* [書式設定されたデータを表示および保持する](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a>文字列の使用に関する推奨事項

.NET による開発で文字列を使用するときの簡単な推奨事項を次に示します。 

* 文字列操作に対して文字列比較の規則を明示的に指定するオーバーロードを使用します。 そのためには、通常、[StringComparison](xref:System.StringComparison) 型のパラメーターを持つメソッド オーバーロードを呼び出します。

* カルチャに依存しない文字列照合の安全な既定の方法として、[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) を使用して比較を行います。

* パフォーマンスを向上させるには、[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) による比較を使用します。

* ユーザーに出力を表示する場合は、[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) に基づく文字列操作を使用します。

* 比較が言語的な意味を持たない場合 (記号としての比較など) は、[CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) に基づく文字列操作ではなく、非言語的な [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 値または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 値を使用します。

* 比較のために文字列を正規化する場合は、[String.ToLowerInvariant](xref:System.String.ToLowerInvariant) メソッドではなく [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) メソッドを使用します。

* 2 つの文字列が等価かどうかをテストするには、[String](xref:System.String) `Equals` メソッドのオーバーロードを使用します。

* [String](xref:System.String) `Compare` メソッドと [String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドのオーバーロードは、文字列を並べ替える場合に使用し、文字列の等価性を確認する場合には使用しません。

* 数値、日付など、文字列以外のデータをユーザー インターフェイスに表示するには、カルチャに依存する書式設定を使用します。 文字列以外のデータを文字列形式で保持するには、インバリアント カルチャを使用する書式設定を使用します。

文字列を使用する際に避ける必要があることを次に示します。

* 文字列操作に対して文字列比較の規則を明示的または暗黙的に指定しないオーバーロードは使用しないでください。 

* 2 つの文字列が等価かどうかを確認する場合に、[String](xref:System.String) `Compare` メソッドまたは [String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドのオーバーロードで戻り値が 0 かどうかをテストする方法は使用しないでください。

* 数値データや日時データを文字列形式で保持する場合は、カルチャに依存する書式設定を使用しないでください。

## <a name="specifying-string-comparisons-explicitly"></a>文字列比較の明示的な指定

.NET の文字列操作メソッドは、ほとんどがオーバーロードされています。 通常は、既定の設定をそのまま使用する 1 つまたは複数のオーバーロードと、既定の設定を使用せずに文字列の比較または操作の正確な方法を定義するその他のオーバーロードがあります。 既定の設定に依存しないメソッドには、ほとんどの場合、[StringComparison](xref:System.StringComparison) 型のパラメーターが含まれています。これは、カルチャおよび大文字と小文字の区別によって文字列比較の規則を明示的に指定する列挙型です。 [StringComparison](xref:System.StringComparison) 列挙型のメンバーを次の表に示します。 

StringComparison のメンバー | 説明
----------------------- | -----------
[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) | 現在のカルチャを使用して、大文字と小文字を区別する比較を実行します。
[CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) | 現在のカルチャを使用して、大文字と小文字を区別しない比較を実行します。
[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) | 序数に基づく比較を実行します。
[StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) | 大文字と小文字を区別しない、序数に基づく比較を実行します。

たとえば、文字または文字列に一致する[String](xref:System.String) オブジェクト内の部分文字列のインデックスを返す [String](xref:System.String) `IndexOf` メソッドには、次の 9 つのオーバーロードがあります。

* [IndexOf(Char)](xref:System.String.IndexOf(System.Char))、[IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32))、および [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32))。文字列内の文字の序数に基づく (大文字と小文字を区別し、カルチャに依存しない) 検索を既定で実行します。

* [IndexOf(String)](xref:System.String.IndexOf(System.String))、[IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32))、および [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32))。文字列内の部分文字列の、大文字と小文字を区別し、カルチャに依存した検索を既定で実行します。

* [IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison))、[IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison))、および [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison))。比較の形式を指定できる StringComparison 型のパラメーターが含まれています。

次のような理由から、既定値を使用しないオーバーロードを選択することをお勧めします。

* 既定のパラメーターを持つオーバーロードには、序数に基づく比較を実行するもの (文字列インスタンスで [Char](xref:System.Char) を検索するもの) と、カルチャに依存するもの (文字列インスタンスで文字列を検索するもの) があります。 どのメソッドがどの既定値を使用するのかを覚えておくのは容易ではなく、使用するオーバーロードを間違えやすくなります。

* メソッド呼び出しで既定値に依存するコードは、意図が不明確になります。 たとえば、既定値に依存する次の例では、2 つの文字列の序数に基づく比較と言語に基づく比較のどちらを開発者が意図しているのかや、`protocol` と "http" の大文字と小文字が違っていた場合に等価性テストで `false` が返されるのかどうかがわかりにくくなっています。

  ```csharp
  string protocol = GetProtocol(url);       
  if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
     // ...Code to handle HTTP protocol.
  }
  else {
     throw new InvalidOperationException();
  }
  ```

  ```vb
  Dim protocol As String = GetProtocol(url)       
  If String.Equals(protocol, "http") Then
    ' ...Code to handle HTTP protocol.
  Else
     Throw New InvalidOperationException()
  End If
  ```

一般的には、既定値に依存しないメソッドを呼び出すことをお勧めします。そうすると、コードの意図が明確になります。 その結果、コードが読みやすくなるため、デバッグや保守も容易になります。 次の例では、前の例で発生した問題に対応します。 序数比較を使用することと、大文字と小文字の違いを無視することを指定します。 

```csharp
string protocol = GetProtocol(url);       
if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
   // ...Code to handle HTTP protocol.
}
else {
   throw new InvalidOperationException();
}
```

```vb
Dim protocol As String = GetProtocol(url)       
If String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase) Then
   ' ...Code to handle HTTP protocol.
Else
   Throw New InvalidOperationException()
End If
```

## <a name="the-details-of-string-comparison"></a>文字列比較の詳細

文字列比較は、多くの文字列関連操作 (特に並べ替えおよび等価性テスト) の中核です。 文字列は、決まった順序で並べられています。たとえば、文字列の並べ替え済みリストで "my" が "string" の前にある場合は、比較で "my" が "string" 以下になる必要があります。 また、比較は等価性を暗黙的に定義します。 比較演算では、等価と見なされた文字列に対して 0 が返されます。 これは、どちらの文字列ももう一方の文字列より小さくないという意味に解釈するとわかりやすくなります。 文字列に関係する、意味のある操作のほとんどには、他の文字列との比較か、正しく定義された並べ替え操作の実行のいずれかまたは両方の処理が含まれています。

しかし、2 つの文字列の等価性や並べ替え順序を評価する場合、正しい結果は 1 つではありません。結果は、文字列の比較に使用される基準に依存するためです。 特に、序数に基づく文字列比較や、現在のカルチャまたはインバリアント カルチャ (英語をベースとする、ロケールに依存しないカルチャ) の大文字と小文字の規則や並べ替えの規則に基づく文字列比較では、さまざまな結果が返される可能性があります。

### <a name="string-comparisons-that-use-the-current-culture"></a>現在のカルチャを使用する文字列比較

文字列を比較するときの基準として現在のカルチャの規則が使用される場合があります。 現在のカルチャに基づく比較では、スレッドの現在のカルチャ (ロケール) が使用されます。 言語的な意味を持つデータや、カルチャに依存したユーザー操作を反映するデータに対しては、常に現在のカルチャに基づく比較を使用する必要があります。 

しかし、.NET の比較や大文字と小文字の区別の動作は、カルチャによって変わります。 たとえば、開発されたコンピューターとは異なるカルチャのコンピューターでアプリケーションが実行された場合や、実行中のスレッドのカルチャが変更された場合などに、この変化が生じます。 これは意図的な動作ですが、多くの開発者にはまだあまり知られていません。 次の例は、英語 (米国) ("en-US") とスウェーデン語 ("sv-SE") のカルチャの並べ替え順序の違いを示しています。 並べ替えられた文字列配列で、"ångström"、"Windows"、および "Visual Studio" の位置が違っていることに注目してください。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] values= { "able", "ångström", "apple", "Æble", 
                         "Windows", "Visual Studio" };
      Array.Sort(values);
      DisplayArray(values);

      // Change culture to Swedish (Sweden).
      string originalCulture = CultureInfo.CurrentCulture.Name;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("sv-SE");
      Array.Sort(values);
      DisplayArray(values);

      // Restore the original culture.
      Thread.CurrentThread.CurrentCulture = new CultureInfo(originalCulture);
    }

    private static void DisplayArray(string[] values)
    {
      Console.WriteLine("Sorting using the {0} culture:",  
                        CultureInfo.CurrentCulture.Name);
      foreach (string value in values)
         Console.WriteLine("   {0}", value);

      Console.WriteLine();
    }
}
// The example displays the following output:
//       Sorting using the en-US culture:
//          able
//          Æble
//          ångström
//          apple
//          Visual Studio
//          Windows
//       
//       Sorting using the sv-SE culture:
//          able
//          Æble
//          apple
//          Windows
//          Visual Studio
//          ångström
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim values() As String = { "able", "ångström", "apple", _
                                 "Æble", "Windows", "Visual Studio" }
      Array.Sort(values)
      DisplayArray(values)

      ' Change culture to Swedish (Sweden).
      Dim originalCulture As String = CultureInfo.CurrentCulture.Name
      Thread.CurrentThread.CurrentCulture = New CultureInfo("sv-SE")
      Array.Sort(values)
      DisplayArray(values)

      ' Restore the original culture.
      Thread.CurrentThread.CurrentCulture = New CultureInfo(originalCulture)
    End Sub

    Private Sub DisplayArray(values() As String)
      Console.WRiteLine("Sorting using the {0} culture:", _ 
                        CultureInfo.CurrentCulture.Name)
      For Each value As String In values
         Console.WriteLine("   {0}", value)
      Next
      Console.WriteLine()   
    End Sub
End Module
' The example displays the following output:
'       Sorting using the en-US culture:
'          able
'          Æble
'          ångström
'          apple
'          Visual Studio
'          Windows
'       
'       Sorting using the sv-SE culture:
'          able
'          Æble
'          apple
'          Windows
'          Visual Studio
'          ångström
```

現在のカルチャを使用する、大文字と小文字を区別しない比較は、スレッドの現在のカルチャの大文字と小文字の区別の規則が無視される以外は、カルチャに依存した比較と同じです。 この動作も、並べ替え順序に影響する場合があります。 

現在のカルチャのセマンティクスを使用する比較は、次のメソッドで既定で使用されます。

* [StringComparison](xref:System.StringComparison) パラメーターを含まない [String](xref:System.String) `Compare` オーバーロード。

* [String.CompareTo](xref:System.String.CompareTo(System.String)) オーバーロード。

* 既定の [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) メソッド。 

* 既定の [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) メソッド。

* 検索パラメーターとして [String](xref:System.String) を受け取る、[StringComparison](xref:System.StringComparison) パラメーターを持たない [String](xref:System.String) `IndexOf` のオーバーロード。

* 検索パラメーターとして [String](xref:System.String) を受け取る、[StringComparison](xref:System.StringComparison) パラメーターを持たない [String](xref:System.String) `LastIndexOf` のオーバーロード。

どのような場合でも、[StringComparison](xref:System.StringComparison) パラメーターを持つオーバーロードを呼び出して、メソッド呼び出しの意図を明確にすることをお勧めします。 

非言語的な文字列データが言語的に解釈されたり、特定のカルチャの文字列データが別のカルチャの規則で解釈されたりすると、軽度のバグやあまり軽度でないバグが発生する可能性があります。 その典型的な例が、トルコ語の I の問題です。

英語 (米国) を含むほぼすべてのラテン アルファベットでは、文字 "i" (\u0069) は "I" (\u0049) の小文字版です。 この大文字と小文字の規則は、このようなカルチャでプログラミングを行う人にとってはすぐに当たり前のことになります。 しかし、トルコ語 ("tr-TR") のアルファベットには、"i" の大文字版である "ドット付きの I" ("İ" (\u0130)) や、 大文字にすると "I" になる小文字の "ドットなしの i" ("ı" (\u0131)) があります。 この動作は、アゼルバイジャン語 ("az") のカルチャでも発生します。

したがって、"i" を大文字にしたり "I" を小文字にしたりする動作に関する前提は、すべてのカルチャで有効なわけではありません。 文字列比較ルーチンの既定のオーバーロードを使用すると、カルチャ間の差異の影響を受けることになります。 また、非言語的なデータを比較する場合も、既定のオーバーロードを使用すると望ましくない結果が返される可能性があります。たとえば次の例では、文字列 "file" と "FILE" の大文字と小文字を区別しない比較を実行しようとしています。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fileUrl = "file";
      Thread.CurrentThread.CurrentCulture = new CultureInfo("en-US");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                       fileUrl.StartsWith("FILE", true, null));
      Console.WriteLine();

      Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                        fileUrl.StartsWith("FILE", true, null));
   }
}
// The example displays the following output:
//       Culture = English (United States)
//       (file == FILE) = True
//       
//       Culture = Turkish (Turkey)
//       (file == FILE) = False
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fileUrl = "file"
      Thread.CurrentThread.CurrentCulture = New CultureInfo("en-US")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                       fileUrl.StartsWith("FILE", True, Nothing))
      Console.WriteLine()

      Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                        fileUrl.StartsWith("FILE", True, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Culture = English (United States)
'       (file == FILE) = True
'       
'       Culture = Turkish (Turkey)
'       (file == FILE) = False
```

この比較は、セキュリティが重要となる状況でカルチャが不注意に使用されると、重大な問題を引き起こす可能性があります。 `IsFileURI("file:")` などのメソッド呼び出しは、現在のカルチャが英語 (米国) の場合は `true` を返しますが、現在のカルチャがトルコ語の場合は `false` を返します。 したがって、"FILE:" で始まる URI へのアクセスを大文字と小文字の区別なくブロックするセキュリティ対策は、トルコ語のシステムでは攻略される可能性があります。

```csharp
public static bool IsFileURI(String path) 
{
   return path.StartsWith("FILE:", true, null);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
   Return path.StartsWith("FILE:", True, Nothing)
End Function
```

この例の "file:" は、カルチャに依存しない非言語的な識別子として解釈されるものなので、コードを次のように書き換える必要があります。

```csharp
public static bool IsFileURI(string path) 
{
   return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
    Return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase)
End Function
```

## <a name="ordinal-string-operations"></a>序数に基づく文字列操作

メソッド呼び出しで [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 値または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 値を指定すると、非言語的な比較が行われ、自然言語の特性は無視されます。 これらの [StringComparison](xref:System.StringComparison) 値を使用して呼び出されたメソッドでは、文字列操作の判断が、大文字と小文字の指定、またはカルチャでパラメーター化される同等の表ではなく、単純なバイト比較に基づいて行われます。 これにより、ほとんどの場合に文字列が意図されたとおりに解釈され、コードの実行速度と信頼性も向上します。 

序数に基づく比較とは、各文字列の各バイトが言語的に解釈されずに比較される文字列比較です (たとえば、"windows" と "Windows" は一致しません)。 文字列が厳密に一致する必要がある状況や、慎重な照合ポリシーが求められる状況では、この比較を使用します。 また、序数に基づく比較は最も高速な比較演算でもあります。これは、結果を判定するときに言語の規則が適用されないためです。

.NET の文字列には、null 文字が埋め込まれる場合があります。 序数に基づく比較とカルチャに依存した比較 (インバリアント カルチャを使用する比較を含む) の最も明白な違いの 1 つは、文字列に埋め込まれた null 文字の処理に関連しています。 これらの文字は、[String](xref:System.String) `Compare` メソッドや [String](xref:System.String) `Equals` メソッドを使用して、カルチャに依存した比較 (インバリアント カルチャを使用する比較を含む) を実行する場合には無視されます。 その結果、カルチャに依存した比較では、null 文字が埋め込まれた文字列と null 文字が埋め込まれていない文字列が等価と見なされる可能性があります。 

> [!IMPORTANT]
> 埋め込まれた null 文字は、文字列比較メソッドでは無視されますが、文字列検索メソッド ([String.Contains](xref:System.String.Contains(System.String))、[String.EndsWith](xref:System.String.EndsWith(System.String))、[String.IndexOf](xref:System.String.IndexOf(System.Char))、[String.LastIndexOf](xref:System.String.LastIndexOf(System.String))、[String.StartsWith](xref:System.String.StartsWith(System.String)) など) では無視されません。 

次の例では、文字列 "Aa" と、"A" と "a" の間にいくつかの null 文字が埋め込まれた類似の文字列とのカルチャに依存した比較を実行して、2 つの文字列が等価と見なされることを示しています。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string str1 = "Aa";
      string str2 = "A" + new String('\u0000', 3) + "a";
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                        str1, ShowBytes(str1), str2, ShowBytes(str2));
      Console.WriteLine("   With String.Compare:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.InvariantCulture));

      Console.WriteLine("   With String.Equals:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.InvariantCulture));
   }

   private static string ShowBytes(string str)
   {
      string hexString = String.Empty;
      for (int ctr = 0; ctr < str.Length; ctr++)
      {
         string result = String.Empty;
         result = Convert.ToInt32(str[ctr]).ToString("X4");
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2);
         hexString += result;
      }
      return hexString.Trim();
   }
}
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Current Culture: 0
//          Invariant Culture: 0
//       With String.Equals:
//          Current Culture: True
//          Invariant Culture: True
```

```vb
Module Example
   Public Sub Main()
      Dim str1 As String = "Aa"
      Dim str2 As String = "A" + New String(Convert.ToChar(0), 3) + "a"
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                        str1, ShowBytes(str1), str2, ShowBytes(str2))
      Console.WriteLine("   With String.Compare:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.InvariantCulture))

      Console.WriteLine("   With String.Equals:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.InvariantCulture))
   End Sub

   Private Function ShowBytes(str As String) As String
      Dim hexString As String = String.Empty
      For ctr As Integer = 0 To str.Length - 1
         Dim result As String = String.Empty
         result = Convert.ToInt32(str.Chars(ctr)).ToString("X4")
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2)
         hexString += result
      Next
      Return hexString.Trim()
   End Function
End Module
```

一方、次の例のように序数に基づく比較を使用すると、これらの文字列は等価とは見なされません。

```csharp
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                  str1, ShowBytes(str1), str2, ShowBytes(str2));
Console.WriteLine("   With String.Compare:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Compare(str1, str2, StringComparison.Ordinal));

Console.WriteLine("   With String.Equals:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Equals(str1, str2, StringComparison.Ordinal));
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Ordinal: 97
//       With String.Equals:
//          Ordinal: False
```

```vb
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                  str1, ShowBytes(str1), str2, ShowBytes(str2))
Console.WriteLine("   With String.Compare:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Compare(str1, str2, StringComparison.Ordinal))

Console.WriteLine("   With String.Equals:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Equals(str1, str2, StringComparison.Ordinal))
' The example displays the following output:
'    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
'       With String.Compare:
'          Ordinal: 97
'       With String.Equals:
'          Ordinal: False
```

序数に基づく比較の次に慎重な方法は、大文字と小文字を区別しない序数に基づく比較です。 この比較では、大文字と小文字の区別のほとんどが無視されます (たとえば、"windows" と "Windows" は一致します)。 ASCII 文字を操作する場合、このポリシーは [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) と同等ですが、通常の ASCII の大文字と小文字の区別が無視されます。 したがって、[A, Z] (\u0041-\u005A) の任意の文字が [a,z] (\u0061-\007A) の対応する文字と一致します。 ASCII の範囲外の大文字と小文字の区別には、インバリアント カルチャのテーブルが使用されます。 次に例を示します。

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

この比較は、次の比較と同等です (ただし、より高速です)。 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

とはいえ、これらの比較はどちらも非常に高速です。

[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) と [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) は、どちらもバイナリ値を直接使用するため、照合に最適です。 比較の設定について確信を持てない場合は、この 2 つのいずれかの値を使用してください。 ただし、これらの値を使用するとバイトごとの比較が行われるため、言語的な順序 (英語の辞書のような順序) ではなくバイナリの順序で並べ替えが行われます。 したがって、結果をユーザーに表示すると、ほとんどの場合不自然に見えます。

序数に基づくセマンティクスは、[StringComparison](xref:System.StringComparison) 引数を含まない [String](xref:System.String) `Equals` のオーバーロード (等値演算子を含む) で既定で使用されます。 どのような場合でも、[StringComparison](xref:System.StringComparison) パラメーターを持つオーバーロードを呼び出すことをお勧めします。

### <a name="string-operations-that-use-the-invariant-culture"></a>インバリアント カルチャを使用する文字列操作

インバリアント カルチャを使用する比較では、静的 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) プロパティから返される [CompareInfo](xref:System.Globalization.CompareInfo) プロパティが使用されます。 この動作は、すべてのシステムで同じです。範囲外の文字は、等価のインバリアント文字と見なされる文字に変換されます。 このポリシーは、同じ文字列動作のセットを複数のカルチャにわたって保持する場合に便利ですが、予期しない結果になることもよくあります。

インバリアント カルチャを使用する、大文字と小文字を区別しない比較でも、静的 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) プロパティから返される静的 [CompareInfo](xref:System.Globalization.CompareInfo) プロパティが比較情報として使用されます。 変換後の文字の大文字と小文字の違いは無視されます。

[CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) オブジェクトによって、[String](xref:System.String) `Compare` メソッドで特定の文字のセットが等価と解釈されます。 たとえば、次の例が等価になるのは、インバリアント カルチャでは妥当です。

InvariantCulture: a + ̊ = å

latin small lette A 文字 "a" (\u0061) は、combining ring above 文字 "+ " ̊" (\u030a) の横にある場合、latin small letter A with ring above 文字 "å" (\u00e5) として解釈されます。 この動作は、次の例に示すように、序数に基づく比較とは異なります。

```csharp
string separated = "\u0061\u030a";
string combined = "\u00e5";

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}",
                  separated, combined, 
                  String.Compare(separated, combined, 
                                 StringComparison.InvariantCulture) == 0);

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}",
                  separated, combined,
                  String.Compare(separated, combined, 
                                 StringComparison.Ordinal) == 0);
// The example displays the following output:
//    Equal sort weight of a° and å using InvariantCulture: True
//    Equal sort weight of a° and å using Ordinal: False 
```

```vb
Dim separated As String = ChrW(&h61) + ChrW(&h30a)
Dim combined As String = ChrW(&he5)

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _ 
                                 StringComparison.InvariantCulture) = 0)

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _
                                 StringComparison.Ordinal) = 0)
' The example displays the following output:
'    Equal sort weight of a° and å using InvariantCulture: True
'    Equal sort weight of a° and å using Ordinal: False
```

ファイル名やクッキーなど、"å" のような組み合わせが出現する可能性がある要素を解釈する場合にも、序数に基づく比較を使用するのが最も明確かつ適切な方法になります。

結局のところ、インバリアント カルチャには、比較に使用する際に便利なプロパティがほとんどありません。 インバリアント カルチャを使用すると、言語的な意味を持つ形で比較が行われるため、記号の完全な等価性は保証されません。その一方で、特定のカルチャでの表示にも適していません。 たとえば、表示する並べ替え済みの識別子のリストを含む大きなデータ ファイルがアプリケーションに付属している場合に、そのリストにエントリを追加するには、インバリアント スタイルの並べ替えを使用する挿入が必要になります。

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>メソッド呼び出しに使用する StringComparison メンバーの選択

文字列のセマンティックなコンテキストと [StringComparison](xref:System.StringComparison) 列挙型のメンバーとの対応関係の概要を次の表に示します。

データ | 動作 | 対応する System.StringComparison 値
---- | -------- | -------------------------------------------
大文字と小文字が区別される内部識別子、XML や HTTP などの標準の、大文字と小文字が区別される識別子、または大文字と小文字が区別されるセキュリティ関連の設定。 | バイトが正確に一致する非言語的識別子。 | [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)
大文字と小文字が区別されない内部識別子、XML や HTTP などの標準の、大文字と小文字が区別される識別子、ファイル パス、レジストリ キーと値、環境変数、リソース識別子 (ハンドル名など)、または大文字と小文字が区別されないセキュリティ関連の設定。 | 大文字と小文字の区別に関係ない非言語的識別子。 | [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase)
ユーザーに表示されるデータまたはほとんどのユーザーの入力。 | 特定の言語の規則を必要とするデータ。 | [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) または [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)

## <a name="common-string-comparison-methods"></a>一般的な文字列比較メソッド

以降では、文字列比較でよく使用されるメソッドについて説明します。

### <a name="stringcompare"></a>String.Compare

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

このメソッドは文字列解釈の中心的な操作となるため、メソッド呼び出しのすべてのインスタンスを調べて、文字列を現在のカルチャに従って解釈するべきか、カルチャから切り離して (記号として) 扱うべきかどうかを確認する必要があります。 ほとんどは後者であるため、その場合は代わりに [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) の比較を使用します。

[CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) プロパティから返される [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) クラスにも、[CompareOptions](xref:System.Globalization.CompareOptions) フラグ列挙体でさまざまな照合方法 (序数に基づく、空白文字を無視する、カナ型を無視するなど) を指定できる [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) メソッドが含まれています。 

### <a name="stringcompareto"></a>String.CompareTo

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

このメソッドには、現時点では、[StringComparison](xref:System.StringComparison) 型を指定するオーバーロードはありません。 通常は、このメソッドを推奨される [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) の形式に変換できます。

このメソッドは、[IComparable](xref:System.IComparable) インターフェイスと [IComparable&lt;T&gt;](xref:System.IComparable%601) インターフェイスを実装する型に実装されます。 このメソッドには[StringComparison](xref:System.StringComparison) パラメーターのオプションがないため、実装する型のコンストラクターで [StringComparer](xref:System.StringComparer) を指定できるようにするのが一般的です。 次の例では、クラス コンストラクターに [StringComparer](xref:System.StringComparer) パラメーターを含む `FileName` クラスを定義しています。 この [StringComparer](xref:System.StringComparer) オブジェクトは、その後、`FileName.CompareTo` メソッドで使用されています。

```csharp
using System;

public class FileName : IComparable
{
   string fname;
   StringComparer comparer; 

   public FileName(string name, StringComparer comparer)
   {
      if (String.IsNullOrEmpty(name))
         throw new ArgumentNullException("name");

      this.fname = name;

      if (comparer != null)
         this.comparer = comparer;
      else
         this.comparer = StringComparer.OrdinalIgnoreCase;
   }

   public string Name
   {
      get { return fname; }
   }

   public int CompareTo(object obj)
   {
      if (obj == null) return 1;

      if (! (obj is FileName))
         return comparer.Compare(this.fname, obj.ToString());
      else
         return comparer.Compare(this.fname, ((FileName) obj).Name);
   }
}
```

```vb
Public Class FileName : Implements IComparable
   Dim fname As String
   Dim comparer As StringComparer 

   Public Sub New(name As String, comparer As StringComparer)
      If String.IsNullOrEmpty(name) Then
         Throw New ArgumentNullException("name")
      End If

      Me.fname = name

      If comparer IsNot Nothing Then
         Me.comparer = comparer
      Else
         Me.comparer = StringComparer.OrdinalIgnoreCase
      End If      
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return fname
      End Get   
   End Property

   Public Function CompareTo(obj As Object) As Integer _
          Implements IComparable.CompareTo
      If obj Is Nothing Then Return 1

      If Not TypeOf obj Is FileName Then
         obj = obj.ToString()
      Else
         obj = CType(obj, FileName).Name
      End If         
      Return comparer.Compare(Me.fname, obj)
   End Function
End Class
```

### <a name="stringequals"></a>String.Equals

既定の解釈: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)。

[String](xref:System.String) クラスで等価性テストを実行するには、`Equals` メソッド (静的メソッドまたはインスタンス メソッド) のオーバーロードを呼び出すか、静的等値演算子を使用します。 これらのオーバーロードと演算子では、序数に基づく比較が既定で使用されますが、 序数に基づく比較を実行する場合でも、[StringComparison](xref:System.StringComparison) 型を明示的に指定するオーバーロードを呼び出すことをお勧めします。これにより、特定の文字列解釈のコードを検索しやすくなります。 

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper と String.ToLower

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

これらのメソッドを使用するときには注意が必要です。というのも、文字列を大文字や小文字に強制的に変換する操作は、文字列を大文字と小文字の区別に関係なく比較するための小規模の正規化としてよく使用されるからです。 その場合は、大文字と小文字を区別しない比較を使用することを検討してください。 

[String.ToUpperInvariant](xref:System.String.ToUpperInvariant) メソッドと [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) メソッドも使用できます。 [ToUpperInvariant](xref:System.String.ToUpperInvariant) は、大文字と小文字を正規化するための標準的な方法です。 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) を使用して行われる比較は、動作の内容を見ると、両方の文字列引数に対して [ToUpperInvariant](xref:System.String.ToUpperInvariant) を呼び出し、[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) を使用して比較を行うという、2 つの呼び出しの組み合わせです。

特定のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを渡してそのカルチャで大文字および小文字への変換を行うためのオーバーロードもあります。

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper と Char.ToLower

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

これらのメソッドの動作は、上で説明した [String.ToUpper](xref:System.String.ToUpper) メソッドおよび [String.ToLower](xref:System.String.ToLower) メソッドと同様です。

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith と String.EndsWith

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

これらのメソッドは、いずれもカルチャに依存した比較を既定で実行します。

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf と String.LastIndexOf

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

これらのメソッドの既定のオーバーロードは、比較の実行方法が一貫していません。 [Char](xref:System.Char) パラメーターを含むすべての [String](xref:System.String) `IndexOf` メソッドと [String](xref:System.String) `LastIndexOf` メソッドは、序数に基づく比較を実行します。一方、[String](xref:System.String) パラメーターを含む既定の [String](xref:System.String) `IndexOf` メソッドと [String`](xref:System.String) `LastIndexOf` メソッドは、カルチャに依存した比較を実行します。 

` `IndexOf` or `LastIndexOf` メソッドを呼び出して、現在のインスタンスで検索する文字列を渡す場合は、[StringComparison](xref:System.StringComparison) 型を明示的に指定するオーバーロードを呼び出すことをお勧めします。 [Char](xref:System.Char) 引数を含むオーバーロードでは、[StringComparison](xref:System.StringComparison) 型を指定することはできません。

## <a name="methods-that-perform-string-comparison-indirectly"></a>間接的に文字列比較を実行するメソッド

文字列比較を中心的な操作とする非文字列メソッドの中には、[StringComparer](xref:System.StringComparer) 型を使用するものがあります。 [StringComparer](xref:System.StringComparer) クラスには、[StringComparer](xref:System.StringComparer) のインスタンスを返す静的プロパティが 4 つ含まれています。これらのインスタンスの `Compare` メソッドは、次の種類の文字列比較を実行します。

* 現在のカルチャを使用する、カルチャに依存した文字列比較。 この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) プロパティによって返されます。

* 現在のカルチャを使用する、大文字と小文字を区別しない比較。 この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) プロパティによって返されます。

* 序数に基づく比較。 この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.Ordinal](xref:System.StringComparer.Ordinal) プロパティによって返されます。 

* 大文字と小文字を区別しない、序数に基づく比較。 この [StringComparer](xref:System.StringComparer) オブジェクトは、[StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) プロパティによって返されます。

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort と Array.BinarySearch

既定の解釈: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

データをコレクションに格納したり、永続化されたデータをファイルやデータベースからコレクションに読み取ったりするときに現在のカルチャを切り替えると、コレクション内のインバリアントが無効になる可能性があります。 [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) メソッドでは、配列内で検索する要素が既に並べ替えられていると見なされます。 [Array.Sort](xref:System.Array.Sort(System.Array)) メソッドは、配列内の文字列要素を並べ替えるために、[String] `Compare` メソッドを呼び出して個々の要素を順序付けます。 配列の並べ替えが行われてから内容の検索が行われるまでの間にカルチャが変更される場合、カルチャに依存した比較子を使用するのは危険です。 たとえば、次のコードでは、`Thread.CurrentThread.CurrentCulture` プロパティによって暗黙的に提供される比較子で格納と取得の操作が行われています。 `StoreNames` の呼び出しと `DoesNameExist` の呼び出しの間にカルチャが変更されると (この 2 つのメソッドの呼び出しの間に配列の内容が永続化された場合には特に)、バイナリ サーチが失敗する可能性があります。 

```csharp
// Incorrect.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names); // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name) >= 0);  // Line B.
}
```

```vb
' Incorrect.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names)          ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name) >= 0      ' Line B.
End Function
```

次の例は、推奨されるバリエーションを示しています。ここでは、配列の並べ替えと検索の両方に、同じ序数に基づく (カルチャに依存しない) 比較メソッドが使用されています。 コードの変更は、2 つの例の `Line A` および `Line B` というラベルが付いた行に反映されています。

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.Ordinal);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.Ordinal) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.Ordinal)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.Ordinal) >= 0      ' Line B.
End Function
```

このデータを永続化して別のカルチャのシステムに移動したり、データをユーザーに表示するために並べ替えたりする場合は、`StringComparison.InvariantCulture` を使用することを検討してください。そうすると、ユーザー出力のために言語的な操作を行っても、カルチャの変更による影響を受けることはありません。 次の例では、前の 2 つの例を変更して、配列の並べ替えと検索にインバリアント カルチャを使用しています。

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.InvariantCulture);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.InvariantCulture) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.InvariantCulture)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.InvariantCulture) >= 0      ' Line B.
End Function
```

### <a name="collections-example-hashtable-constructor"></a>コレクションの例: Hashtable のコンストラクター

文字列のハッシュも、文字列の比較方法の影響を受ける操作の 1 つです。 

次の例では、[StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) プロパティによって返される [StringComparer](xref:System.StringComparer) オブジェクトを渡すことによって [Hashtable](xref:System.Collections.Hashtable) オブジェクトをインスタンス化します。 [StringComparer](xref:System.StringComparer) から派生するクラス [StringComparer](xref:System.StringComparer)は [IEqualityComparer](xref:System.Collections.IEqualityComparer) インターフェイスを実装するため、その [GetHashCode](xref:System.Collections.IEqualityComparer) メソッドを使用して、ハッシュ テーブルの文字列のハッシュ コードを計算しています。

```csharp
const int initialTableCapacity = 100;
Hashtable h;

public void PopulateFileTable(string directory)
{
   h = new Hashtable(initialTableCapacity, 
                     StringComparer.OrdinalIgnoreCase);

   foreach (string file in Directory.GetFiles(directory))
         h.Add(file, File.GetCreationTime(file));
}

public void PrintCreationTime(string targetFile)
{
   Object dt = h[targetFile];
   if (dt != null)
   {
      Console.WriteLine("File {0} was created at time {1}.",
         targetFile, 
         (DateTime) dt);
   }
   else
   {
      Console.WriteLine("File {0} does not exist.", targetFile);
   }
}
```

```vb
Const initialTableCapacity As Integer = 100
Dim h As Hashtable

Public Sub PopulateFileTable(dir As String)
   h = New Hashtable(initialTableCapacity, _
                     StringComparer.OrdinalIgnoreCase)

   For Each filename As String In Directory.GetFiles(dir)
      h.Add(filename, File.GetCreationTime(filename))
   Next                        
End Sub

Public Sub PrintCreationTime(targetFile As String)
   Dim dt As Object = h(targetFile)
   If dt IsNot Nothing Then
      Console.WriteLine("File {0} was created at {1}.", _
         targetFile, _
         CDate(dt))
   Else
      Console.WriteLine("File {0} does not exist.", targetFile)
   End If
End Sub  
```

## <a name="displaying-and-persisting-formatted-data"></a>書式設定されたデータを表示および保持する

数値、日時など、文字列以外のデータをユーザーに表示するには、ユーザーのカルチャ設定を使用して書式設定します。 既定では、数値型と日時型の [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッドと `ToString` メソッドは、書式設定の操作に現在のスレッド カルチャを使用します。 書式設定メソッドで現在のカルチャを使用することを明示的に指定するには、provider パラメーターを含む書式設定メソッド ([String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))、[DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) など) のオーバーロードを呼び出して、そのパラメーターを [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) プロパティに渡します。 

文字列以外のデータは、バイナリ データまたは書式付きデータとして保持できます。 書式付きデータとして保存するには、*provider* パラメーターを含む書式指定メソッドのオーバーロードを呼び出し、そのパラメーターを [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) プロパティに渡す必要があります。 インバリアント カルチャは、カルチャとコンピューターに依存しない書式付きデータに一貫した書式を提供します。 これに対し、インバリアント カルチャ以外のカルチャを使用して書式設定するデータの保持には、さまざまな制限があります。 

* カルチャが異なるシステムでデータを取得したり、現在のシステムのユーザーが現在のカルチャを変更してデータを取得しようとしたりすると、そのデータは使用できない可能性があります。 

* 特定のコンピューターのカルチャのプロパティは、その標準の値とは異なる場合があります。 常に、ユーザーはカルチャに依存した表示設定をカスタマイズする可能性があります。 このため、ユーザーがカルチャの設定をカスタマイズすると、システムに保存されている書式付きデータが読み取ることができなくなる場合があります。 コンピューター間の書式付きデータの移植性がさらに制限される可能性があります。 

* 数値や日時の書式設定を制御する国際的、地域的、または国内の標準は時間と共に変化するため、これらの変化はオペレーティング システムの更新プログラムに組み込まれています。 書式設定の規則が変わると、以前の規則に従って書式設定されたデータが読み取ることができなくなる場合があります。 

次に、カルチャに依存する書式設定を使用してデータを保持すると移植性が制限される例を示します。 この例では、日時の値の配列をファイルに保存します。 これらは、英語 (米国) のカルチャの規則を使用して書式設定されています。 現在のスレッド カルチャがフランス語 (スイス) に変更されると、アプリケーションは現在のカルチャの書式設定規則を使用して保存された値を読み取ることを試みます。 2 つのデータ項目の読み取りを試みると、[FormatException](xref:System.FormatException) 例外がスローされます。日付の配列には、[MinValue](xref:System.DateTime.MinValue) に等しい 2 つの間違った要素が含まれることになります。 

```csharp
using System;
using System.Globalization;
using System.IO;
using System.Text;
using System.Threading;

public class Example
{
   private static string filename = @".\dates.dat";

   public static void Main()
   {
      DateTime[] dates = { new DateTime(1758, 5, 6, 21, 26, 0), 
                           new DateTime(1818, 5, 5, 7, 19, 0), 
                           new DateTime(1870, 4, 22, 23, 54, 0),  
                           new DateTime(1890, 9, 8, 6, 47, 0), 
                           new DateTime(1905, 2, 18, 15, 12, 0) }; 
      // Write the data to a file using the current culture.
      WriteData(dates);
      // Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH");
      // Read the data using the current culture.
      DateTime[] newDates = ReadData();
      foreach (var newDate in newDates)
         Console.WriteLine(newDate.ToString("g"));
   }

   private static void WriteData(DateTime[] dates) 
   {
      StreamWriter sw = new StreamWriter(filename, false, Encoding.UTF8);    
      for (int ctr = 0; ctr < dates.Length; ctr++) {
         sw.Write("{0}", dates[ctr].ToString("g", CultureInfo.CurrentCulture));
         if (ctr < dates.Length - 1) sw.Write("|");   
      }      
      sw.Close();
   }

   private static DateTime[] ReadData() 
   {
      bool exceptionOccurred = false;

      // Read file contents as a single string, then split it.
      StreamReader sr = new StreamReader(filename, Encoding.UTF8);
      string output = sr.ReadToEnd();
      sr.Close();   

      string[] values = output.Split( new char[] { '|' } );
      DateTime[] newDates = new DateTime[values.Length]; 
      for (int ctr = 0; ctr < values.Length; ctr++) {
         try {
            newDates[ctr] = DateTime.Parse(values[ctr], CultureInfo.CurrentCulture);
         }
         catch (FormatException) {
            Console.WriteLine("Failed to parse {0}", values[ctr]);
            exceptionOccurred = true;
         }
      }      
      if (exceptionOccurred) Console.WriteLine();
      return newDates;
   }
}
// The example displays the following output:
//       Failed to parse 4/22/1870 11:54 PM
//       Failed to parse 2/18/1905 3:12 PM
//       
//       05.06.1758 21:26
//       05.05.1818 07:19
//       01.01.0001 00:00
//       09.08.1890 06:47
//       01.01.0001 00:00
//       01.01.0001 00:00
```

```vb
Imports System.Globalization
Imports System.IO
Imports System.Text
Imports System.Threading

Module Example
   Private filename As String = ".\dates.dat"

   Public Sub Main()
      Dim dates() As Date = { #5/6/1758 9:26PM#, #5/5/1818 7:19AM#, _ 
                              #4/22/1870 11:54PM#, #9/8/1890 6:47AM#, _ 
                              #2/18/1905 3:12PM# }
      ' Write the data to a file using the current culture.
      WriteData(dates)
      ' Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH")
      ' Read the data using the current culture.
      Dim newDates() As Date = ReadData()
      For Each newDate In newDates
         Console.WriteLine(newDate.ToString("g"))
      Next
   End Sub

   Private Sub WriteData(dates() As Date)
      Dim sw As New StreamWriter(filename, False, Encoding.Utf8)    
      For ctr As Integer = 0 To dates.Length - 1
         sw.Write("{0}", dates(ctr).ToString("g", CultureInfo.CurrentCulture))
         If ctr < dates.Length - 1 Then sw.Write("|")   
      Next      
      sw.Close()
   End Sub

   Private Function ReadData() As Date()
      Dim exceptionOccurred As Boolean = False

      ' Read file contents as a single string, then split it.
      Dim sr As New StreamReader(filename, Encoding.Utf8)
      Dim output As String = sr.ReadToEnd()
      sr.Close()   

      Dim values() As String = output.Split( {"|"c } )
      Dim newDates(values.Length - 1) As Date 
      For ctr As Integer = 0 To values.Length - 1
         Try
            newDates(ctr) = DateTime.Parse(values(ctr), CultureInfo.CurrentCulture)
         Catch e As FormatException
            Console.WriteLine("Failed to parse {0}", values(ctr))
            exceptionOccurred = True
         End Try
      Next      
      If exceptionOccurred Then Console.WriteLine()
      Return newDates
   End Function
End Module
' The example displays the following output:
'       Failed to parse 4/22/1870 11:54 PM
'       Failed to parse 2/18/1905 3:12 PM
'       
'       05.06.1758 21:26
'       05.05.1818 07:19
'       01.01.0001 00:00
'       09.08.1890 06:47
'       01.01.0001 00:00
'       01.01.0001 00:00
'
```

ただし、[DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 呼び出しと [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)) 呼び出しで [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) プロパティを [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) に置き換えると、保持されている日時データは正常に復元されます。次にその出力を示します。

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a>関連項目

[文字列の操作](manipulating-strings.md)



<!--HONumber=Nov16_HO1-->


