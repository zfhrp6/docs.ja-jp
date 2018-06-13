---
title: 既定値の一覧表 (C# リファレンス)
description: 既定のコンストラクターによって返される値の型の既定値について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218791"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="66579-103">既定値の一覧表 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="66579-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="66579-104">次の表では、既定のコンストラクターによって返される値型の既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="66579-104">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="66579-105">既定のコンストラクターは、次のように `new` 演算子を使って呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="66579-105">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="66579-106">上のステートメントは次のステートメントと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="66579-106">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="66579-107">C# では初期化されていない変数を使うことができないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="66579-107">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="66579-108">値の種類</span><span class="sxs-lookup"><span data-stu-id="66579-108">Value type</span></span>|<span data-ttu-id="66579-109">既定値</span><span class="sxs-lookup"><span data-stu-id="66579-109">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="66579-110">bool</span><span class="sxs-lookup"><span data-stu-id="66579-110">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="66579-111">byte</span><span class="sxs-lookup"><span data-stu-id="66579-111">byte</span></span>](byte.md)|<span data-ttu-id="66579-112">0</span><span class="sxs-lookup"><span data-stu-id="66579-112">0</span></span>|
|[<span data-ttu-id="66579-113">char</span><span class="sxs-lookup"><span data-stu-id="66579-113">char</span></span>](char.md)|<span data-ttu-id="66579-114">'\0'</span><span class="sxs-lookup"><span data-stu-id="66579-114">'\0'</span></span>|
|[<span data-ttu-id="66579-115">decimal</span><span class="sxs-lookup"><span data-stu-id="66579-115">decimal</span></span>](decimal.md)|<span data-ttu-id="66579-116">0M</span><span class="sxs-lookup"><span data-stu-id="66579-116">0M</span></span>|
|[<span data-ttu-id="66579-117">double</span><span class="sxs-lookup"><span data-stu-id="66579-117">double</span></span>](double.md)|<span data-ttu-id="66579-118">0.0D</span><span class="sxs-lookup"><span data-stu-id="66579-118">0.0D</span></span>|
|[<span data-ttu-id="66579-119">enum</span><span class="sxs-lookup"><span data-stu-id="66579-119">enum</span></span>](enum.md)|<span data-ttu-id="66579-120">式 (E)0 によって生成される値。E は列挙型識別子です。</span><span class="sxs-lookup"><span data-stu-id="66579-120">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="66579-121">float</span><span class="sxs-lookup"><span data-stu-id="66579-121">float</span></span>](float.md)|<span data-ttu-id="66579-122">0.0F</span><span class="sxs-lookup"><span data-stu-id="66579-122">0.0F</span></span>|
|[<span data-ttu-id="66579-123">int</span><span class="sxs-lookup"><span data-stu-id="66579-123">int</span></span>](int.md)|<span data-ttu-id="66579-124">0</span><span class="sxs-lookup"><span data-stu-id="66579-124">0</span></span>|
|[<span data-ttu-id="66579-125">long</span><span class="sxs-lookup"><span data-stu-id="66579-125">long</span></span>](long.md)|<span data-ttu-id="66579-126">0L</span><span class="sxs-lookup"><span data-stu-id="66579-126">0L</span></span>|
|[<span data-ttu-id="66579-127">sbyte</span><span class="sxs-lookup"><span data-stu-id="66579-127">sbyte</span></span>](sbyte.md)|<span data-ttu-id="66579-128">0</span><span class="sxs-lookup"><span data-stu-id="66579-128">0</span></span>|
|[<span data-ttu-id="66579-129">short</span><span class="sxs-lookup"><span data-stu-id="66579-129">short</span></span>](short.md)|<span data-ttu-id="66579-130">0</span><span class="sxs-lookup"><span data-stu-id="66579-130">0</span></span>|
|[<span data-ttu-id="66579-131">struct</span><span class="sxs-lookup"><span data-stu-id="66579-131">struct</span></span>](struct.md)|<span data-ttu-id="66579-132">すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。</span><span class="sxs-lookup"><span data-stu-id="66579-132">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="66579-133">uint</span><span class="sxs-lookup"><span data-stu-id="66579-133">uint</span></span>](uint.md)|<span data-ttu-id="66579-134">0</span><span class="sxs-lookup"><span data-stu-id="66579-134">0</span></span>|
|[<span data-ttu-id="66579-135">ulong</span><span class="sxs-lookup"><span data-stu-id="66579-135">ulong</span></span>](ulong.md)|<span data-ttu-id="66579-136">0</span><span class="sxs-lookup"><span data-stu-id="66579-136">0</span></span>|
|[<span data-ttu-id="66579-137">ushort</span><span class="sxs-lookup"><span data-stu-id="66579-137">ushort</span></span>](ushort.md)|<span data-ttu-id="66579-138">0</span><span class="sxs-lookup"><span data-stu-id="66579-138">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="66579-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="66579-139">See also</span></span>
 [<span data-ttu-id="66579-140">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="66579-140">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="66579-141">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="66579-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="66579-142">値型の一覧表</span><span class="sxs-lookup"><span data-stu-id="66579-142">Value Types Table</span></span>](value-types-table.md)  
 [<span data-ttu-id="66579-143">値型</span><span class="sxs-lookup"><span data-stu-id="66579-143">Value Types</span></span>](value-types.md)  
 [<span data-ttu-id="66579-144">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="66579-144">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="66579-145">型のリファレンス表</span><span class="sxs-lookup"><span data-stu-id="66579-145">Reference Tables for Types</span></span>](reference-tables-for-types.md)
