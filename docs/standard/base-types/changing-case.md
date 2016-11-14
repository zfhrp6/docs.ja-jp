---
title: "大文字と小文字の変更"
description: "大文字と小文字の変更"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: a6f6f21daae79f752cfac0a70558778ae98d1a5d

---

# <a name="changing-case"></a>大文字と小文字の変更

ユーザーからの入力を受け付けるアプリケーションを記述する場合、ユーザーがデータ入力に使用するケースを正確に予測することはできません。 多くの場合、特にユーザー インターフェイスにそれを表示する場合には、文字列に一貫性のあるケースを使用することが求められます。 次の表は、2 つのケース変更方式を示しています。

メソッド名 | 使用
----------- | ---
[String.ToUpper](xref:System.String.ToUpper) | 文字列内のすべての文字を大文字に変換します。
[String.ToLower](xref:System.String.ToLower) | 文字列内のすべての文字を小文字に変換します。

> [!WARNING]  
> `String.ToUpper` と `String.ToLower` の方式を使用して、文字列を比較したり等しいかどうかをテストしたりする目的で、それらの文字列を変換するべきではないことに注意してください。 

## <a name="comparing-strings-of-mixed-case"></a>大小混合文字の文字列を比較する

大小混合文字の文字列を比較してそれらが等しいかどうかを判別するには、*comparisonType* パラメーターのある [String](xref:System) `Equals` メソッドのいずれかのオーバーロードを呼び出して、*comparisonType* 引数に [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) の値を指定します。 

詳細については、「[文字列を使用するためのベスト プラクティス](best-practices.md)」を参照してください。 

## <a name="toupper"></a>ToUpper

[String.ToUpper](xref:System.String.ToUpper) メソッドは文字列内のすべての文字を大文字に変換します。 次の例では、文字列 "Hello World!" を 大小混合文字から大文字に変換します。

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToUpper());
// This example displays the following output:
//       HELLO WORLD!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToUpper())
' This example displays the following output:
'       HELLO WORLD!
```

## <a name="tolower"></a>ToLower

[String.ToLower](xref:System.String.ToLower) メソッドは、前のメソッドと似ていますが、代わりに文字列内のすべての文字を小文字に変換します。 次の例では、文字列 "Hello World!" を 小文字に変換します。

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToLower());
// This example displays the following output:
//       hello world!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToLower())
' This example displays the following output:
'       hello world!
```

## <a name="see-also"></a>関連項目

[基本的な文字列操作](basic-string-operations.md)



<!--HONumber=Nov16_HO1-->


