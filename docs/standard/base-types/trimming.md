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
ms.translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 96cf08c0de8ba73d931d561187369ccf8b091651
ms.contentlocale: ja-jp
ms.lasthandoff: 11/05/2016

---

# <a name="trimming-and-removing-characters-from-strings"></a><span data-ttu-id="fadc3-104">文字列からの文字のトリムと削除</span><span class="sxs-lookup"><span data-stu-id="fadc3-104">Trimming and removing characters from strings</span></span>

<span data-ttu-id="fadc3-105">文章を個々の単語に分割すると、単語の先頭または末尾に空白が残る場合があります。</span><span class="sxs-lookup"><span data-stu-id="fadc3-105">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="fadc3-106">そのような場合は、[System.String](https://docs.microsoft.com/dotnet/core/api/System.String) クラスのトリム メソッドのいずれかを使用して、文字列内の指定した位置から任意の数の空白またはその他の文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="fadc3-106">In this situation, you can use one of the trim methods in the [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="fadc3-107">使用できるトリム メソッドとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-107">The following table describes the available trim methods.</span></span>

<span data-ttu-id="fadc3-108">メソッド名</span><span class="sxs-lookup"><span data-stu-id="fadc3-108">Method name</span></span> | <span data-ttu-id="fadc3-109">使用</span><span class="sxs-lookup"><span data-stu-id="fadc3-109">Use</span></span>
----------- | ---
[<span data-ttu-id="fadc3-110">String.Trim</span><span class="sxs-lookup"><span data-stu-id="fadc3-110">String.Trim</span></span>](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | <span data-ttu-id="fadc3-111">文字列の先頭と末尾から、空白または文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-111">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>
<span data-ttu-id="fadc3-112">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[]))</span><span class="sxs-lookup"><span data-stu-id="fadc3-112">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[]))</span></span> | <span data-ttu-id="fadc3-113">文字列の末尾から、文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-113">Removes characters specified in an array of characters from the end of a string.</span></span>
<span data-ttu-id="fadc3-114">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[]))</span><span class="sxs-lookup"><span data-stu-id="fadc3-114">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[]))</span></span> | <span data-ttu-id="fadc3-115">文字列の先頭から、文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-115">Removes characters specified in an array of characters from the beginning of a string.</span></span>
<span data-ttu-id="fadc3-116">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="fadc3-116">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32))</span></span> | <span data-ttu-id="fadc3-117">文字列内の指定したインデックス位置から、指定した数の文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-117">Removes a specified number of characters from a specified index position in a string.</span></span>


## <a name="trim"></a><span data-ttu-id="fadc3-118">Trim</span><span class="sxs-lookup"><span data-stu-id="fadc3-118">Trim</span></span>

<span data-ttu-id="fadc3-119">[String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) メソッドを使用すると、文字列の両端から空白を簡単に削除できます。メソッドの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-119">You can easily remove white spaces from both ends of a string by using the [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) method, as shown in the following example.</span></span>

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

<span data-ttu-id="fadc3-120">文字列の先頭と末尾から、文字配列で指定した文字を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="fadc3-120">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="fadc3-121">次に、空白文字、ピリオド、およびアスタリスクを削除する例を示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-121">The following example removes white-space characters, periods, and asterisks.</span></span>

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

## <a name="trimend"></a><span data-ttu-id="fadc3-122">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="fadc3-122">TrimEnd</span></span>

<span data-ttu-id="fadc3-123">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドは、文字列の末尾から文字を削除して新しい文字列オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-123">The [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="fadc3-124">このメソッドには、削除する文字を指定する文字配列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="fadc3-124">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="fadc3-125">文字配列内での要素の順序は、トリム操作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="fadc3-125">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="fadc3-126">トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-126">The trim stops when a character not specified in the array is found.</span></span>

<span data-ttu-id="fadc3-127">TrimEnd メソッドを使用して文字列の末尾の数文字を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-127">The following example removes the last letters of a string using the TrimEnd method.</span></span> <span data-ttu-id="fadc3-128">この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'r'` という文字と `'W'` という文字の順序を逆にしてあります。</span><span class="sxs-lookup"><span data-stu-id="fadc3-128">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="fadc3-129">このコードは、`MyString` の最後の単語だけでなく、最初の単語の一部も削除します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-129">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>

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

<span data-ttu-id="fadc3-130">このコードは、コンソールに `He` と出力します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-130">This code displays `He` to the console.</span></span>

<span data-ttu-id="fadc3-131">[TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドを使用して、文字列の最後の単語を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-131">The following example removes the last word of a string using the [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method.</span></span> <span data-ttu-id="fadc3-132">このコードでは、`Hello` という単語の後にコンマがありますが、削除する文字の配列にコンマは指定されていないため、コンマの位置でトリムが停止します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-132">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>

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

<span data-ttu-id="fadc3-133">このコードは、コンソールに `Hello,` と出力します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-133">This code displays `Hello,` to the console.</span></span>

## <a name="trimstart"></a><span data-ttu-id="fadc3-134">TrimStart</span><span class="sxs-lookup"><span data-stu-id="fadc3-134">TrimStart</span></span>

<span data-ttu-id="fadc3-135">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) メソッドは [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドと似ていますが、既存の文字列オブジェクトの先頭から文字を削除して新しい文字列を作成する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="fadc3-135">The [String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) method is similar to the [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="fadc3-136">[TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) メソッドには、削除する文字を指定する文字配列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="fadc3-136">An array of characters is passed to the [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) method to specify the characters to be removed.</span></span> <span data-ttu-id="fadc3-137">[TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) メソッドの場合と同様に、文字配列内での要素の順序はトリム操作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="fadc3-137">As with the [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="fadc3-138">トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-138">The trim stops when a character not specified in the array is found.</span></span>

<span data-ttu-id="fadc3-139">文字列の最初の単語を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-139">The following example removes the first word of a string.</span></span> <span data-ttu-id="fadc3-140">この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'l'` という文字と `'H'` という文字の順序を逆にしてあります。</span><span class="sxs-lookup"><span data-stu-id="fadc3-140">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>

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

<span data-ttu-id="fadc3-141">このコードは、コンソールに `World!` と出力します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-141">This code displays `World!` to the console.</span></span>

## <a name="remove"></a><span data-ttu-id="fadc3-142">削除</span><span class="sxs-lookup"><span data-stu-id="fadc3-142">Remove</span></span>

<span data-ttu-id="fadc3-143">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) メソッドは、既存の文字列内の指定した位置を開始位置として、指定した数の文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-143">The [String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="fadc3-144">このメソッドは、インデックスが 0 から始まっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="fadc3-144">This method assumes a zero-based index.</span></span>

<span data-ttu-id="fadc3-145">文字列の 0 から始まる 5 番目のインデックスを開始位置として、10 文字を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-145">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>

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

<span data-ttu-id="fadc3-146">また、[String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) メソッドを呼び出し、置換対象として空の文字列 ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) を指定することで、文字列から指定した文字または部分文字列を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="fadc3-146">You can also remove a specified character or substring from a string by calling the [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) method and specifying an empty string ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) as the replacement.</span></span> <span data-ttu-id="fadc3-147">文字列からすべてのコンマを削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fadc3-147">The following example removes all commas from a string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fadc3-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="fadc3-148">See Also</span></span>

[<span data-ttu-id="fadc3-149">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="fadc3-149">Basic string operations</span></span>](basic-string-operations.md)


