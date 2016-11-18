---
title: "列挙型書式指定文字列"
description: "列挙型書式指定文字列"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 4d581898-99bc-42c3-816c-d8238f45096f
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 9f5b60a75bf4b92b88d249be2f95f312ddb6909c

---

# <a name="enumeration-format-strings"></a>列挙型書式指定文字列

[Enum.ToString](xref:System.Enum.ToString) メソッドを使用すると、列挙型メンバーの数値、16 進数、または文字列値を表す新しい文字列オブジェクトを作成できます。 このメソッドは、列挙型書式指定文字列のいずれかを使って、返される値を指定します。

次のセクションでは、列挙型書式指定文字列とそれが返す値を一覧表示します。 これらの書式指定子では大文字と小文字は区別されません。

## <a name="the-g-or-g-format-strings"></a>G または g 書式指定文字列

G または g 書式指定文字列は、可能な場合には列挙エントリを文字列値として表示し、それ以外の場合は、現在のインスタンスの整数値を表示します。 列挙型が `Flags` 属性セットで定義されている場合、有効な各エントリの文字列値はコンマで区切られて連結されます。 `Flags` 属性が設定されていない場合、無効な値が数値エントリとして表示されます。 次の例は、G 書式指定子を示しています。

```csharp
Console.WriteLine(ConsoleColor.Red.ToString("G"));         // Displays Red
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("G"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Red.ToString("G"))           ' Displays Red
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("G"))     ' Displays Hidden, Archive
```

## <a name="the-f-or-f-format-strings"></a>F または f 書式指定文字列

F または f 書式指定文字列は、可能な場合には列挙エントリを文字列値として表示します。 (`Flags` 属性が存在しない場合でも) 値が列挙内のエントリの総和として完全に表示できる場合、有効な各エントリの文字列値はコンマで区切られて連結されます。 値が列挙エントリによって完全に特定できない場合、その値は整数値として書式設定されます。 次の例は、F 書式指定子を示しています。

```csharp
Console.WriteLine(ConsoleColor.Blue.ToString("F"));       // Displays Blue
FileAttributes attributes = FileAttributes.Hidden | 
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("F"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Blue.ToString("F"))         ' Displays Blue
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("F"))     ' Displays Hidden, Archive
```

## <a name="the-d-or-d-format-strings"></a>D または d 書式指定文字列

D または d 書式文字列は、列挙エントリを整数値として可能な限り短い表現で表示します。 次の例は、D 書式指定子を示しています。

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("D"));         // Displays 11
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("D"));                // Displays 34
````

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("D"))           ' Displays 11
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("D"))                  ' Displays 34 
```

## <a name="the-x-or-x-format-strings"></a>X または x 書式指定文字列

X または x 書式指定文字列は、列挙エントリを 16 進数値として表示します。 値は、最小の 8 桁の長さにするため、必要に応じて先頭にゼロを付けて表されます。 次の例は、X 書式指定子を示しています。

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("X"));   // Displays 0000000B
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("X"));          // Displays 00000022
```

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("X"))     ' Displays 0000000B
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("X"))            ' Displays 00000022 
```

## <a name="example"></a>例

次の例では、`Red`、`Blue`、`Green` の 3 つのエントリから構成される、`Colors` と呼ばれる列挙型を定義します。

 ```csharp
 public enum Color {Red = 1, Blue = 2, Green = 3}
```

```vb
Public Enum Color
   Red = 1
   Blue = 2
   Green = 3
End Enum
```

列挙型を定義すると、次のようにインスタンスを宣言できます。

```csharp
Color myColor = Color.Green;
```

```vb
Dim myColor As Color = Color.Green
```

これで `Color.ToString(System.String)` メソッドを使用して、渡された書式指定子に応じて、列挙値をさまざまな方法で表示することができます。

```csharp
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("G"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("F"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("D"));
Console.WriteLine("The value of myColor is 0x{0}.", 
                  myColor.ToString("X"));
// The example displays the following output to the console:
//       The value of myColor is Green.
//       The value of myColor is Green.
//       The value of myColor is 3.
//       The value of myColor is 0x00000003.
```

```vb
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("G"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("F"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("D"))
Console.WriteLine("The value of myColor is 0x{0}.", _
                  myColor.ToString("X"))
' The example displays the following output to the console:
'       The value of myColor is Green.
'       The value of myColor is Green.
'       The value of myColor is 3.
'       The value of myColor is 0x00000003. 
```

## <a name="see-also"></a>関連項目

[型の書式設定](formatting-types.md)




<!--HONumber=Nov16_HO3-->


