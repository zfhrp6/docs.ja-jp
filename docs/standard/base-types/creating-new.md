---
title: "新しい文字列の作成"
description: "新しい文字列の作成"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 639397c7-e694-43e0-845b-1681c62bd9fd
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="creating-new-strings"></a><span data-ttu-id="55053-104">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="55053-104">Creating new strings</span></span>

<span data-ttu-id="55053-105">.NET は、単純な割り当てを使用した文字列の作成をサポートしています。また、多数の異なるパラメーターを使用した文字列の作成をサポートするために、クラス コンストラクターをオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="55053-105">.NET  allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="55053-106">また、.NET は、複数の文字列、文字列の配列、またはオブジェクトを組み合わせて新しい文字列オブジェクトを作成する、[System.String](xref:System.String) クラスの複数のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="55053-106">.NET also provides several methods in the [System.String](xref:System.String) class that create new string objects by combining several strings, arrays of strings, or objects.</span></span> 

## <a name="creating-strings-using-assignment"></a><span data-ttu-id="55053-107">割り当てを使用した文字列の作成</span><span class="sxs-lookup"><span data-stu-id="55053-107">Creating Strings Using Assignment</span></span>

<span data-ttu-id="55053-108">新しい [String](xref:System.String) オブジェクトを作成する最も簡単な方法としては、単に文字列リテラルを [String](xref:System.String) オブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="55053-108">The easiest way to create a new [String](xref:System.String) object is simply to assign a string literal to a [String](xref:System.String) object.</span></span> 

## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="55053-109">クラス コンストラクターを使用した文字列の作成</span><span class="sxs-lookup"><span data-stu-id="55053-109">Creating Strings Using a Class Constructor</span></span>

<span data-ttu-id="55053-110">[String](xref:System.String) クラス コンストラクターのオーバーロードを使用すると、文字配列から文字列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="55053-110">You can use overloads of the [String](xref:System.String) class constructor to create strings from character arrays.</span></span> <span data-ttu-id="55053-111">また、指定した回数だけ特定の文字を複製することで、新しい文字列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="55053-111">You can also create a new string by duplicating a particular character a specified number of times.</span></span> 

## <a name="methods-that-return-strings"></a><span data-ttu-id="55053-112">文字列を返すメソッド</span><span class="sxs-lookup"><span data-stu-id="55053-112">Methods that Return Strings</span></span>

<span data-ttu-id="55053-113">次の表は、新しい文字列オブジェクトを返すいくつかの便利なメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="55053-113">The following table lists several useful methods that return new string objects.</span></span>

<span data-ttu-id="55053-114">メソッド名</span><span class="sxs-lookup"><span data-stu-id="55053-114">Method name</span></span> | <span data-ttu-id="55053-115">使用</span><span class="sxs-lookup"><span data-stu-id="55053-115">Use</span></span>
----------- | ---
<span data-ttu-id="55053-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="55053-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span></span> | <span data-ttu-id="55053-117">入力オブジェクトのセットから、書式設定された文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="55053-117">Builds a formatted string from a set of input objects.</span></span>
<span data-ttu-id="55053-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span><span class="sxs-lookup"><span data-stu-id="55053-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span></span> | <span data-ttu-id="55053-119">2 つ以上の文字列から文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="55053-119">Builds strings from two or more strings.</span></span>
<span data-ttu-id="55053-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span><span class="sxs-lookup"><span data-stu-id="55053-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span></span> |<span data-ttu-id="55053-121">文字列の配列を組み合わせることで、新しい文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="55053-121">Builds a new string by combining an array of strings.</span></span>
<span data-ttu-id="55053-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span><span class="sxs-lookup"><span data-stu-id="55053-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span></span> | <span data-ttu-id="55053-123">既存の文字列の指定のインデックスに文字列を挿入することで、新しい文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="55053-123">Builds a new string by inserting a string into the specified index of an existing string.</span></span>
<span data-ttu-id="55053-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="55053-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span></span> | <span data-ttu-id="55053-125">文字配列内の指定の位置に、文字列内の指定の文字をコピーします。</span><span class="sxs-lookup"><span data-stu-id="55053-125">Copies specified characters in a string into a specified position in an array of characters.</span></span>

### <a name="format"></a><span data-ttu-id="55053-126">形式</span><span class="sxs-lookup"><span data-stu-id="55053-126">Format</span></span>

