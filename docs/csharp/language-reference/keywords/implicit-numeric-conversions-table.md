---
title: "暗黙的な数値変換の一覧表 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="95132-102">暗黙的な数値変換の一覧表 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="95132-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="95132-103">定義済みの暗黙的な数値変換を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="95132-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="95132-104">暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="95132-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="95132-105">変換前</span><span class="sxs-lookup"><span data-stu-id="95132-105">From</span></span>|<span data-ttu-id="95132-106">目的</span><span class="sxs-lookup"><span data-stu-id="95132-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="95132-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="95132-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="95132-108">`short`、`int`、`long`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-109">byte</span><span class="sxs-lookup"><span data-stu-id="95132-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="95132-110">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-111">short</span><span class="sxs-lookup"><span data-stu-id="95132-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="95132-112">`int`、`long`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-113">ushort</span><span class="sxs-lookup"><span data-stu-id="95132-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="95132-114">`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-115">int</span><span class="sxs-lookup"><span data-stu-id="95132-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="95132-116">`long`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-117">uint</span><span class="sxs-lookup"><span data-stu-id="95132-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="95132-118">`long`、`ulong`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-119">long</span><span class="sxs-lookup"><span data-stu-id="95132-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="95132-120">`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-121">char</span><span class="sxs-lookup"><span data-stu-id="95132-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="95132-122">`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="95132-123">float</span><span class="sxs-lookup"><span data-stu-id="95132-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="95132-124">ulong</span><span class="sxs-lookup"><span data-stu-id="95132-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="95132-125">`float`、`double`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="95132-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95132-126">コメント</span><span class="sxs-lookup"><span data-stu-id="95132-126">Remarks</span></span>  
  
-   <span data-ttu-id="95132-127">`int`、`uint`、`long`、または `ulong` から `float` への変換と `long` から `ulong` または `double` への変換では、有効桁数が失われる場合があります (絶対値ではありません)。</span><span class="sxs-lookup"><span data-stu-id="95132-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="95132-128">`char` 型への暗黙的な変換はありません。</span><span class="sxs-lookup"><span data-stu-id="95132-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="95132-129">浮動小数点型と `decimal` 型の間に、暗黙的な変換はありません。</span><span class="sxs-lookup"><span data-stu-id="95132-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="95132-130">`int` 型の定数式は、定数式の値が変換後の型の範囲内にある場合、`sbyte`、`byte`、`short`、`ushort`、`uint`、または `ulong` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="95132-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="95132-131">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="95132-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95132-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="95132-132">See Also</span></span>  
 [<span data-ttu-id="95132-133">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="95132-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="95132-134">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="95132-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95132-135">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="95132-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="95132-136">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="95132-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="95132-137">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="95132-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="95132-138">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="95132-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
