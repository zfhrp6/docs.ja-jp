---
title: "文字列からの文字のトリムと削除"
description: "文字列からの文字のトリムと削除"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 95d818bc-2661-43f6-adb8-13b53abf9682
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 96cf08c0de8ba73d931d561187369ccf8b091651

---

# <a name="trimming-and-removing-characters-from-strings"></a>文字列からの文字のトリムと削除

文章を個々の単語に分割すると、単語の先頭または末尾に空白が残る場合があります。 そのような場合は、[System.String](https://docs.microsoft.com/dotnet/core/api/System.String) クラスのトリム メソッドのいずれかを使用して、文字列内の指定した位置から任意の数の空白またはその他の文字を削除できます。 使用できるトリム メソッドとその説明を次の表に示します。

メソッド名 | 使用
----------- | ---
[String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | 文字列の先頭と末尾から、空白または文字配列で指定した文字を削除します。
[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) | 文字列の末尾から、文字配列で指定した文字を削除します。
[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) | 文字列の先頭から、文字配列で指定した文字を削除します。
[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) | 文字列内の指定したインデックス位置から、指定した数の文字を削除します。


## <a name="trim"></a>Trim

[String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) メソッドを使用すると、文字列の両端から空白を簡単に削除できます。メソッドの使用例を次に示します。

```csharp
string MyString = " Big   ";
Console.WriteLine("Hello{0}World!", MyString);
string TrimString = MyString.Trim();
Console.WriteLine("Hello{0}World!", TrimString);
//       The example displays the following output:
//             Hello Big   World!
//             HelloBigWorld!
```

```vb
Dim MyString As String = " Big   "
Console.WriteLine("Hello{0}World!", MyString)
Dim TrimString As String = MyString.Trim()
Console.WriteLine("Hello{0}World!", TrimString)
' The example displays the following output:
'       Hello Big   World!
'       HelloBigWorld!
```

文字列の先頭と末尾から、文字配列で指定した文字を削除することもできます。 次に、空白文字、ピリオド、およびアスタリスクを削除する例を示します。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String header = "* A Short String. *";
      Console.WriteLine(header);
      Console.WriteLine(header.Trim( new Char[] { ' ', '*', '.' } ));
   }
}
// The example displays the following output:
//       * A Short String. *
//       A Short String
```

```vb
Module Example
   Public Sub Main()
      Dim header As String = "* A Short String. *"
      Console.WriteLine(header)
      Console.WriteLine(header.Trim( { " "c, "*"c, "."c } ))
   End Sub
End Module
' The example displays the following output:
'       * A Short String. *
'       A Short String
```

## <a name="trimend"></a>TrimEnd

[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドは、文字列の末尾から文字を削除して新しい文字列オブジェクトを作成します。 このメソッドには、削除する文字を指定する文字配列が渡されます。 文字配列内での要素の順序は、トリム操作に影響しません。 トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。

TrimEnd メソッドを使用して文字列の末尾の数文字を削除する例を次に示します。 この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'r'` という文字と `'W'` という文字の順序を逆にしてあります。 このコードは、`MyString` の最後の単語だけでなく、最初の単語の一部も削除します。

```csharp
string MyString = "Hello World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

このコードは、コンソールに `He` と出力します。

[TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドを使用して、文字列の最後の単語を削除する例を次に示します。 このコードでは、`Hello` という単語の後にコンマがありますが、削除する文字の配列にコンマは指定されていないため、コンマの位置でトリムが停止します。

```csharp
string MyString = "Hello, World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello, World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

このコードは、コンソールに `Hello,` と出力します。

## <a name="trimstart"></a>TrimStart

[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) メソッドは [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドと似ていますが、既存の文字列オブジェクトの先頭から文字を削除して新しい文字列を作成する点が異なります。 [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) メソッドには、削除する文字を指定する文字配列が渡されます。 [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドの場合と同様に、文字配列内での要素の順序はトリム操作に影響しません。 トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。

文字列の最初の単語を削除する例を次に示します。 この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'l'` という文字と `'H'` という文字の順序を逆にしてあります。

```csharp
string MyString = "Hello World!";
char[] MyChar = {'e', 'H','l','o',' ' };
string NewString = MyString.TrimStart(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"e","H","l","o"," " }
Dim NewString As String = MyString.TrimStart(MyChar)
Console.WriteLine(NewString)
```

このコードは、コンソールに `World!` と出力します。

## <a name="remove"></a>削除

[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) メソッドは、既存の文字列内の指定した位置を開始位置として、指定した数の文字を削除します。 このメソッドは、インデックスが 0 から始まっていることを前提としています。

文字列の 0 から始まる 5 番目のインデックスを開始位置として、10 文字を削除する例を次に示します。

```csharp
string MyString = "Hello Beautiful World!";
Console.WriteLine(MyString.Remove(5,10));
// The example displays the following output:
//         Hello World!  
```

```vb
Dim MyString As String = "Hello Beautiful World!"
Console.WriteLine(MyString.Remove(5,10))
' The example displays the following output:
'         Hello World!
```

また、[String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) メソッドを呼び出し、置換対象として空の文字列 ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) を指定することで、文字列から指定した文字または部分文字列を削除することもできます。 文字列からすべてのコンマを削除する例を次に示します。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String phrase = "a cold, dark night";
      Console.WriteLine("Before: {0}", phrase);
      phrase = phrase.Replace(",", "");
      Console.WriteLine("After: {0}", phrase);
   }
}
// The example displays the following output:
//       Before: a cold, dark night
//       After: a cold dark night
```

```vb
Module Example
   Public Sub Main()
      Dim phrase As String = "a cold, dark night"
      Console.WriteLine("Before: {0}", phrase)
      phrase = phrase.Replace(",", "")
      Console.WriteLine("After: {0}", phrase)
   End Sub
End Module
' The example displays the following output:
'       Before: a cold, dark night
'       After: a cold dark night
```

## <a name="see-also"></a>関連項目

[基本的な文字列操作](basic-string-operations.md)




<!--HONumber=Nov16_HO1-->