<span data-ttu-id="55053-127">`String.Format` メソッドを使用すると、書式設定された文字列を作成し、複数のオブジェクトを表す文字列を連結できます。</span><span class="sxs-lookup"><span data-stu-id="55053-127">You can use the `String.Format` method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="55053-128">このメソッドは、渡されたすべてのオブジェクトを文字列に自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="55053-128">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="55053-129">たとえば、アプリケーションでユーザーに対して [Int32](xref:System.Int32) 値と [DateTime](xref:System.DateTime) 値を表示する必要がある場合、`Format` メソッドを使用して、これらの値を表す文字列を簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="55053-129">For example, if your application must display an [Int32](xref:System.Int32) value and a [DateTime](xref:System.DateTime) value to the user, you can easily construct a string to represent these values using the `Format` method.</span></span> <span data-ttu-id="55053-130">このメソッドで使用される書式設定規則については、[複合書式指定](composite-format.md)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="55053-130">For information about formatting conventions used with this method, see the section on [composite formatting](composite-format.md).</span></span>

<span data-ttu-id="55053-131">次の例では、`Format` メソッドを使用して、整数型の変数を使用する文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="55053-131">The following example uses the `Format` method to create a string that uses an integer variable.</span></span>

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

<span data-ttu-id="55053-132">この例では、[DateTime.Now](xref:System.DateTime.Now) は、現在のスレッドに関連付けられているカルチャで指定された方法で現在の日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="55053-132">In this example, [DateTime.Now](xref:System.DateTime.Now) displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>

### <a name="concat"></a><span data-ttu-id="55053-133">Concat</span><span class="sxs-lookup"><span data-stu-id="55053-133">Concat</span></span>

<span data-ttu-id="55053-134">`String.Concat` メソッドを使用すると、2 つ以上の既存のオブジェクトから新しい文字列オブジェクトを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="55053-134">The `String.Concat` method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="55053-135">言語に依存せずに文字列を連結する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="55053-135">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="55053-136">このメソッドは、`System.Object` から派生したすべてのクラスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="55053-136">This method accepts any class that derives from `System.Object`.</span></span> <span data-ttu-id="55053-137">次の例では、2 つの既存の文字列オブジェクトおよび区切り文字から文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="55053-137">The following example creates a string from two existing string objects and a separating character.</span></span>

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

### <a name="join"></a><span data-ttu-id="55053-138">Join</span><span class="sxs-lookup"><span data-stu-id="55053-138">Join</span></span>

<span data-ttu-id="55053-139">`String.Join` メソッドは、文字列の配列および区切り文字列から新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="55053-139">The `String.Join` method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="55053-140">このメソッドは、複数の文字列を連結して、たとえばコンマで区切られたリストを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="55053-140">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>

<span data-ttu-id="55053-141">次の例では、スペースを使用して文字列の配列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="55053-141">The following example uses a space to bind a string array.</span></span>

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

### <a name="insert"></a><span data-ttu-id="55053-142">挿入</span><span class="sxs-lookup"><span data-stu-id="55053-142">Insert</span></span>

<span data-ttu-id="55053-143">`String.Insert` メソッドは、別の文字列内の指定の位置に文字列を挿入することで、新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="55053-143">The `String.Insert` method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="55053-144">このメソッドは、0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="55053-144">This method uses a zero-based index.</span></span> <span data-ttu-id="55053-145">次の例では、`MyString` の&5; 番目のインデックス位置に文字列を挿入し、この値を持つ新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="55053-145">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>

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

### <a name="copyto"></a><span data-ttu-id="55053-146">CopyTo</span><span class="sxs-lookup"><span data-stu-id="55053-146">CopyTo</span></span>

<span data-ttu-id="55053-147">`String.CopyTo` メソッドは、文字配列に文字列の部分をコピーします。</span><span class="sxs-lookup"><span data-stu-id="55053-147">The `String.CopyTo` method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="55053-148">文字列の開始インデックスと、コピーする文字数の両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="55053-148">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="55053-149">このメソッドは、ソース インデックス、文字配列、コピー先のインデックス、およびコピーする文字数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="55053-149">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="55053-150">すべてのインデックスは&0; から始まります。</span><span class="sxs-lookup"><span data-stu-id="55053-150">All indexes are zero-based.</span></span>

<span data-ttu-id="55053-151">次の例では、`CopyTo` メソッドを使用して、文字列オブジェクトから文字配列の最初のインデックス位置に、単語 "Hello" の文字をコピーします。</span><span class="sxs-lookup"><span data-stu-id="55053-151">The following example uses the `CopyTo` method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="55053-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="55053-152">See Also</span></span>

[<span data-ttu-id="55053-153">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="55053-153">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="55053-154">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="55053-154">Composite formatting</span></span>](composite-format.md)


