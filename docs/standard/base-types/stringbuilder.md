---
title: "StringBuilder クラスの使用"
description: "StringBuilder クラスの使用"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: f4f5d1c7-d84d-4867-810f-2708cd6de0da
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 076e10e095b50cc96187f2ec13ade2365d83dad3
ms.lasthandoff: 03/02/2017

---

# <a name="using-the-stringbuilder-class"></a>StringBuilder クラスの使用

[String](xref:System.String) オブジェクトは、変更できません。 [System.String](xref:System.String) クラスのメソッドのいずれかを使用するたびに、新しい文字列オブジェクトをメモリ内に作成します。その際、その新しいオブジェクトに対して領域を新たに割り当てる必要があります。 文字列に対して何度も変更を実行する必要がある場合、新しい [String](xref:System.String) オブジェクトの作成に関連したオーバーヘッドが高コストになる可能性があります。 新しいオブジェクトを作成せずに文字列を変更したい場合は、[System.Text.StringBuilder](xref:System.Text.StringBuilder) クラスを使用することができます。 たとえば、ループで多数の文字列を連結する場合に、[StringBuilder](xref:System.Text.StringBuilder) クラスを使用してパフォーマンスを向上させることができます。

## <a name="importing-the-systemtext-namespace"></a>System.Text 名前空間のインポート

[StringBuilder](xref:System.Text.StringBuilder) は [System.Text](xref:System.Text) 名前空間にあります。 完全修飾型名をコードに指定しなくてもすむように、[System.Text](xref:System.Text) 名前空間をインポートすることができます。 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a>StringBuilder オブジェクトのインスタンス化

以下の例に示すように、オーバーロードされたコンストラクター メソッドの&1; つで変数を初期化することにより、[StringBuilder](xref:System.Text.StringBuilder) クラスの新しいインスタンスを作成することができます。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a>容量と長さの設定

[StringBuilder](xref:System.Text.StringBuilder) は、カプセル化する文字列内の文字数を拡張できるようにする動的オブジェクトですが、保持可能な最大文字数の値を指定することができます。 この値を、オブジェクトの容量と呼びます。これを現行の [StringBuilder](xref:System.Text.StringBuilder) が保持する文字列の長さと混同すべきではありません。 たとえば、"Hello" という長さ 5 の文字列を持つ [StringBuilder](xref:System.Text.StringBuilder) クラスの新しいインスタンスを作成するときに、オブジェクトの最大容量として 25 を指定することができます。 [StringBuilder](xref:System.Text.StringBuilder) を変更する際、容量に達するまでは、自動再割り当ては発生しません。 容量に達すると、新しい領域が自動的に割り当てられ、容量が&2; 倍になります。 オーバーロードされたコンストラクターのいずれかを使用して、[StringBuilder](xref:System.Text.StringBuilder) クラスの容量を指定することができます。 次の例は、`MyStringBuilder` オブジェクトを最大 25 の領域に拡張できることを示しています。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

また、[Capacity](xref:System.Text.StringBuilder.Capacity) の読み取り/書き込みプロパティを使用して、オブジェクトの最大長を設定することができます。 次の例では、[Capacity](xref:System.Text.StringBuilder.Capacity) プロパティを使用して、オブジェクトの最大長を定義しています。

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

[EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) メソッドを使用して、現行 [StringBuilder](xref:System.Text.StringBuilder) の容量を確認することができます。 容量が渡された値よりも大きい場合、変更は行われません。しかし、容量が渡された値より小さい場合は、渡された値と一致するよう現行の容量が変更されます。

[Length](xref:System.Text.StringBuilder.Length) プロパティを表示または設定することもできます。 [Length](xref:System.Text.StringBuilder.Length) プロパティを、[Capacity](xref:System.Text.StringBuilder.Capacity) プロパティより大きな値に設定する場合、[Capacity](xref:System.Text.StringBuilder.Capacity) プロパティは [Length](xref:System.Text.StringBuilder.Length) プロパティと同じ値に自動的に変更されます。 [Length](xref:System.Text.StringBuilder.Length) プロパティを、現行の [StringBuilder](xref:System.Text.StringBuilder) 内の文字列の長さより小さい値に設定すると、文字列は短縮されます。

## <a name="modifying-the-stringbuilder-string"></a>StringBuilder 文字列の変更

[StringBuilder](xref:System.Text.StringBuilder) の内容の変更に使用できるメソッドを次の表に一覧表示します。

