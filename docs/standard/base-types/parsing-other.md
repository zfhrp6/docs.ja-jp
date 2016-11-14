---
title: ".NET でのその他の文字列の解析"
description: ".NET でのその他の文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 67670b10-3df4-45ea-8908-5ba3f056887c
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 3f26670dc9f4c6b6608599793352445d5665cf64

---

# <a name="parsing-other-strings-in-net"></a>.NET でのその他の文字列の解析

数値および [DateTime](xref:System.DateTime) 文字列だけでなく、[Char](xref:System.Char)、[Boolean](xref:System.Boolean)、および [Enum](xref:System.Enum) 型を表す文字列をデータ型に解析することもできます。

## <a name="char"></a>Char

[Char](xref:System.Char) データ型に関連付けられている静的解析メソッドは、1 つの文字を含む文字列をUnicode 値に変換するのに便利です。 次のコードの例では、文字列を Unicode 文字に解析します。

```csharp
string MyString1 = "A";
char MyChar = Char.Parse(MyString1);
// MyChar now contains a Unicode "A" character.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="boolean"></a>ブール型

[Boolean](xref:System.Boolean) データ型には、[Parse](xref:System.Boolean.Parse(System.String)) メソッドが含まれ、`Boolean` 値を示す文字列を実際の `Boolean` 型に変換するために使用できます。 このメソッドは大文字と小文字を区別しません。また、"True" または "False" を含む文字列を正常に解析することができます。 `Boolean` 型に関連付けられる `Parse` メソッドは、空白で囲まれた文字列を解析することもできます。 その他の文字列が渡された場合、[FormatException](xref:System.FormatException) がスローされます。

次のコードの例では、`Parse` メソッドを使用して、文字列を `Boolean` 値に変換します。

```csharp
string MyString2 = "True";
bool MyBool = bool.Parse(MyString2);
// MyBool now contains a True Boolean value.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="enumeration"></a>列挙

静的 [Parse](xref:System.Enum.Parse(System.Type,System.String)) メソッドを使用して、列挙型を文字列の値に初期化できます。 このメソッドでは、解析している列挙型、解析する文字列、および解析が大文字小文字を区別するかどうかを示す省略可能な `Boolean` フラグを受け入れます。 解析している文字列は、コンマで区切られた複数の値を含めることができます。これは、1 つ以上の空の領域 (空白とも呼ばれます) が前後にある場合があります。 文字列に複数の値がある場合、返されたオブジェクトの値は、ビット演算 OR 演算と組み合わされたすべての指定された値の値です。

次の例では、`Parse` メソッドを使用して、文字列形式を列挙値に変換します。 [DayOfWeek](xref:System.DayOfWeek) 列挙体は、文字列から Thursday に初期化されます。

```csharp
string MyString3 = "Thursday";
DayOfWeek MyDays = (DayOfWeek)Enum.Parse(typeof(DayOfWeek), MyString3);
Console.WriteLine(MyDays);
// The result is Thursday.
```

```vb
Dim MyString3 As String = "Thursday"
Dim MyDays As DayOfWeek = CType([Enum].Parse(GetType(DayOfWeek), MyString3), DayOfWeek)
Console.WriteLine("{0:G}", MyDays)
' The result is Thursday.
```

## <a name="see-also"></a>関連項目

[.NET での文字列の解析](parsing-strings.md)

[.NET での型の書式設定](formatting-types.md)

[.NET での型変換](type-conversion.md)




<!--HONumber=Nov16_HO1-->


