---
title: "文字列の埋め込み"
description: "文字列の埋め込み"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bc3cc9028b232cc2ba6ca3130c4bdb261c4a0a42
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="padding-strings"></a><span data-ttu-id="ff4a0-104">文字列の埋め込み</span><span class="sxs-lookup"><span data-stu-id="ff4a0-104">Padding strings</span></span>

<span data-ttu-id="ff4a0-105">ある文字の先頭または末尾に文字を埋め込み、合計を指定の長さにするとき、元の文字列で構成される新しい文字列を次の [System.String](xref:System.String) メソッドの&1; つを利用して作成します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-105">Use one of the following [System.String](xref:System.String) methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="ff4a0-106">埋め込み文字にはスペースや指定した文字を利用できます。結果的に、右揃えまたは左揃えのように見えます。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-106">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>

<span data-ttu-id="ff4a0-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="ff4a0-107">Method name</span></span> | <span data-ttu-id="ff4a0-108">使用</span><span class="sxs-lookup"><span data-stu-id="ff4a0-108">Use</span></span>
----------- | ---
<span data-ttu-id="ff4a0-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="ff4a0-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span></span> | <span data-ttu-id="ff4a0-110">文字列の先頭に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-110">Pads a string with leading characters to a specified total length.</span></span>
<span data-ttu-id="ff4a0-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="ff4a0-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span></span> | <span data-ttu-id="ff4a0-112">文字列の末尾に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-112">Pads a string with trailing characters to a specified total length.</span></span>

## <a name="padleft"></a><span data-ttu-id="ff4a0-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="ff4a0-113">PadLeft</span></span>

<span data-ttu-id="ff4a0-114">[String.PadLeft](xref:System.String.PadLeft(System.Int32)) メソッドでは、元の文字列の先頭に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-114">The [String.PadLeft](xref:System.String.PadLeft(System.Int32)) method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="ff4a0-115">[String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) メソッドでは、空白文字が埋め込み文字として利用されます。[String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) メソッドでは、独自の埋め込み文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-115">The [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) method uses white space as the padding character and the [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="ff4a0-116">次のコード例では、[PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) メソッドを利用し、長さが&20; 文字の新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-116">The following code example uses the [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="ff4a0-117">この例は、コンソールに "`--------Hello World!`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-117">The example displays "`--------Hello World!`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a><span data-ttu-id="ff4a0-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="ff4a0-118">PadRight</span></span>

<span data-ttu-id="ff4a0-119">[String.PadRight](xref:System.String.PadRight(System.Int32)) メソッドでは、元の文字列の末尾に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-119">The [String.PadRight](xref:System.String.PadRight(System.Int32)) method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="ff4a0-120">[String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) メソッドでは、空白文字が埋め込み文字として利用されます。[String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) メソッドでは、独自の埋め込み文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-120">The [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) method uses white space as the padding character and the [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="ff4a0-121">次のコード例では、[PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) メソッドを利用し、長さが&20; 文字の新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-121">The following code example uses the [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="ff4a0-122">この例は、コンソールに "`Hello World!--------`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="ff4a0-122">The example displays "`Hello World!--------`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a><span data-ttu-id="ff4a0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff4a0-123">See Also</span></span>

[<span data-ttu-id="ff4a0-124">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="ff4a0-124">Basic string operations</span></span>](basic-string-operations.md)