メソッド名 | 使用
----------- | ---
[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) | 現行の [StringBuilder](xref:System.Text.StringBuilder) の末尾に情報を追加します。
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | 文字列に渡される書式指定子を、書式設定されたテキスト文字列で置き換えます。
[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) | 現行の [StringBuilder](xref:System.Text.StringBuilder) の指定されたインデックスに、文字列またはオブジェクトを挿入します。
[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) | 現行の [StringBuilder](xref:System.Text.StringBuilder) から、指定された文字数を削除します。
[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 指定されたインデックスで、指定された文字を置き換えます。

### <a name="append"></a>追加

[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) メソッドを使用して、現行 [StringBuilder](xref:System.Text.StringBuilder) によって表される文字列の末尾にオブジェクトのテキストまたは文字列形式を追加することができます。 次の例では、[StringBuilder](xref:System.Text.StringBuilder) を "Hello World" に初期設定し、テキストをオブジェクトの末尾に追加しています。 領域は、必要に応じて自動的に割り当てられます。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Append(" What a beautiful day.");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World! What a beautiful day.
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Append(" What a beautiful day.")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World! What a beautiful day.
```

### <a name="appendformat"></a>AppendFormat

[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) メソッドは、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトの末尾にテキストを追加します。 これは、書式設定される&1; つ以上のオブジェクトの [IFormattable](xref:System.IFormattable) 実装を呼び出すことにより、複合書式機能をサポートしています (詳細については、[Composite Formatting](composite-format.md) を参照してください)。 そのため、数値、日時、および列挙の値に対して標準書式文字列を受け取り、数値と日時の値、およびカスタム型に定義されている書式文字列に対してカスタム書式文字列を受け取ります。 (書式設定については、「[型の書式設定](formatting-types.md)」を参照してください。)このメソッドを使用して、変数の書式をカスタマイズし、その値を [StringBuilder](xref:System.Text.StringBuilder) に追加することができます。 次の例では、AppendFormat メソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトの末尾に、通貨値として書式設定されている整数値を挿入しています。

```csharp
int MyInt = 25; 
StringBuilder MyStringBuilder = new StringBuilder("Your total is ");
MyStringBuilder.AppendFormat("{0:C} ", MyInt);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Your total is $25.00
```

```vb
Dim MyInt As Integer = 25
Dim MyStringBuilder As New StringBuilder("Your total is ")
MyStringBuilder.AppendFormat("{0:C} ", MyInt)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'     Your total is $25.00 
```

### <a name="insert"></a>挿入

[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) メソッドは、現行の [StringBuilder](xref:System.Text.StringBuilder) オブジェクトの指定された位置に、文字列またはオブジェクトを追加します。 次の例では、このメソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトの&6; 番目の位置に単語を挿入しています。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Insert(6,"Beautiful ");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello Beautiful World!
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Insert(6, "Beautiful ")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'      Hello Beautiful World!
```

### <a name="remove"></a>削除

[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) メソッドを使用して、現行の [StringBuilder](xref:System.Text.StringBuilder) オブジェクトから指定された文字数を削除します (0 から始まる指定されたインデックスで開始します)。 次の例では、[Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) メソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトを短縮しています。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Remove(5,7);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Remove(5, 7)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello
```

### <a name="replace"></a>置換

[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 指定されたインデックスで、指定された文字を置き換えます。
メソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクト内の文字を、指定された別の文字で置き換えることができます。 次の例では、[Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 指定されたインデックスで、指定された文字を置き換えます。
メソッドを使用して、感嘆符 (!) のすべてのインスタンスを求めて [StringBuilder](xref:System.Text.StringBuilder) オブジェクトを検索し、疑問符 (?) で置き換えています。
 
 ```csharp
 StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Replace('!', '?');
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World?
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Replace("!"c, "?"c)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World?
```

## <a name="converting-a-stringbuilder-object-to-a-string"></a>文字列への StringBuilder オブジェクトの変換

[StringBuilder](xref:System.Text.StringBuilder) オブジェクトで表される文字列を [String](xref:System.String) パラメーターを持つメソッドに渡すかそれをユーザー インターフェイスに表示するには、事前に [StringBuilder](xref:System.Text.StringBuilder) オブジェクトを [String](xref:System.String) オブジェクトに変換する必要があります。 この変換は、[StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) メソッドを呼び出すことによって行います。 次の例では、いくつかの [StringBuilder](xref:System.Text.StringBuilder) メソッドを呼び出し、その後、[StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) メソッドを呼び出して文字列を表示しています。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      StringBuilder sb = new StringBuilder();
      bool flag = true;
      string[] spellings = { "recieve", "receeve", "receive" };
      sb.AppendFormat("Which of the following spellings is {0}:", flag);
      sb.AppendLine();
      for (int ctr = 0; ctr <= spellings.GetUpperBound(0); ctr++) {
         sb.AppendFormat("   {0}. {1}", ctr, spellings[ctr]);
         sb.AppendLine();
      }
      sb.AppendLine();
      Console.WriteLine(sb.ToString());
   }
}
// The example displays the following output:
//       Which of the following spellings is True:
//          0. recieve
//          1. receeve
//          2. receive
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim sb As New StringBuilder()
      Dim flag As Boolean = True
      Dim spellings() As String = { "recieve", "receeve", "receive" }
      sb.AppendFormat("Which of the following spellings is {0}:", flag)
      sb.AppendLine()
      For ctr As Integer = 0 To spellings.GetUpperBound(0)
         sb.AppendFormat("   {0}. {1}", ctr, spellings(ctr))
         sb.AppendLine()
      Next
      sb.AppendLine()
      Console.WriteLine(sb.ToString())
   End Sub
End Module
' The example displays the following output:
'       Which of the following spellings is True:
'          0. recieve
'          1. receeve
'          2. receive
```

## <a name="see-also"></a>関連項目

[System.Text.StringBuilder](xref:System.Text.StringBuilder)

[基本的な文字列操作](basic-string-operations.md)

[型の書式設定](formatting-types.md)

