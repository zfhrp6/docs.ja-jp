---
title: Null 許容型 (C# プログラミング ガイド)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: fcff492f420a60a41b373bf9042ed0c2d66d0446
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34456589"
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="0391e-102">Null 許容型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0391e-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="0391e-103">Null 許容型は、<xref:System.Nullable%601?displayProperty=nameWithType> 構造体のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="0391e-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="0391e-104">Null 許容型は、基になる値型の適切な範囲の値だけでなく、`null` 値も表すことができます。</span><span class="sxs-lookup"><span data-stu-id="0391e-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="0391e-105">たとえば、`Nullable<Int32>` ("Null 許容の Int32" と読みます) には、-2147483648 ～ 2147483647 の範囲の任意の値または `null` 値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="0391e-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="0391e-106">`Nullable<bool>` には、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、または [null](../../../csharp/language-reference/keywords/null.md) の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="0391e-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="0391e-107">数値型と Boolean 型に `null` を割り当てる機能は、値が割り当てられていない可能性がある要素を含むデータベースとその他のデータ型を処理するときに特に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="0391e-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="0391e-108">たとえば、データベースの Boolean フィールドには、値 `true` または `false` が格納されている可能性がありますが、未定義である可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="0391e-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
<span data-ttu-id="0391e-109">その他の例については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="0391e-109">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="0391e-110">Null 許容型の概要</span><span class="sxs-lookup"><span data-stu-id="0391e-110">Nullable Types Overview</span></span>  
 <span data-ttu-id="0391e-111">Null 許容型には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="0391e-111">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="0391e-112">Null 許容型は、`null`値を割り当てることができる、値型の変数を表します。</span><span class="sxs-lookup"><span data-stu-id="0391e-112">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="0391e-113">参照型に基づいた Null 許容型は作成できません </span><span class="sxs-lookup"><span data-stu-id="0391e-113">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="0391e-114">(参照型は既に `null` 値をサポートしています)。</span><span class="sxs-lookup"><span data-stu-id="0391e-114">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="0391e-115">構文 `T?` は、<xref:System.Nullable%601> の省略表現です。ここで、`T` は値型です。</span><span class="sxs-lookup"><span data-stu-id="0391e-115">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="0391e-116">この 2 つの形式は同義であり、どちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="0391e-116">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="0391e-117">Null 許容型に値を割り当てる方法は、通常の値型の場合と同じです。たとえば、`int? x = 10;` や `double? d = 4.108` と指定します。</span><span class="sxs-lookup"><span data-stu-id="0391e-117">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="0391e-118">Null 許容型には、値 `null` も割り当てることができます。たとえば、`int? x = null.` と指定します。</span><span class="sxs-lookup"><span data-stu-id="0391e-118">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="0391e-119">割り当てられた値、または値が `null` の場合に基になる型の既定値を返すには、<xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> メソッドを使用します。たとえば、`int j = x.GetValueOrDefault();` と指定します。</span><span class="sxs-lookup"><span data-stu-id="0391e-119">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="0391e-120">null かどうかを確認して値を取得するには、<xref:System.Nullable%601.HasValue%2A> と <xref:System.Nullable%601.Value%2A> の読み取り専用プロパティを使用します。たとえば、`if(x.HasValue) j = x.Value;` と指定します。</span><span class="sxs-lookup"><span data-stu-id="0391e-120">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="0391e-121">`HasValue` プロパティは、変数に値が含まれる場合は `true` を返し、`null` の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="0391e-121">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="0391e-122">`Value` プロパティは、値が割り当てられていれば、その値を返します。</span><span class="sxs-lookup"><span data-stu-id="0391e-122">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="0391e-123">それ以外の場合は、<xref:System.InvalidOperationException?displayProperty=nameWithType> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0391e-123">Otherwise, a <xref:System.InvalidOperationException?displayProperty=nameWithType> is thrown.</span></span>  
  
    -   <span data-ttu-id="0391e-124">`HasValue` の既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="0391e-124">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="0391e-125">`Value`プロパティには既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="0391e-125">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="0391e-126">Null 許容型では `==` 演算子と `!=` 演算子も使用できます。たとえば、`if (x != null) y = x;` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="0391e-126">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="0391e-127">現在の値が `null` である Null 許容型が Null 許容型以外の型に割り当てられるときに適用される既定値を割り当てるには、`??` 演算子を使用します。たとえば、`int? x = null; int y = x ?? -1;` と指定します。</span><span class="sxs-lookup"><span data-stu-id="0391e-127">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="0391e-128">入れ子になった Null 許容型は許可されません。</span><span class="sxs-lookup"><span data-stu-id="0391e-128">Nested nullable types are not allowed.</span></span> <span data-ttu-id="0391e-129">次の行はコンパイルされません。`Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="0391e-129">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0391e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0391e-130">Related Sections</span></span>  
 <span data-ttu-id="0391e-131">詳細情報</span><span class="sxs-lookup"><span data-stu-id="0391e-131">For more information:</span></span>  
  
-   [<span data-ttu-id="0391e-132">Null 許容型の使用</span><span class="sxs-lookup"><span data-stu-id="0391e-132">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="0391e-133">Null 許容型のボックス化</span><span class="sxs-lookup"><span data-stu-id="0391e-133">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="0391e-134">??演算子</span><span class="sxs-lookup"><span data-stu-id="0391e-134">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="0391e-135">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0391e-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0391e-136">参照</span><span class="sxs-lookup"><span data-stu-id="0391e-136">See Also</span></span>  
 <xref:System.Nullable>  
 [<span data-ttu-id="0391e-137">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0391e-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0391e-138">C#</span><span class="sxs-lookup"><span data-stu-id="0391e-138">C#</span></span>](../../../csharp/index.md)  
 [<span data-ttu-id="0391e-139">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="0391e-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0391e-140">What Exactly Does 'Lifted' mean? ('Lifted' の正確な意味)</span><span class="sxs-lookup"><span data-stu-id="0391e-140">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
