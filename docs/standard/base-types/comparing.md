---
title: "文字列の比較"
description: "文字列の比較"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 47ee37886fa2662a89730e9d52ee04987e37da2f
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="comparing-strings"></a><span data-ttu-id="f07b4-104">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="f07b4-104">Comparing strings</span></span>

<span data-ttu-id="f07b4-105">.NET は、文字列の値を比較するためのメソッドをいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="f07b4-106">これらの値の比較メソッドとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-106">The following table lists and describes the value-comparison methods.</span></span>

<span data-ttu-id="f07b4-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="f07b4-107">Method name</span></span> | <span data-ttu-id="f07b4-108">使用</span><span class="sxs-lookup"><span data-stu-id="f07b4-108">Use</span></span>
----------- | ---
<span data-ttu-id="f07b4-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f07b4-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="f07b4-110">2 つの文字列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-110">Compares the values of two strings.</span></span> <span data-ttu-id="f07b4-111">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-111">Returns an integer value.</span></span>
<span data-ttu-id="f07b4-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f07b4-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="f07b4-113">ローカル カルチャに関係なく、2 つの文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-113">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="f07b4-114">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-114">Returns an integer value.</span></span>
<span data-ttu-id="f07b4-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="f07b4-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="f07b4-116">現在の文字列オブジェクトを別の文字列と比較します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-116">Compares the current string object to another string.</span></span> <span data-ttu-id="f07b4-117">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-117">Returns an integer value.</span></span>
<span data-ttu-id="f07b4-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span><span class="sxs-lookup"><span data-stu-id="f07b4-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span></span> | <span data-ttu-id="f07b4-119">文字列が、渡された文字列で始まるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-119">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="f07b4-120">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-120">Returns a Boolean value.</span></span>
<span data-ttu-id="f07b4-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="f07b4-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="f07b4-122">文字列が、渡された文字列で終わるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-122">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="f07b4-123">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-123">Returns a Boolean value.</span></span>
<span data-ttu-id="f07b4-124">[String.Equals](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="f07b4-124">[String.Equals](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="f07b4-125">2 つの文字列が等しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-125">Determines whether two strings are the same.</span></span> <span data-ttu-id="f07b4-126">Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-126">Returns a Boolean value.</span></span>
<span data-ttu-id="f07b4-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="f07b4-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span></span> | <span data-ttu-id="f07b4-128">検索対象文字列の先頭から開始して、特定の文字または文字列が見つかったインデックス位置を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-128">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="f07b4-129">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-129">Returns an integer value.</span></span>
<span data-ttu-id="f07b4-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="f07b4-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span></span> | <span data-ttu-id="f07b4-131">検索対象文字列の末尾から開始して、特定の文字または文字列が見つかったインデックス位置を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-131">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="f07b4-132">整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-132">Returns an integer value.</span></span>

## <a name="compare"></a><span data-ttu-id="f07b4-133">比較</span><span class="sxs-lookup"><span data-stu-id="f07b4-133">Compare</span></span>

<span data-ttu-id="f07b4-134">静的な [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、2 つの文字列を詳細に比較する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-134">The static [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="f07b4-135">このメソッドはカルチャに対応しています。</span><span class="sxs-lookup"><span data-stu-id="f07b4-135">This method is culturally aware.</span></span> <span data-ttu-id="f07b4-136">この機能は、2 つの文字列、または&2; つの文字列の部分文字列を比較するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-136">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="f07b4-137">また、大文字と小文字の区別やカルチャの違いを考慮または無視するためのオーバーロードも用意されています。</span><span class="sxs-lookup"><span data-stu-id="f07b4-137">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="f07b4-138">このメソッドによって返される可能性のある&3; つの整数値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-138">The following table shows the three integer values that this method might return.</span></span> 

<span data-ttu-id="f07b4-139">戻り値</span><span class="sxs-lookup"><span data-stu-id="f07b4-139">Return value</span></span> | <span data-ttu-id="f07b4-140">条件</span><span class="sxs-lookup"><span data-stu-id="f07b4-140">Condition</span></span>
------------ | ---------
<span data-ttu-id="f07b4-141">負の整数</span><span class="sxs-lookup"><span data-stu-id="f07b4-141">A negative integer</span></span> | <span data-ttu-id="f07b4-142">最初の文字列は、並べ替え順序が&2; 番目の文字列の前に置かれます。そうでない場合、最初の文字列は `null` です。</span><span class="sxs-lookup"><span data-stu-id="f07b4-142">The first string precedes the second string in the sort order, or the first string is `null`.</span></span>
<span data-ttu-id="f07b4-143">0</span><span class="sxs-lookup"><span data-stu-id="f07b4-143">0</span></span> | <span data-ttu-id="f07b4-144">最初の文字列と&2; 番目の文字列は等価です。そうでない場合、両方の文字列が `null` です。</span><span class="sxs-lookup"><span data-stu-id="f07b4-144">The first string and the second string are equal, or both strings are `null`.</span></span>
<span data-ttu-id="f07b4-145">正の整数、または 1</span><span class="sxs-lookup"><span data-stu-id="f07b4-145">A positive integer, or 1</span></span> | <span data-ttu-id="f07b4-146">最初の文字列は、並べ替え順序が&2; 番目の文字列の後に続きます。そうでない場合、2 番目の文字列は null です。</span><span class="sxs-lookup"><span data-stu-id="f07b4-146">The first string follows the second string in the sort order, or the second string is null.</span></span>
 
> [!IMPORTANT]
> <span data-ttu-id="f07b4-147">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="f07b4-147">The [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="f07b4-148">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f07b4-148">You should not use the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="f07b4-149">2 つの文字列が等価かどうかを判断するには、[String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f07b4-149">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="f07b4-150">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドを使用して、2 つの文字列の相対値を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-150">The following example uses the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to determine the relative values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

<span data-ttu-id="f07b4-151">この例は、コンソールに `-1` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-151">This example displays `-1` to the console.</span></span>

## <a name="compareordinal"></a><span data-ttu-id="f07b4-152">CompareOrdinal</span><span class="sxs-lookup"><span data-stu-id="f07b4-152">CompareOrdinal</span></span>

<span data-ttu-id="f07b4-153">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、ローカル カルチャを考慮せずに&2; つの文字列オブジェクトを比較します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-153">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="f07b4-154">このメソッドの戻り値は、上の表で示した `Compare` メソッドによって返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="f07b4-154">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f07b4-155">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="f07b4-155">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="f07b4-156">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f07b4-156">You should not use the [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="f07b4-157">2 つの文字列が等価かどうかを判断するには、[String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f07b4-157">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="f07b4-158">`CompareOrdinal` メソッドを使用して、2 つの文字列の値を比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-158">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

<span data-ttu-id="f07b4-159">この例は、コンソールに `-32` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-159">This example displays `-32` to the console.</span></span>

## <a name="compareto"></a><span data-ttu-id="f07b4-160">CompareTo</span><span class="sxs-lookup"><span data-stu-id="f07b4-160">CompareTo</span></span>

<span data-ttu-id="f07b4-161">[String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドは、現在の文字列オブジェクトがカプセル化している文字列を別の文字列またはオブジェクトと比較します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-161">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="f07b4-162">このメソッドの戻り値は、上の表で示した `String.Compare` メソッドによって返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="f07b4-162">The return values of this method are identical to the values returned by the `String.Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f07b4-163">[String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドは、主に文字列の並べ替えに使用するものです。</span><span class="sxs-lookup"><span data-stu-id="f07b4-163">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="f07b4-164">等価性をテストする (つまり、ある文字列が別の文字列より大きいか小さいかを問題にせずに戻り値 0 を明示的に検索する) 目的では、[String.CompareTo](xref:System.String.CompareTo(System.String)) メソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f07b4-164">You should not use the [String.CompareTo](xref:System.String.CompareTo(System.String)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="f07b4-165">2 つの文字列が等価かどうかを判断するには、[String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f07b4-165">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="f07b4-166">`String.CompareTo` メソッドを使用して、`string1` オブジェクトを `string2` オブジェクトと比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-166">The following example uses the `String.CompareTo` method to compare the `string1` object to the `string2` object.</span></span>

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

<span data-ttu-id="f07b4-167">この例は、コンソールに `-1` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-167">This example displays `-1` to the console.</span></span>

## <a name="equals"></a><span data-ttu-id="f07b4-168">次の値に等しい</span><span class="sxs-lookup"><span data-stu-id="f07b4-168">Equals</span></span>

<span data-ttu-id="f07b4-169">[String.Equals](xref:System.String.CompareTo(System.String)) メソッドを使用すると、2 つの文字列が等しいかどうかを簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-169">The [String.Equals](xref:System.String.CompareTo(System.String)) method can easily determine if two strings are the same.</span></span> <span data-ttu-id="f07b4-170">このメソッドは大文字と小文字を区別し、`true` または `false` の Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-170">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="f07b4-171">このメソッドは、次の例に示すように、既存のクラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-171">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="f07b4-172">`Equals` メソッドを使用して、文字列オブジェクトに "Hello World" という語句が含まれているかどうかを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-172">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

<span data-ttu-id="f07b4-173">この例は、コンソールに `true` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-173">This example displays `true` to the console.</span></span>

<span data-ttu-id="f07b4-174">このメソッドは、静的メソッドとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-174">This method can also be used as a static method.</span></span> <span data-ttu-id="f07b4-175">静的メソッドを使用して、2 つの文字列オブジェクトを比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-175">The following example compares two string objects using a static method.</span></span>

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

<span data-ttu-id="f07b4-176">この例は、コンソールに `true` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-176">This example displays `true` to the console.</span></span>

## <a name="startswith-and-endswith"></a><span data-ttu-id="f07b4-177">StartsWith と EndsWith</span><span class="sxs-lookup"><span data-stu-id="f07b4-177">StartsWith and EndsWith</span></span>

<span data-ttu-id="f07b4-178">[String.StartsWith](xref:System.String.StartsWith(System.String)) メソッドを使用すると、文字列オブジェクトが、別の文字列を構成している文字と同じ文字で始まっているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-178">You can use the [String.StartsWith](xref:System.String.StartsWith(System.String)) method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="f07b4-179">このメソッドは大文字と小文字を区別し、現在の文字列オブジェクトが、渡された文字列で始まる場合は `true`、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-179">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="f07b4-180">このメソッドを使用して、文字列オブジェクトが "Hello" で始まるかどうかを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-180">The following example uses this method to determine if a string object begins with "Hello".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

<span data-ttu-id="f07b4-181">この例は、コンソールに `true` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-181">This example displays `true` to the console.</span></span>

<span data-ttu-id="f07b4-182">[String.EndsWith](xref:System.String.CompareTo(System.String)) メソッドは、渡された文字列を現在の文字列オブジェクトの末尾にある文字列と比較します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-182">The [String.EndsWith](xref:System.String.CompareTo(System.String)) method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="f07b4-183">このメソッドも Boolean 値を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-183">It also returns a Boolean value.</span></span> <span data-ttu-id="f07b4-184">`EndsWith` メソッドを使用して、文字列の末尾を確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-184">The following example checks the end of a string using the `EndsWith` method.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

<span data-ttu-id="f07b4-185">この例は、コンソールに `false` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-185">This example displays `false` to the console.</span></span>

## <a name="indexof-and-lastindexof"></a><span data-ttu-id="f07b4-186">IndexOf と LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="f07b4-186">IndexOf and LastIndexOf</span></span>

<span data-ttu-id="f07b4-187">[String.IndexOf](xref:System.String.IndexOf(System.Char)) メソッドを使用すると、特定の文字が文字列内で最初に出現する位置を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-187">You can use the [String.IndexOf](xref:System.String.IndexOf(System.Char)) method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="f07b4-188">このメソッドは大文字と小文字を区別し、文字列の先頭からカウントを開始し、0 から始まるインデックスを使用して、渡された文字が出現する位置を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-188">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="f07b4-189">指定した文字が見つからない場合は、値 –1 を返します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-189">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="f07b4-190">`IndexOf` メソッドを使用して、'`l`' という文字が文字列内で最初に出現する位置を検索する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-190">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

<span data-ttu-id="f07b4-191">この例は、コンソールに `2` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-191">This example displays `2` to the console.</span></span>

<span data-ttu-id="f07b4-192">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) メソッドは `String.IndexOf` メソッドに似ていますが、指定した文字列が文字列内で最後に出現する位置を返すという点が異なります。</span><span class="sxs-lookup"><span data-stu-id="f07b4-192">The [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="f07b4-193">このメソッドは大文字と小文字を区別し、0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-193">It is case-sensitive and uses a zero-based index.</span></span> 

<span data-ttu-id="f07b4-194">`LastIndexOf` メソッドを使用して、'`l`' という文字が文字列内で最後に出現する位置を検索する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-194">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

<span data-ttu-id="f07b4-195">この例は、コンソールに `9` と出力します。</span><span class="sxs-lookup"><span data-stu-id="f07b4-195">This example displays `9` to the console.</span></span>

<span data-ttu-id="f07b4-196">いずれのメソッドも、[String.Remove](xref:System.String.Remove(System.Int32)) メソッドと組み合わせて使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="f07b4-196">Both methods are useful when used in conjunction with the [String.Remove](xref:System.String.Remove(System.Int32)) method.</span></span> <span data-ttu-id="f07b4-197">`IndexOf` メソッドまたは `LastIndexOf` メソッドのいずれかを使用して文字の位置を取得し、その位置を `Remove method` メソッドに渡すことによって、その文字またはその文字で始まる単語を削除できます。</span><span class="sxs-lookup"><span data-stu-id="f07b4-197">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove method` in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="f07b4-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="f07b4-198">See Also</span></span>

[<span data-ttu-id="f07b4-199">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="f07b4-199">Basic string operations</span></span>](basic-string-operations.md)













