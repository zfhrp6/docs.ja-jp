---
title: "新しい文字列の作成"
description: "新しい文字列の作成"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 639397c7-e694-43e0-845b-1681c62bd9fd
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 43d6194afd948aeccbf051365e059794c74d2646

---

# <a name="creating-new-strings"></a>新しい文字列の作成

.NET は、単純な割り当てを使用した文字列の作成をサポートしています。また、多数の異なるパラメーターを使用した文字列の作成をサポートするために、クラス コンストラクターをオーバーロードします。 また、.NET は、複数の文字列、文字列の配列、またはオブジェクトを組み合わせて新しい文字列オブジェクトを作成する、[System.String](xref:System.String) クラスの複数のメソッドを提供します。 

## <a name="creating-strings-using-assignment"></a>割り当てを使用した文字列の作成

新しい [String](xref:System.String) オブジェクトを作成する最も簡単な方法としては、単に文字列リテラルを [String](xref:System.String) オブジェクトに割り当てます。 

## <a name="creating-strings-using-a-class-constructor"></a>クラス コンストラクターを使用した文字列の作成

[String](xref:System.String) クラス コンストラクターのオーバーロードを使用すると、文字配列から文字列を作成できます。 また、指定した回数だけ特定の文字を複製することで、新しい文字列を作成することもできます。 

## <a name="methods-that-return-strings"></a>文字列を返すメソッド

次の表は、新しい文字列オブジェクトを返すいくつかの便利なメソッドを示しています。

メソッド名 | 使用
----------- | ---
[String.Format](xref:System.String.Format(System.String,System.Object)) | 入力オブジェクトのセットから、書式設定された文字列をビルドします。
[String.Concat](xref:System.String.Concat(System.String,System.String)) | 2 つ以上の文字列から文字列をビルドします。
[String.Join](xref:System.String.Join(System.String,System.String[])) |文字列の配列を組み合わせることで、新しい文字列をビルドします。
[String.Insert](xref:System.String.Insert(System.Int32,System.String)) | 既存の文字列の指定のインデックスに文字列を挿入することで、新しい文字列をビルドします。
[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32)) | 文字配列内の指定の位置に、文字列内の指定の文字をコピーします。

### <a name="format"></a>形式

`String.Format` メソッドを使用すると、書式設定された文字列を作成し、複数のオブジェクトを表す文字列を連結できます。 このメソッドは、渡されたすべてのオブジェクトを文字列に自動的に変換します。 たとえば、アプリケーションでユーザーに対して [Int32](xref:System.Int32) 値と [DateTime](xref:System.DateTime) 値を表示する必要がある場合、`Format` メソッドを使用して、これらの値を表す文字列を簡単に作成できます。 このメソッドで使用される書式設定規則については、[複合書式指定](composite-format.md)に関するセクションを参照してください。

次の例では、`Format` メソッドを使用して、整数型の変数を使用する文字列を作成します。

```csharp
int numberOfFleas = 12;
string miscInfo = String.Format("Your dog has {0} fleas. " +
                                "It is time to get a flea collar. " + 
                                "The current universal date is: {1:u}.", 
                                numberOfFleas, DateTime.Now);
Console.WriteLine(miscInfo);
// The example displays the following output:
//       Your dog has 12 fleas. It is time to get a flea collar. 
//       The current universal date is: 2008-03-28 13:31:40Z.
```

```vb
Dim numberOfFleas As Integer = 12
Dim miscInfo As String = String.Format("Your dog has {0} fleas. " & _
                                       "It is time to get a flea collar. " & _ 
                                       "The current universal date is: {1:u}.", _ 
                                       numberOfFleas, Date.Now)
Console.WriteLine(miscInfo)
' The example displays the following output:
'       Your dog has 12 fleas. It is time to get a flea collar. 
'       The current universal date is: 2008-03-28 13:31:40Z.
```

