---
title: "既定値の一覧表 (C# リファレンス)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034c1daf495c50e299fec4c5bf399652dad08ce
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2017
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="27971-102">既定値の一覧表 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="27971-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="27971-103">次の表では、既定のコンストラクターによって返される値型の既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="27971-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="27971-104">既定のコンストラクターは、次のように `new` 演算子を使って呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="27971-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="27971-105">上のステートメントは次のステートメントと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="27971-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="27971-106">C# では初期化されていない変数を使うことができないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="27971-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="27971-107">値の種類</span><span class="sxs-lookup"><span data-stu-id="27971-107">Value type</span></span>|<span data-ttu-id="27971-108">既定値</span><span class="sxs-lookup"><span data-stu-id="27971-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="27971-109">bool</span><span class="sxs-lookup"><span data-stu-id="27971-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="27971-110">byte</span><span class="sxs-lookup"><span data-stu-id="27971-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="27971-111">0</span><span class="sxs-lookup"><span data-stu-id="27971-111">0</span></span>|
|[<span data-ttu-id="27971-112">char</span><span class="sxs-lookup"><span data-stu-id="27971-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="27971-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="27971-113">'\0'</span></span>|
|[<span data-ttu-id="27971-114">decimal</span><span class="sxs-lookup"><span data-stu-id="27971-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="27971-115">0 M</span><span class="sxs-lookup"><span data-stu-id="27971-115">0M</span></span>|
|[<span data-ttu-id="27971-116">double</span><span class="sxs-lookup"><span data-stu-id="27971-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="27971-117">0.0D</span><span class="sxs-lookup"><span data-stu-id="27971-117">0.0D</span></span>|
|[<span data-ttu-id="27971-118">enum</span><span class="sxs-lookup"><span data-stu-id="27971-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="27971-119">式 (E)0 によって生成される値。E は列挙型識別子です。</span><span class="sxs-lookup"><span data-stu-id="27971-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="27971-120">float</span><span class="sxs-lookup"><span data-stu-id="27971-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="27971-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="27971-121">0.0F</span></span>|
|[<span data-ttu-id="27971-122">int</span><span class="sxs-lookup"><span data-stu-id="27971-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="27971-123">0</span><span class="sxs-lookup"><span data-stu-id="27971-123">0</span></span>|
|[<span data-ttu-id="27971-124">long</span><span class="sxs-lookup"><span data-stu-id="27971-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="27971-125">0L</span><span class="sxs-lookup"><span data-stu-id="27971-125">0L</span></span>|
|[<span data-ttu-id="27971-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="27971-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="27971-127">0</span><span class="sxs-lookup"><span data-stu-id="27971-127">0</span></span>|
|[<span data-ttu-id="27971-128">short</span><span class="sxs-lookup"><span data-stu-id="27971-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="27971-129">0</span><span class="sxs-lookup"><span data-stu-id="27971-129">0</span></span>|
|[<span data-ttu-id="27971-130">struct</span><span class="sxs-lookup"><span data-stu-id="27971-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="27971-131">すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。</span><span class="sxs-lookup"><span data-stu-id="27971-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="27971-132">uint</span><span class="sxs-lookup"><span data-stu-id="27971-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="27971-133">0</span><span class="sxs-lookup"><span data-stu-id="27971-133">0</span></span>|
|[<span data-ttu-id="27971-134">ulong</span><span class="sxs-lookup"><span data-stu-id="27971-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="27971-135">0</span><span class="sxs-lookup"><span data-stu-id="27971-135">0</span></span>|
|[<span data-ttu-id="27971-136">ushort</span><span class="sxs-lookup"><span data-stu-id="27971-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="27971-137">0</span><span class="sxs-lookup"><span data-stu-id="27971-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="27971-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="27971-138">See also</span></span>
 [<span data-ttu-id="27971-139">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="27971-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="27971-140">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="27971-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27971-141">値型の一覧表</span><span class="sxs-lookup"><span data-stu-id="27971-141">Value Types Table</span></span>](../../../csharp/language-reference/keywords/value-types-table.md)  
 [<span data-ttu-id="27971-142">値型</span><span class="sxs-lookup"><span data-stu-id="27971-142">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="27971-143">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="27971-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="27971-144">型のリファレンス表</span><span class="sxs-lookup"><span data-stu-id="27971-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
