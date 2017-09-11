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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 076e10e095b50cc96187f2ec13ade2365d83dad3
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="using-the-stringbuilder-class"></a><span data-ttu-id="a5666-104">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="a5666-104">Using the StringBuilder class</span></span>

<span data-ttu-id="a5666-105">[String](xref:System.String) オブジェクトは、変更できません。</span><span class="sxs-lookup"><span data-stu-id="a5666-105">The [String](xref:System.String) object is immutable.</span></span> <span data-ttu-id="a5666-106">[System.String](xref:System.String) クラスのメソッドのいずれかを使用するたびに、新しい文字列オブジェクトをメモリ内に作成します。その際、その新しいオブジェクトに対して領域を新たに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5666-106">Every time you use one of the methods in the [System.String](xref:System.String) class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="a5666-107">文字列に対して何度も変更を実行する必要がある場合、新しい [String](xref:System.String) オブジェクトの作成に関連したオーバーヘッドが高コストになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5666-107">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new [String](xref:System.String) object can be costly.</span></span> <span data-ttu-id="a5666-108">新しいオブジェクトを作成せずに文字列を変更したい場合は、[System.Text.StringBuilder](xref:System.Text.StringBuilder) クラスを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-108">The [System.Text.StringBuilder](xref:System.Text.StringBuilder) class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="a5666-109">たとえば、ループで多数の文字列を連結する場合に、[StringBuilder](xref:System.Text.StringBuilder) クラスを使用してパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-109">For example, using the [StringBuilder](xref:System.Text.StringBuilder) class can boost performance when concatenating many strings together in a loop.</span></span>

## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="a5666-110">System.Text 名前空間のインポート</span><span class="sxs-lookup"><span data-stu-id="a5666-110">Importing the System.Text Namespace</span></span>

<span data-ttu-id="a5666-111">[StringBuilder](xref:System.Text.StringBuilder) は [System.Text](xref:System.Text) 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="a5666-111">The [StringBuilder](xref:System.Text.StringBuilder) class is found in the [System.Text](xref:System.Text) namespace.</span></span> <span data-ttu-id="a5666-112">完全修飾型名をコードに指定しなくてもすむように、[System.Text](xref:System.Text) 名前空間をインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-112">To avoid having to provide a fully qualified type name in your code, you can import the [System.Text](xref:System.Text) namespace:</span></span> 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="a5666-113">StringBuilder オブジェクトのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="a5666-113">Instantiating a StringBuilder Object</span></span>

<span data-ttu-id="a5666-114">以下の例に示すように、オーバーロードされたコンストラクター メソッドの&1; つで変数を初期化することにより、[StringBuilder](xref:System.Text.StringBuilder) クラスの新しいインスタンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-114">You can create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="a5666-115">容量と長さの設定</span><span class="sxs-lookup"><span data-stu-id="a5666-115">Setting the Capacity and Length</span></span>

