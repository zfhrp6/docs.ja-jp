---
title: "Null 許容型 (C# プログラミング ガイド)"
ms.date: 2017-05-15
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
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
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 56e22638457017688ff380f6683b463b47c53a17
ms.contentlocale: ja-jp
ms.lasthandoff: 09/02/2017

---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="da18e-102">Null 許容型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="da18e-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="da18e-103">Null 許容型は、<xref:System.Nullable%601?displayProperty=fullName> 構造体のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="da18e-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=fullName> struct.</span></span> <span data-ttu-id="da18e-104">Null 許容型は、基になる値型の適切な範囲の値だけでなく、`null` 値も表すことができます。</span><span class="sxs-lookup"><span data-stu-id="da18e-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="da18e-105">たとえば、`Nullable<Int32>` ("Null 許容の Int32" と読みます) には、-2147483648 ～ 2147483647 の範囲の任意の値または `null` 値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="da18e-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="da18e-106">`Nullable<bool>` には、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、または [null](../../../csharp/language-reference/keywords/null.md) の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="da18e-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="da18e-107">数値型と Boolean 型に `null` を割り当てる機能は、値が割り当てられていない可能性がある要素を含むデータベースとその他のデータ型を処理するときに特に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="da18e-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="da18e-108">たとえば、データベースの Boolean フィールドには、値 `true` または `false` が格納されている可能性がありますが、未定義である可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="da18e-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
<span data-ttu-id="da18e-109">[!code-cs[null 許容型](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]</span><span class="sxs-lookup"><span data-stu-id="da18e-109">[!code-cs[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]</span></span>  
  
<span data-ttu-id="da18e-110">その他の例については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="da18e-110">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="da18e-111">Null 許容型の概要</span><span class="sxs-lookup"><span data-stu-id="da18e-111">Nullable Types Overview</span></span>  
 <span data-ttu-id="da18e-112">Null 許容型には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="da18e-112">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="da18e-113">Null 許容型は、`null`値を割り当てることができる、値型の変数を表します。</span><span class="sxs-lookup"><span data-stu-id="da18e-113">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="da18e-114">参照型に基づいた Null 許容型は作成できません </span><span class="sxs-lookup"><span data-stu-id="da18e-114">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="da18e-115">(参照型は既に `null` 値をサポートしています)。</span><span class="sxs-lookup"><span data-stu-id="da18e-115">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="da18e-116">構文 `T?` は、<xref:System.Nullable%601> の省略表現です。ここで、`T` は値型です。</span><span class="sxs-lookup"><span data-stu-id="da18e-116">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="da18e-117">この 2 つの形式は同義であり、どちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="da18e-117">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="da18e-118">Null 許容型に値を割り当てる方法は、通常の値型の場合と同じです。たとえば、`int? x = 10;` や `double? d = 4.108` と指定します。</span><span class="sxs-lookup"><span data-stu-id="da18e-118">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108`.</span></span> <span data-ttu-id="da18e-119">Null 許容型には、値 `null` も割り当てることができます。たとえば、`int? x = null.` と指定します。</span><span class="sxs-lookup"><span data-stu-id="da18e-119">A nullable type can also be assigned the value `null`: `int? x = null.`</span></span>  
  
-   <span data-ttu-id="da18e-120">割り当てられた値、または値が `null` の場合に基になる型の既定値を返すには、<xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> メソッドを使用します。たとえば、`int j = x.GetValueOrDefault();` と指定します。</span><span class="sxs-lookup"><span data-stu-id="da18e-120">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="da18e-121">null かどうかを確認して値を取得するには、<xref:System.Nullable%601.HasValue%2A> と <xref:System.Nullable%601.Value%2A> の読み取り専用プロパティを使用します。たとえば、`if(x.HasValue) j = x.Value;` と指定します。</span><span class="sxs-lookup"><span data-stu-id="da18e-121">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="da18e-122">`HasValue` プロパティは、変数に値が含まれる場合は `true` を返し、`null` の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="da18e-122">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="da18e-123">`Value` プロパティは、値が割り当てられていれば、その値を返します。</span><span class="sxs-lookup"><span data-stu-id="da18e-123">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="da18e-124">それ以外の場合は、<xref:System.InvalidOperationException?displayProperty=fullName> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="da18e-124">Otherwise, a <xref:System.InvalidOperationException?displayProperty=fullName> is thrown.</span></span>  
  
    -   <span data-ttu-id="da18e-125">`HasValue` の既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="da18e-125">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="da18e-126">`Value`プロパティには既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="da18e-126">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="da18e-127">Null 許容型では `==` 演算子と `!=` 演算子も使用できます。たとえば、`if (x != null) y = x;` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="da18e-127">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="da18e-128">現在の値が `null` である Null 許容型が Null 許容型以外の型に割り当てられるときに適用される既定値を割り当てるには、`??` 演算子を使用します。たとえば、`int? x = null; int y = x ?? -1;` と指定します。</span><span class="sxs-lookup"><span data-stu-id="da18e-128">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="da18e-129">入れ子になった Null 許容型は許可されません。</span><span class="sxs-lookup"><span data-stu-id="da18e-129">Nested nullable types are not allowed.</span></span> <span data-ttu-id="da18e-130">次の行はコンパイルされません。`Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="da18e-130">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da18e-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="da18e-131">Related Sections</span></span>  
 <span data-ttu-id="da18e-132">詳細情報</span><span class="sxs-lookup"><span data-stu-id="da18e-132">For more information:</span></span>  
  
-   [<span data-ttu-id="da18e-133">Null 許容型の使用</span><span class="sxs-lookup"><span data-stu-id="da18e-133">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="da18e-134">Null 許容型のボックス化</span><span class="sxs-lookup"><span data-stu-id="da18e-134">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="da18e-135">??演算子</span><span class="sxs-lookup"><span data-stu-id="da18e-135">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="da18e-136">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="da18e-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da18e-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="da18e-137">See Also</span></span>  
 <span data-ttu-id="da18e-138"><xref:System.Nullable></span><span class="sxs-lookup"><span data-stu-id="da18e-138"><xref:System.Nullable></span></span>   
 <span data-ttu-id="da18e-139">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="da18e-139">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="da18e-140">[C#](../../../csharp/index.md) </span><span class="sxs-lookup"><span data-stu-id="da18e-140">[C#](../../../csharp/index.md) </span></span>  
 <span data-ttu-id="da18e-141">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="da18e-141">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="da18e-142">What Exactly Does 'Lifted' mean? ('Lifted' の正確な意味)</span><span class="sxs-lookup"><span data-stu-id="da18e-142">What exactly does 'lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112382)

