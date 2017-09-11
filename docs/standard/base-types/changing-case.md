---
title: "大文字と小文字の変更"
description: "大文字と小文字の変更"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 023f40969095627242d3652add853eb999c30c4b
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="changing-case"></a><span data-ttu-id="38c59-104">大文字と小文字の変更</span><span class="sxs-lookup"><span data-stu-id="38c59-104">Changing case</span></span>

<span data-ttu-id="38c59-105">ユーザーからの入力を受け付けるアプリケーションを記述する場合、ユーザーがデータ入力に使用するケースを正確に予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="38c59-105">If you write an application that accepts input from a user, you can never be sure what case he or she will use to enter the data.</span></span> <span data-ttu-id="38c59-106">多くの場合、特にユーザー インターフェイスにそれを表示する場合には、文字列に一貫性のあるケースを使用することが求められます。</span><span class="sxs-lookup"><span data-stu-id="38c59-106">Often, you want strings to be cased consistently, particularly if you are displaying them in the user interface.</span></span> <span data-ttu-id="38c59-107">次の表は、2 つのケース変更方式を示しています。</span><span class="sxs-lookup"><span data-stu-id="38c59-107">The following table describes two case-changing methods.</span></span>

<span data-ttu-id="38c59-108">メソッド名</span><span class="sxs-lookup"><span data-stu-id="38c59-108">Method name</span></span> | <span data-ttu-id="38c59-109">使用</span><span class="sxs-lookup"><span data-stu-id="38c59-109">Use</span></span>
----------- | ---
[<span data-ttu-id="38c59-110">String.ToUpper</span><span class="sxs-lookup"><span data-stu-id="38c59-110">String.ToUpper</span></span>](xref:System.String.ToUpper) | <span data-ttu-id="38c59-111">文字列内のすべての文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="38c59-111">Converts all characters in a string to uppercase.</span></span>
[<span data-ttu-id="38c59-112">String.ToLower</span><span class="sxs-lookup"><span data-stu-id="38c59-112">String.ToLower</span></span>](xref:System.String.ToLower) | <span data-ttu-id="38c59-113">文字列内のすべての文字を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="38c59-113">Converts all characters in a string to lowercase.</span></span>

> [!WARNING]  
> <span data-ttu-id="38c59-114">`String.ToUpper` と `String.ToLower` の方式を使用して、文字列を比較したり等しいかどうかをテストしたりする目的で、それらの文字列を変換するべきではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38c59-114">Note that the `String.ToUpper` and `String.ToLower` methods should not be used to convert strings in order to compare them or test them for equality.</span></span> 

## <a name="comparing-strings-of-mixed-case"></a><span data-ttu-id="38c59-115">大小混合文字の文字列を比較する</span><span class="sxs-lookup"><span data-stu-id="38c59-115">Comparing strings of mixed case</span></span>

<span data-ttu-id="38c59-116">大小混合文字の文字列を比較してそれらが等しいかどうかを判別するには、*comparisonType* パラメーターのある [String](xref:System) `Equals` メソッドのいずれかのオーバーロードを呼び出して、*comparisonType* 引数に [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) または [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="38c59-116">To compare strings of mixed case to determine whether they are equal, their, call one of the overloads of the [String](xref:System) `Equals` method with a *comparisonType* parameter, and provide a value of either [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for the *comparisonType* argument.</span></span> 

<span data-ttu-id="38c59-117">詳細については、「[文字列を使用するためのベスト プラクティス](best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38c59-117">For more information, see [Best Practices for Using Strings](best-practices.md).</span></span> 

## <a name="toupper"></a><span data-ttu-id="38c59-118">ToUpper</span><span class="sxs-lookup"><span data-stu-id="38c59-118">ToUpper</span></span>

<span data-ttu-id="38c59-119">[String.ToUpper](xref:System.String.ToUpper) メソッドは文字列内のすべての文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="38c59-119">The [String.ToUpper](xref:System.String.ToUpper) method changes all characters in a string to uppercase.</span></span> <span data-ttu-id="38c59-120">次の例では、文字列 "Hello World!" を</span><span class="sxs-lookup"><span data-stu-id="38c59-120">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="38c59-121">大小混合文字から大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="38c59-121">from mixed case to uppercase.</span></span>

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

## <a name="tolower"></a><span data-ttu-id="38c59-122">ToLower</span><span class="sxs-lookup"><span data-stu-id="38c59-122">ToLower</span></span>

<span data-ttu-id="38c59-123">[String.ToLower](xref:System.String.ToLower) メソッドは、前のメソッドと似ていますが、代わりに文字列内のすべての文字を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="38c59-123">The [String.ToLower](xref:System.String.ToLower) method is similar to the previous method, but instead converts all the characters in a string to lowercase.</span></span> <span data-ttu-id="38c59-124">次の例では、文字列 "Hello World!" を</span><span class="sxs-lookup"><span data-stu-id="38c59-124">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="38c59-125">小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="38c59-125">to lowercase.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38c59-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="38c59-126">See Also</span></span>

[<span data-ttu-id="38c59-127">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="38c59-127">Basic string operations</span></span>](basic-string-operations.md)

