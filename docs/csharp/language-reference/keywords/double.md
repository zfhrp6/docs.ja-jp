---
title: double (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: e2524c907781bd3ce618acb0bdd087acb4b10f75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="double-c-reference"></a><span data-ttu-id="596b6-102">double (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="596b6-102">double (C# Reference)</span></span>
<span data-ttu-id="596b6-103">`double` キーワードは、64 ビット浮動小数点値を格納する単純な型を示します。</span><span class="sxs-lookup"><span data-stu-id="596b6-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="596b6-104">次の表では、`double` 型の有効桁数とおおよその範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="596b6-104">The following table shows the precision and approximate range for the `double` type.</span></span>  
  
|<span data-ttu-id="596b6-105">型</span><span class="sxs-lookup"><span data-stu-id="596b6-105">Type</span></span>|<span data-ttu-id="596b6-106">おおよその範囲</span><span class="sxs-lookup"><span data-stu-id="596b6-106">Approximate range</span></span>|<span data-ttu-id="596b6-107">有効桁数</span><span class="sxs-lookup"><span data-stu-id="596b6-107">Precision</span></span>|<span data-ttu-id="596b6-108">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="596b6-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|<span data-ttu-id="596b6-109">±5.0 × 10<sup>−324</sup> - ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="596b6-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="596b6-110">15-16 桁</span><span class="sxs-lookup"><span data-stu-id="596b6-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="596b6-111">リテラル</span><span class="sxs-lookup"><span data-stu-id="596b6-111">Literals</span></span>  
 <span data-ttu-id="596b6-112">既定では、代入演算子の右辺にある実数値リテラルは `double` として扱われます。</span><span class="sxs-lookup"><span data-stu-id="596b6-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="596b6-113">ただし、整数を `double` として処理する場合、次のようにサフィックスの d または D を使用します。</span><span class="sxs-lookup"><span data-stu-id="596b6-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>  
  
```  
double x = 3D;  
```  
  
## <a name="conversions"></a><span data-ttu-id="596b6-114">変換</span><span class="sxs-lookup"><span data-stu-id="596b6-114">Conversions</span></span>  
 <span data-ttu-id="596b6-115">整数型と浮動小数点型を 1 つの式の中の混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="596b6-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="596b6-116">この場合、整数型が浮動小数点型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="596b6-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="596b6-117">式の評価は、次の規則に従って実行されます。</span><span class="sxs-lookup"><span data-stu-id="596b6-117">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="596b6-118">浮動小数点型の 1 つが `double` の場合、式は `double` または [bool](../../../csharp/language-reference/keywords/bool.md) (関係式またはブール式の場合) と評価されます。</span><span class="sxs-lookup"><span data-stu-id="596b6-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="596b6-119">式に `double` 型が含まれない場合は、[float](../../../csharp/language-reference/keywords/float.md) または [bool](../../../csharp/language-reference/keywords/bool.md) (関係式またはブール式の場合) と評価されます。</span><span class="sxs-lookup"><span data-stu-id="596b6-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="596b6-120">浮動小数点式は、次の値のセットを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="596b6-120">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="596b6-121">正および負のゼロ。</span><span class="sxs-lookup"><span data-stu-id="596b6-121">Positive and negative zero.</span></span>  
  
-   <span data-ttu-id="596b6-122">正および負の無限大。</span><span class="sxs-lookup"><span data-stu-id="596b6-122">Positive and negative infinity.</span></span>  
  
-   <span data-ttu-id="596b6-123">Not-a-Number (NaN) 値。</span><span class="sxs-lookup"><span data-stu-id="596b6-123">Not-a-Number value (NaN).</span></span>  
  
-   <span data-ttu-id="596b6-124">ゼロ以外の値の有限のセット。</span><span class="sxs-lookup"><span data-stu-id="596b6-124">The finite set of nonzero values.</span></span>  
  
 <span data-ttu-id="596b6-125">これらの値について詳しくは、[IEEE](http://www.ieee.org) の Web サイトで入手できるバイナリ浮動小数点演算の IEEE 標準に関する資料をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="596b6-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="596b6-126">例</span><span class="sxs-lookup"><span data-stu-id="596b6-126">Example</span></span>  
 <span data-ttu-id="596b6-127">次の例では、[int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md)、`double` がまとめて追加され、結果として `double` になります。</span><span class="sxs-lookup"><span data-stu-id="596b6-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="596b6-128">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="596b6-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="596b6-129">参照</span><span class="sxs-lookup"><span data-stu-id="596b6-129">See Also</span></span>  
 [<span data-ttu-id="596b6-130">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="596b6-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="596b6-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="596b6-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="596b6-132">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="596b6-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="596b6-133">既定値の一覧表</span><span class="sxs-lookup"><span data-stu-id="596b6-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="596b6-134">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="596b6-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="596b6-135">浮動小数点型の一覧表</span><span class="sxs-lookup"><span data-stu-id="596b6-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [<span data-ttu-id="596b6-136">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="596b6-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="596b6-137">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="596b6-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
