---
title: "文字列の埋め込み"
description: "文字列の埋め込み"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 73452c1f432fb8cb50a36e739fb91962693f8e51

---

# <a name="padding-strings"></a>文字列の埋め込み

ある文字の先頭または末尾に文字を埋め込み、合計を指定の長さにするとき、元の文字列で構成される新しい文字列を次の [System.String](xref:System.String) メソッドの 1 つを利用して作成します。 埋め込み文字にはスペースや指定した文字を利用できます。結果的に、右揃えまたは左揃えのように見えます。

メソッド名 | 使用
----------- | ---
[String.PadLeft](xref:System.String.PadLeft(System.Int32)) | 文字列の先頭に文字を埋め込み、合計を指定の長さにします。
[String.PadRight](xref:System.String.PadRight(System.Int32)) | 文字列の末尾に文字を埋め込み、合計を指定の長さにします。

## <a name="padleft"></a>PadLeft

[String.PadLeft](xref:System.String.PadLeft(System.Int32)) メソッドでは、元の文字列の先頭に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。 [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) メソッドでは、空白文字が埋め込み文字として利用されます。[String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) メソッドでは、独自の埋め込み文字を指定できます。

次のコード例では、[PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) メソッドを利用し、長さが 20 文字の新しい文字列を作成します。 この例は、コンソールに "`--------Hello World!`" と出力します。

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a>PadRight

[String.PadRight](xref:System.String.PadRight(System.Int32)) メソッドでは、元の文字列の末尾に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。 [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) メソッドでは、空白文字が埋め込み文字として利用されます。[String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) メソッドでは、独自の埋め込み文字を指定できます。

次のコード例では、[PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) メソッドを利用し、長さが 20 文字の新しい文字列を作成します。 この例は、コンソールに "`Hello World!--------`" と出力します。

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a>関連項目

[基本的な文字列操作](basic-string-operations.md)




<!--HONumber=Nov16_HO1-->