この例では、[DateTime.Now](xref:System.DateTime.Now) は、現在のスレッドに関連付けられているカルチャで指定された方法で現在の日時を表示します。

### <a name="concat"></a>Concat

`String.Concat` メソッドを使用すると、2 つ以上の既存のオブジェクトから新しい文字列オブジェクトを簡単に作成できます。 言語に依存せずに文字列を連結する方法を提供します。 このメソッドは、`System.Object` から派生したすべてのクラスを受け入れます。 次の例では、2 つの既存の文字列オブジェクトおよび区切り文字から文字列を作成します。

```csharp
string helloString1 = "Hello";
string helloString2 = "World!";
Console.WriteLine(String.Concat(helloString1, ' ', helloString2));
// The example displays the following output:
//      Hello World!
```

```vb
Dim helloString1 As String = "Hello"
Dim helloString2 As String = "World!"
Console.WriteLine(String.Concat(helloString1, " "c, helloString2))
' The example displays the following output:
'      Hello World!
```

### <a name="join"></a>Join

`String.Join` メソッドは、文字列の配列および区切り文字列から新しい文字列を作成します。 このメソッドは、複数の文字列を連結して、たとえばコンマで区切られたリストを作成する場合に便利です。

次の例では、スペースを使用して文字列の配列をバインドします。

```csharp
string[] words = {"Hello", "and", "welcome", "to", "my" , "world!"};
Console.WriteLine(String.Join(" ", words));
// The example displays the following output:
//      Hello and welcome to my world!
```

```vb
Dim words() As String = {"Hello", "and", "welcome", "to", "my" , "world!"}
Console.WriteLine(String.Join(" ", words))
' The example displays the following output:
'      Hello and welcome to my world!
```

### <a name="insert"></a>挿入

`String.Insert` メソッドは、別の文字列内の指定の位置に文字列を挿入することで、新しい文字列を作成します。 このメソッドは、0 から始まるインデックスを使用します。 次の例では、`MyString` の 5 番目のインデックス位置に文字列を挿入し、この値を持つ新しい文字列を作成します。

```csharp
string sentence = "Once a time.";   
 Console.WriteLine(sentence.Insert(4, " upon"));
 // The example displays the following output:
 //      Once upon a time.
```

```vb
Dim sentence As String = "Once a time."   
 Console.WriteLine(sentence.Insert(4, " upon"))
 ' The example displays the 
```

### <a name="copyto"></a>CopyTo

`String.CopyTo` メソッドは、文字配列に文字列の部分をコピーします。 文字列の開始インデックスと、コピーする文字数の両方を指定できます。 このメソッドは、ソース インデックス、文字配列、コピー先のインデックス、およびコピーする文字数を受け取ります。 すべてのインデックスは 0 から始まります。

次の例では、`CopyTo` メソッドを使用して、文字列オブジェクトから文字配列の最初のインデックス位置に、単語 "Hello" の文字をコピーします。

```csharp
string greeting = "Hello World!";
char[] charArray = {'W','h','e','r','e'};
Console.WriteLine("The original character array: {0}", new string(charArray));
greeting.CopyTo(0, charArray,0 ,5);
Console.WriteLine("The new character array: {0}", new string(charArray));
// The example displays the following output:
//       The original character array: Where
//       The new character array: Hello
```

```vb
Dim greeting As String = "Hello World!"
Dim charArray() As Char = {"W"c, "h"c, "e"c, "r"c, "e"c}
Console.WriteLine("The original character array: {0}", New String(charArray))
greeting.CopyTo(0, charArray,0 ,5)
Console.WriteLine("The new character array: {0}", New String(charArray))
' The example displays the following output:
'       The original character array: Where
'       The new character array: Hello
```

## <a name="see-also"></a>関連項目

[基本的な文字列操作](basic-string-operations.md)

[複合書式指定](composite-format.md)




<!--HONumber=Nov16_HO1-->


