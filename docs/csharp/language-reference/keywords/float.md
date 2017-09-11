---
title: "float (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2f1fb02f84de504112eee826dbee1275fa3ccb7a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="float-c-reference"></a><span data-ttu-id="0bc6f-102">float (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0bc6f-102">float (C# Reference)</span></span>
<span data-ttu-id="0bc6f-103">`float` キーワードは、32 ビット浮動小数点値を格納する単純な型を示します。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="0bc6f-104">次の表では、`float` 型の有効桁数とおおよその範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="0bc6f-105">型</span><span class="sxs-lookup"><span data-stu-id="0bc6f-105">Type</span></span>|<span data-ttu-id="0bc6f-106">おおよその範囲</span><span class="sxs-lookup"><span data-stu-id="0bc6f-106">Approximate range</span></span>|<span data-ttu-id="0bc6f-107">有効桁数</span><span class="sxs-lookup"><span data-stu-id="0bc6f-107">Precision</span></span>|<span data-ttu-id="0bc6f-108">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="0bc6f-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="0bc6f-109">-3.4 × 10<sup>38</sup> から +3.4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="0bc6f-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="0bc6f-110">7 桁</span><span class="sxs-lookup"><span data-stu-id="0bc6f-110">7 digits</span></span>|<xref:System.Single?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="0bc6f-111">リテラル</span><span class="sxs-lookup"><span data-stu-id="0bc6f-111">Literals</span></span>  
 <span data-ttu-id="0bc6f-112">既定では、代入演算子の右辺にある実数値リテラルは、[double](double.md) として扱われます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="0bc6f-113">したがって、float 変数を初期化するには、次の例のように、サフィックス `f` または `F` を使います。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="0bc6f-114">前の宣言でサフィックスを使わないと、[double](double.md) 値を `float` 変数に保存しようとするため、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="0bc6f-115">変換</span><span class="sxs-lookup"><span data-stu-id="0bc6f-115">Conversions</span></span>  
 <span data-ttu-id="0bc6f-116">整数型と浮動小数点型を 1 つの式の中の混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="0bc6f-117">この場合、整数型が浮動小数点型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="0bc6f-118">式の評価は、次の規則に従って実行されます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="0bc6f-119">浮動小数点型の 1 つが [double](double.md) の場合、式は [double](double.md) または [bool](bool.md) (関係式またはブール式の場合) と評価されます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="0bc6f-120">式に [double](double.md) 型が含まれない場合は、式は `float` または [bool](bool.md) (関係式またはブール式の場合) と評価されます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="0bc6f-121">浮動小数点式は、次の値のセットを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="0bc6f-122">正および負のゼロ</span><span class="sxs-lookup"><span data-stu-id="0bc6f-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="0bc6f-123">正および負の無限大</span><span class="sxs-lookup"><span data-stu-id="0bc6f-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="0bc6f-124">Not-a-Number (NaN) 値</span><span class="sxs-lookup"><span data-stu-id="0bc6f-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="0bc6f-125">ゼロ以外の値の有限のセット</span><span class="sxs-lookup"><span data-stu-id="0bc6f-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="0bc6f-126">これらの値について詳しくは、[IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) の Web サイトで入手できるバイナリ浮動小数点演算の IEEE 標準に関する資料をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc6f-127">例</span><span class="sxs-lookup"><span data-stu-id="0bc6f-127">Example</span></span>  
 <span data-ttu-id="0bc6f-128">次の例では、[int](int.md)、[short](short.md)、`float` が算術式に含まれ、`float` の結果を提供します。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="0bc6f-129">(`float` は <xref:System.Single?displayProperty=fullName> 型のエイリアスです。)式には [double](double.md) が存在しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0bc6f-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=fullName> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 <span data-ttu-id="0bc6f-130">[!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bc6f-130">[!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0bc6f-131">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0bc6f-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0bc6f-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bc6f-132">See Also</span></span>  
 <span data-ttu-id="0bc6f-133"><xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="0bc6f-133"><xref:System.Single></span></span>   
 <span data-ttu-id="0bc6f-134">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0bc6f-135">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0bc6f-136">[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-136">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 <span data-ttu-id="0bc6f-137">[C# のキーワード](index.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-137">[C# Keywords](index.md) </span></span>  
 <span data-ttu-id="0bc6f-138">[整数型の一覧表](integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-138">[Integral Types Table](integral-types-table.md) </span></span>  
 <span data-ttu-id="0bc6f-139">[組み込み型の一覧表](built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-139">[Built-In Types Table](built-in-types-table.md) </span></span>  
 <span data-ttu-id="0bc6f-140">[暗黙的な数値変換の一覧表](implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="0bc6f-140">[Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="0bc6f-141">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="0bc6f-141">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)

