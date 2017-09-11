---
title: "既定値の一覧表 (C# リファレンス)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
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
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: f8cf12317f1f0163028db003ff31604480da5d1c
ms.openlocfilehash: 975d416259778e0741347829d8a9c79aaa6cfc8c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="5e59c-102">既定値の一覧表 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5e59c-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="5e59c-103">次の表では、既定のコンストラクターによって返される値型の既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="5e59c-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="5e59c-104">既定のコンストラクターは、次のように `new` 演算子を使って呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5e59c-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="5e59c-105">上のステートメントは次のステートメントと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="5e59c-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="5e59c-106">C# では初期化されていない変数を使うことができないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5e59c-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="5e59c-107">値の種類</span><span class="sxs-lookup"><span data-stu-id="5e59c-107">Value type</span></span>|<span data-ttu-id="5e59c-108">既定値</span><span class="sxs-lookup"><span data-stu-id="5e59c-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="5e59c-109">bool</span><span class="sxs-lookup"><span data-stu-id="5e59c-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="5e59c-110">byte</span><span class="sxs-lookup"><span data-stu-id="5e59c-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="5e59c-111">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-111">0</span></span>|
|[<span data-ttu-id="5e59c-112">char</span><span class="sxs-lookup"><span data-stu-id="5e59c-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="5e59c-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="5e59c-113">'\0'</span></span>|
|[<span data-ttu-id="5e59c-114">decimal</span><span class="sxs-lookup"><span data-stu-id="5e59c-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="5e59c-115">0.0M</span><span class="sxs-lookup"><span data-stu-id="5e59c-115">0.0M</span></span>|
|[<span data-ttu-id="5e59c-116">double</span><span class="sxs-lookup"><span data-stu-id="5e59c-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="5e59c-117">0.0D</span><span class="sxs-lookup"><span data-stu-id="5e59c-117">0.0D</span></span>|
|[<span data-ttu-id="5e59c-118">enum</span><span class="sxs-lookup"><span data-stu-id="5e59c-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="5e59c-119">式 (E)0 によって生成される値。E は列挙型識別子です。</span><span class="sxs-lookup"><span data-stu-id="5e59c-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="5e59c-120">float</span><span class="sxs-lookup"><span data-stu-id="5e59c-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="5e59c-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="5e59c-121">0.0F</span></span>|
|[<span data-ttu-id="5e59c-122">int</span><span class="sxs-lookup"><span data-stu-id="5e59c-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="5e59c-123">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-123">0</span></span>|
|[<span data-ttu-id="5e59c-124">long</span><span class="sxs-lookup"><span data-stu-id="5e59c-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="5e59c-125">0L</span><span class="sxs-lookup"><span data-stu-id="5e59c-125">0L</span></span>|
|[<span data-ttu-id="5e59c-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="5e59c-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="5e59c-127">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-127">0</span></span>|
|[<span data-ttu-id="5e59c-128">short</span><span class="sxs-lookup"><span data-stu-id="5e59c-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="5e59c-129">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-129">0</span></span>|
|[<span data-ttu-id="5e59c-130">struct</span><span class="sxs-lookup"><span data-stu-id="5e59c-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="5e59c-131">すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。</span><span class="sxs-lookup"><span data-stu-id="5e59c-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="5e59c-132">uint</span><span class="sxs-lookup"><span data-stu-id="5e59c-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="5e59c-133">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-133">0</span></span>|
|[<span data-ttu-id="5e59c-134">ulong</span><span class="sxs-lookup"><span data-stu-id="5e59c-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="5e59c-135">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-135">0</span></span>|
|[<span data-ttu-id="5e59c-136">ushort</span><span class="sxs-lookup"><span data-stu-id="5e59c-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="5e59c-137">0</span><span class="sxs-lookup"><span data-stu-id="5e59c-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="5e59c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e59c-138">See also</span></span>
 <span data-ttu-id="5e59c-139">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5e59c-139">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5e59c-140">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5e59c-140">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5e59c-141">[値型の一覧表](../../../csharp/language-reference/keywords/value-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="5e59c-141">[Value Types Table](../../../csharp/language-reference/keywords/value-types-table.md) </span></span>  
 <span data-ttu-id="5e59c-142">[値型](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="5e59c-142">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="5e59c-143">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="5e59c-143">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 [<span data-ttu-id="5e59c-144">型のリファレンス表</span><span class="sxs-lookup"><span data-stu-id="5e59c-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)

