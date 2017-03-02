---
title: "文字列の比較"
description: "文字列の比較"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 47ee37886fa2662a89730e9d52ee04987e37da2f
ms.lasthandoff: 03/02/2017

---

# <a name="comparing-strings"></a>文字列の比較

.NET は、文字列の値を比較するためのメソッドをいくつか提供します。 これらの値の比較メソッドとその説明を次の表に示します。

メソッド名 | 使用
----------- | ---
[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) | 2 つの文字列の値を比較します。 整数値を返します。
[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) | ローカル カルチャに関係なく、2 つの文字列を比較します。 整数値を返します。
[String.CompareTo](xref:System.String.CompareTo(System.String)) | 現在の文字列オブジェクトを別の文字列と比較します。 整数値を返します。
[String.StartsWith](xref:System.String.StartsWith(System.String)) | 文字列が、渡された文字列で始まるかどうかを確認します。 Boolean 値を返します。
[String.EndsWith](xref:System.String.CompareTo(System.String)) | 文字列が、渡された文字列で終わるかどうかを確認します。 Boolean 値を返します。
[String.Equals](xref:System.String.CompareTo(System.String)) | 2 つの文字列が等しいかどうかを確認します。 Boolean 値を返します。
[String.IndexOf](xref:System.String.IndexOf(System.Char)) | 検索対象文字列の先頭から開始して、特定の文字または文字列が見つかったインデックス位置を返します。 整数値を返します。
[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) | 検索対象文字列の末尾から開始して、特定の文字または文字列が見つかったインデックス位置を返します。 整数値を返します。

## <a name="compare"></a>比較

静的な [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、2 つの文字列を詳細に比較する手段を提供します。 このメソッドはカルチャに対応しています。 この機能は、2 つの文字列、または&2; つの文字列の部分文字列を比較するために使用できます。 また、大文字と小文字の区別やカルチャの違いを考慮または無視するためのオーバーロードも用意されています。 このメソッドによって返される可能性のある&3; つの整数値を次の表に示します。 

戻り値 | 条件
------------ | ---------
負の整数 | 最初の文字列は、並べ替え順序が&2; 番目の文字列の前に置かれます。そうでない場合、最初の文字列は `null` です。
0 | 最初の文字列と&2; 番目の文字列は等価です。そうでない場合、両方の文字列が `null` です。
正の整数、または 1 | 最初の文字列は、並べ替え順序が&2; 番目の文字列の後に続きます。そうでない場合、2 番目の文字列は null です。
 
> [!IMPORTANT]
> [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、主に文字列の並べ替えに使用するものです。 等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドを使用しないでください。 2 つの文字列が等価かどうかを判断するには、[String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) メソッドを使用してください。

[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドを使用して、2 つの文字列の相対値を確認する例を次に示します。

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

この例は、コンソールに `-1` と出力します。

## <a name="compareordinal"></a>CompareOrdinal

[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、ローカル カルチャを考慮せずに&2; つの文字列オブジェクトを比較します。 このメソッドの戻り値は、上の表で示した `Compare` メソッドによって返される値と同じです。

> [!IMPORTANT]
> [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、主に文字列の並べ替えに使用するものです。 等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドを使用しないでください。 2 つの文字列が等価かどうかを判断するには、[String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) メソッドを使用してください。

`CompareOrdinal` メソッドを使用して、2 つの文字列の値を比較する例を次に示します。

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

この例は、コンソールに `-32` と出力します。

## <a name="compareto"></a>CompareTo

[String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドは、現在の文字列オブジェクトがカプセル化している文字列を別の文字列またはオブジェクトと比較します。 このメソッドの戻り値は、上の表で示した `String.Compare` メソッドによって返される値と同じです。

> [!IMPORTANT]
> [String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドは、主に文字列の並べ替えに使用するものです。 等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、[String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドを使用しないでください。 2 つの文字列が等価かどうかを判断するには、[String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) メソッドを使用してください。

`String.CompareTo` メソッドを使用して、`string1` オブジェクトを `string2` オブジェクトと比較する例を次に示します。

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

この例は、コンソールに `-1` と出力します。

## <a name="equals"></a>次の値に等しい

[String.Equals](xref:System.String.CompareTo(System.String)) メソッドを使用すると、2 つの文字列が等しいかどうかを簡単に確認できます。 このメソッドは大文字と小文字を区別し、`true` または `false` の Boolean 値を返します。 このメソッドは、次の例に示すように、既存のクラスで使用できます。 `Equals` メソッドを使用して、文字列オブジェクトに "Hello World" という語句が含まれているかどうかを確認する例を次に示します。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

この例は、コンソールに `true` と出力します。

このメソッドは、静的メソッドとしても使用できます。 静的メソッドを使用して、2 つの文字列オブジェクトを比較する例を次に示します。

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

この例は、コンソールに `true` と出力します。

## <a name="startswith-and-endswith"></a>StartsWith と EndsWith

[String.StartsWith](xref:System.String.StartsWith(System.String)) メソッドを使用すると、文字列オブジェクトが、別の文字列を構成している文字と同じ文字で始まっているかどうかを確認できます。 このメソッドは大文字と小文字を区別し、現在の文字列オブジェクトが、渡された文字列で始まる場合は `true`、それ以外の場合は `false` を返します。 このメソッドを使用して、文字列オブジェクトが "Hello" で始まるかどうかを確認する例を次に示します。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

この例は、コンソールに `true` と出力します。

[String.EndsWith](xref:System.String.CompareTo(System.String)) メソッドは、渡された文字列を現在の文字列オブジェクトの末尾にある文字列と比較します。 このメソッドも Boolean 値を返します。 `EndsWith` メソッドを使用して、文字列の末尾を確認する例を次に示します。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

この例は、コンソールに `false` と出力します。

## <a name="indexof-and-lastindexof"></a>IndexOf と LastIndexOf

[String.IndexOf](xref:System.String.IndexOf(System.Char)) メソッドを使用すると、特定の文字が文字列内で最初に出現する位置を確認できます。 このメソッドは大文字と小文字を区別し、文字列の先頭からカウントを開始し、0 から始まるインデックスを使用して、渡された文字が出現する位置を返します。 指定した文字が見つからない場合は、値 –1 を返します。

`IndexOf` メソッドを使用して、'`l`' という文字が文字列内で最初に出現する位置を検索する例を次に示します。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

この例は、コンソールに `2` と出力します。

[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) メソッドは `String.IndexOf` メソッドに似ていますが、指定した文字列が文字列内で最後に出現する位置を返すという点が異なります。 このメソッドは大文字と小文字を区別し、0 から始まるインデックスを使用します。 

`LastIndexOf` メソッドを使用して、'`l`' という文字が文字列内で最後に出現する位置を検索する例を次に示します。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

この例は、コンソールに `9` と出力します。

いずれのメソッドも、[String.Remove](xref:System.String.Remove(System.Int32)) メソッドと組み合わせて使用すると便利です。 `IndexOf` メソッドまたは `LastIndexOf` メソッドのいずれかを使用して文字の位置を取得し、その位置を `Remove method` メソッドに渡すことによって、その文字またはその文字で始まる単語を削除できます。

## <a name="see-also"></a>関連項目

[基本的な文字列操作](basic-string-operations.md)