<span data-ttu-id="a5666-116">[StringBuilder](xref:System.Text.StringBuilder) は、カプセル化する文字列内の文字数を拡張できるようにする動的オブジェクトですが、保持可能な最大文字数の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-116">Although the [StringBuilder](xref:System.Text.StringBuilder) is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="a5666-117">この値を、オブジェクトの容量と呼びます。これを現行の [StringBuilder](xref:System.Text.StringBuilder) が保持する文字列の長さと混同すべきではありません。</span><span class="sxs-lookup"><span data-stu-id="a5666-117">This value is called the capacity of the object and should not be confused with the length of the string that the current [StringBuilder](xref:System.Text.StringBuilder) holds.</span></span> <span data-ttu-id="a5666-118">たとえば、"Hello" という長さ 5 の文字列を持つ [StringBuilder](xref:System.Text.StringBuilder) クラスの新しいインスタンスを作成するときに、オブジェクトの最大容量として 25 を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-118">For example, you might create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="a5666-119">[StringBuilder](xref:System.Text.StringBuilder) を変更する際、容量に達するまでは、自動再割り当ては発生しません。</span><span class="sxs-lookup"><span data-stu-id="a5666-119">When you modify the [StringBuilder](xref:System.Text.StringBuilder), it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="a5666-120">容量に達すると、新しい領域が自動的に割り当てられ、容量が&2; 倍になります。</span><span class="sxs-lookup"><span data-stu-id="a5666-120">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="a5666-121">オーバーロードされたコンストラクターのいずれかを使用して、[StringBuilder](xref:System.Text.StringBuilder) クラスの容量を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-121">You can specify the capacity of the [StringBuilder](xref:System.Text.StringBuilder) class using one of the overloaded constructors.</span></span> <span data-ttu-id="a5666-122">次の例は、`MyStringBuilder` オブジェクトを最大 25 の領域に拡張できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-122">The following example specifies that the `MyStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

<span data-ttu-id="a5666-123">また、[Capacity](xref:System.Text.StringBuilder.Capacity) の読み取り/書き込みプロパティを使用して、オブジェクトの最大長を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-123">Additionally, you can use the read/write [Capacity](xref:System.Text.StringBuilder.Capacity) property to set the maximum length of your object.</span></span> <span data-ttu-id="a5666-124">次の例では、[Capacity](xref:System.Text.StringBuilder.Capacity) プロパティを使用して、オブジェクトの最大長を定義しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-124">The following example uses the [Capacity](xref:System.Text.StringBuilder.Capacity) property to define the maximum object length.</span></span>

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

<span data-ttu-id="a5666-125">[EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) メソッドを使用して、現行 [StringBuilder](xref:System.Text.StringBuilder) の容量を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-125">The [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) method can be used to check the capacity of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="a5666-126">容量が渡された値よりも大きい場合、変更は行われません。しかし、容量が渡された値より小さい場合は、渡された値と一致するよう現行の容量が変更されます。</span><span class="sxs-lookup"><span data-stu-id="a5666-126">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>

<span data-ttu-id="a5666-127">[Length](xref:System.Text.StringBuilder.Length) プロパティを表示または設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5666-127">The [Length](xref:System.Text.StringBuilder.Length) property can also be viewed or set.</span></span> <span data-ttu-id="a5666-128">[Length](xref:System.Text.StringBuilder.Length) プロパティを、[Capacity](xref:System.Text.StringBuilder.Capacity) プロパティより大きな値に設定する場合、[Capacity](xref:System.Text.StringBuilder.Capacity) プロパティは [Length](xref:System.Text.StringBuilder.Length) プロパティと同じ値に自動的に変更されます。</span><span class="sxs-lookup"><span data-stu-id="a5666-128">If you set the [Length](xref:System.Text.StringBuilder.Length) property to a value that is greater than the [Capacity](xref:System.Text.StringBuilder.Capacity) property, the [Capacity](xref:System.Text.StringBuilder.Capacity) property is automatically changed to the same value as the [Length](xref:System.Text.StringBuilder.Length) property.</span></span> <span data-ttu-id="a5666-129">[Length](xref:System.Text.StringBuilder.Length) プロパティを、現行の [StringBuilder](xref:System.Text.StringBuilder) 内の文字列の長さより小さい値に設定すると、文字列は短縮されます。</span><span class="sxs-lookup"><span data-stu-id="a5666-129">Setting the [Length](xref:System.Text.StringBuilder.Length) property to a value that is less than the length of the string within the current [StringBuilder](xref:System.Text.StringBuilder) shortens the string.</span></span>

## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="a5666-130">StringBuilder 文字列の変更</span><span class="sxs-lookup"><span data-stu-id="a5666-130">Modifying the StringBuilder String</span></span>

<span data-ttu-id="a5666-131">[StringBuilder](xref:System.Text.StringBuilder) の内容の変更に使用できるメソッドを次の表に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a5666-131">The following table lists the methods you can use to modify the contents of a [StringBuilder](xref:System.Text.StringBuilder).</span></span>

<span data-ttu-id="a5666-132">メソッド名</span><span class="sxs-lookup"><span data-stu-id="a5666-132">Method name</span></span> | <span data-ttu-id="a5666-133">使用</span><span class="sxs-lookup"><span data-stu-id="a5666-133">Use</span></span>
----------- | ---
<span data-ttu-id="a5666-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span><span class="sxs-lookup"><span data-stu-id="a5666-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span></span> | <span data-ttu-id="a5666-135">現行の [StringBuilder](xref:System.Text.StringBuilder) の末尾に情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="a5666-135">Appends information to the end of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="a5666-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="a5666-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | <span data-ttu-id="a5666-137">文字列に渡される書式指定子を、書式設定されたテキスト文字列で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a5666-137">Replaces a format specifier passed in a string with formatted text.</span></span>
<span data-ttu-id="a5666-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span><span class="sxs-lookup"><span data-stu-id="a5666-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span></span> | <span data-ttu-id="a5666-139">現行の [StringBuilder](xref:System.Text.StringBuilder) の指定されたインデックスに、文字列またはオブジェクトを挿入します。</span><span class="sxs-lookup"><span data-stu-id="a5666-139">Inserts a string or object into the specified index of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="a5666-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="a5666-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span></span> | <span data-ttu-id="a5666-141">現行の [StringBuilder](xref:System.Text.StringBuilder) から、指定された文字数を削除します。</span><span class="sxs-lookup"><span data-stu-id="a5666-141">Removes a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="a5666-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span><span class="sxs-lookup"><span data-stu-id="a5666-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span></span> | <span data-ttu-id="a5666-143">指定されたインデックスで、指定された文字を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a5666-143">Replaces a specified character at a specified index.</span></span>

### <a name="append"></a><span data-ttu-id="a5666-144">追加</span><span class="sxs-lookup"><span data-stu-id="a5666-144">Append</span></span>

<span data-ttu-id="a5666-145">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) メソッドを使用して、現行 [StringBuilder](xref:System.Text.StringBuilder) によって表される文字列の末尾にオブジェクトのテキストまたは文字列形式を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-145">The [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) method can be used to add text or a string representation of an object to the end of a string represented by the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="a5666-146">次の例では、[StringBuilder](xref:System.Text.StringBuilder) を "Hello World" に初期設定し、テキストをオブジェクトの末尾に追加しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-146">The following example initializes a [StringBuilder](xref:System.Text.StringBuilder) to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="a5666-147">領域は、必要に応じて自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a5666-147">Space is allocated automatically as needed.</span></span>

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

### <a name="appendformat"></a><span data-ttu-id="a5666-148">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="a5666-148">AppendFormat</span></span>

<span data-ttu-id="a5666-149">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) メソッドは、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトの末尾にテキストを追加します。</span><span class="sxs-lookup"><span data-stu-id="a5666-149">The [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) method adds text to the end of the [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="a5666-150">これは、書式設定される&1; つ以上のオブジェクトの [IFormattable](xref:System.IFormattable) 実装を呼び出すことにより、複合書式機能をサポートしています (詳細については、[Composite Formatting](composite-format.md) を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a5666-150">It supports the composite formatting feature (for more information, see [Composite Formatting](composite-format.md)) by calling the [IFormattable](xref:System.IFormattable) implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="a5666-151">そのため、数値、日時、および列挙の値に対して標準書式文字列を受け取り、数値と日時の値、およびカスタム型に定義されている書式文字列に対してカスタム書式文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a5666-151">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="a5666-152">(書式設定については、「[型の書式設定](formatting-types.md)」を参照してください。)このメソッドを使用して、変数の書式をカスタマイズし、その値を [StringBuilder](xref:System.Text.StringBuilder) に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-152">(For information about formatting, see [Formatting Types](formatting-types.md).) You can use this method to customize the format of variables and append those values to a [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="a5666-153">次の例では、AppendFormat メソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトの末尾に、通貨値として書式設定されている整数値を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-153">The following example uses the AppendFormat method to place an integer value formatted as a currency value at the end of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="insert"></a><span data-ttu-id="a5666-154">挿入</span><span class="sxs-lookup"><span data-stu-id="a5666-154">Insert</span></span>

<span data-ttu-id="a5666-155">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) メソッドは、現行の [StringBuilder](xref:System.Text.StringBuilder) オブジェクトの指定された位置に、文字列またはオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="a5666-155">The [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) method adds a string or object to a specified position in the current [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="a5666-156">次の例では、このメソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトの&6; 番目の位置に単語を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-156">The following example uses this method to insert a word into the sixth position of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="remove"></a><span data-ttu-id="a5666-157">削除</span><span class="sxs-lookup"><span data-stu-id="a5666-157">Remove</span></span>

<span data-ttu-id="a5666-158">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) メソッドを使用して、現行の [StringBuilder](xref:System.Text.StringBuilder) オブジェクトから指定された文字数を削除します (0 から始まる指定されたインデックスで開始します)。</span><span class="sxs-lookup"><span data-stu-id="a5666-158">You can use the [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to remove a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder) object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="a5666-159">次の例では、[Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) メソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクトを短縮しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-159">The following example uses the [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to shorten a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="replace"></a><span data-ttu-id="a5666-160">置換</span><span class="sxs-lookup"><span data-stu-id="a5666-160">Replace</span></span>

<span data-ttu-id="a5666-161">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 指定されたインデックスで、指定された文字を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a5666-161">The [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="a5666-162">メソッドを使用して、[StringBuilder](xref:System.Text.StringBuilder) オブジェクト内の文字を、指定された別の文字で置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="a5666-162">method can be used to replace characters within the [StringBuilder](xref:System.Text.StringBuilder) object with another specified character.</span></span> <span data-ttu-id="a5666-163">次の例では、[Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 指定されたインデックスで、指定された文字を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a5666-163">The following example uses the [Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="a5666-164">メソッドを使用して、感嘆符 (!) のすべてのインスタンスを求めて [StringBuilder](xref:System.Text.StringBuilder) オブジェクトを検索し、疑問符 (?) で置き換えています。</span><span class="sxs-lookup"><span data-stu-id="a5666-164">method to search a [StringBuilder](xref:System.Text.StringBuilder) object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>
 
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

## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="a5666-165">文字列への StringBuilder オブジェクトの変換</span><span class="sxs-lookup"><span data-stu-id="a5666-165">Converting a StringBuilder Object to a String</span></span>

<span data-ttu-id="a5666-166">[StringBuilder](xref:System.Text.StringBuilder) オブジェクトで表される文字列を [String](xref:System.String) パラメーターを持つメソッドに渡すかそれをユーザー インターフェイスに表示するには、事前に [StringBuilder](xref:System.Text.StringBuilder) オブジェクトを [String](xref:System.String) オブジェクトに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5666-166">You must convert the [StringBuilder](xref:System.Text.StringBuilder) object to a [String](xref:System.String) object before you can pass the string represented by the [StringBuilder](xref:System.Text.StringBuilder) object to a method that has a [String](xref:System.String) parameter or display it in the user interface.</span></span> <span data-ttu-id="a5666-167">この変換は、[StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) メソッドを呼び出すことによって行います。</span><span class="sxs-lookup"><span data-stu-id="a5666-167">You do this conversion by calling the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method.</span></span> <span data-ttu-id="a5666-168">次の例では、いくつかの [StringBuilder](xref:System.Text.StringBuilder) メソッドを呼び出し、その後、[StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) メソッドを呼び出して文字列を表示しています。</span><span class="sxs-lookup"><span data-stu-id="a5666-168">The following example calls a number of [StringBuilder](xref:System.Text.StringBuilder) methods and then calls the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method to display the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a5666-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5666-169">See Also</span></span>

[<span data-ttu-id="a5666-170">System.Text.StringBuilder</span><span class="sxs-lookup"><span data-stu-id="a5666-170">System.Text.StringBuilder</span></span>](xref:System.Text.StringBuilder)

[<span data-ttu-id="a5666-171">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="a5666-171">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="a5666-172">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="a5666-172">Formatting types</span></span>](formatting-types.md)

