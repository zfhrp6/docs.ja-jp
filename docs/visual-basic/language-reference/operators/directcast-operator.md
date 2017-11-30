---
title: "DirectCast 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords: DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="c7d3c-102">DirectCast 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7d3c-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="c7d3c-103">継承または実装に基づいて、型変換操作をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7d3c-104">コメント</span><span class="sxs-lookup"><span data-stu-id="c7d3c-104">Remarks</span></span>  
 <span data-ttu-id="c7d3c-105">`DirectCast`実行時のヘルパー ルーチンに多少を提供するための変換よりもパフォーマンスが向上、Visual Basic を使用しない`CType`データ型に変換するときに`Object`です。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="c7d3c-106">使用する、`DirectCast`キーワードを使用するのと同様、 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)と[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword.</span></span> <span data-ttu-id="c7d3c-107">最初の引数と型に変換するために 2 番目の引数として式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="c7d3c-108">`DirectCast`2 つの引数のデータ型間の継承または実装のリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="c7d3c-109">これは、1 つの型が継承する必要があるかどうか、または、他の実装していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="c7d3c-110">エラーや障害</span><span class="sxs-lookup"><span data-stu-id="c7d3c-110">Errors and Failures</span></span>  
 <span data-ttu-id="c7d3c-111">`DirectCast`継承または実装のリレーションシップが存在しないことが検出された場合は、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="c7d3c-112">コンパイラ エラーがないことに成功した変換が保証されません。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="c7d3c-113">必要な変換は縮小すると、実行時に失敗する可能性がします。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="c7d3c-114">この場合、ランタイムは、スロー、<xref:System.InvalidCastException>エラーです。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="c7d3c-115">変換キーワード</span><span class="sxs-lookup"><span data-stu-id="c7d3c-115">Conversion Keywords</span></span>  
 <span data-ttu-id="c7d3c-116">型変換のキーワードの比較は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="c7d3c-117">キーワード</span><span class="sxs-lookup"><span data-stu-id="c7d3c-117">Keyword</span></span>|<span data-ttu-id="c7d3c-118">データ型</span><span class="sxs-lookup"><span data-stu-id="c7d3c-118">Data types</span></span>|<span data-ttu-id="c7d3c-119">引数の関係</span><span class="sxs-lookup"><span data-stu-id="c7d3c-119">Argument relationship</span></span>|<span data-ttu-id="c7d3c-120">実行時エラー</span><span class="sxs-lookup"><span data-stu-id="c7d3c-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="c7d3c-121">CType 関数</span><span class="sxs-lookup"><span data-stu-id="c7d3c-121">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="c7d3c-122">すべてのデータ型</span><span class="sxs-lookup"><span data-stu-id="c7d3c-122">Any data types</span></span>|<span data-ttu-id="c7d3c-123">2 つのデータ型の間では、拡大または縮小変換を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="c7d3c-124">スローされます。<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="c7d3c-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="c7d3c-125">すべてのデータ型</span><span class="sxs-lookup"><span data-stu-id="c7d3c-125">Any data types</span></span>|<span data-ttu-id="c7d3c-126">1 つの型を継承または、他の型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="c7d3c-127">スローされます。<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="c7d3c-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="c7d3c-128">TryCast 演算子</span><span class="sxs-lookup"><span data-stu-id="c7d3c-128">TryCast Operator</span></span>](../../../visual-basic/language-reference/operators/trycast-operator.md)|<span data-ttu-id="c7d3c-129">参照型のみ</span><span class="sxs-lookup"><span data-stu-id="c7d3c-129">Reference types only</span></span>|<span data-ttu-id="c7d3c-130">1 つの型を継承または、他の型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="c7d3c-131">返します[何も行われません](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="c7d3c-131">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7d3c-132">例</span><span class="sxs-lookup"><span data-stu-id="c7d3c-132">Example</span></span>  
 <span data-ttu-id="c7d3c-133">次の例では、2 つの用途の`DirectCast`、いずれかのいずれかの実行時に失敗することは成功します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 <span data-ttu-id="c7d3c-134">前の例で、実行時の入力の`q`は`Double`します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="c7d3c-135">`CType`成功`Double`に変換できる`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="c7d3c-136">ただし、最初の`DirectCast`、実行時の入力のために、実行時に失敗`Double`継承関係を持たない`Integer`変換が存在する場合でも、します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="c7d3c-137">2 番目`DirectCast`が型から変換が成功した<xref:System.Windows.Forms.Form>入力<xref:System.Windows.Forms.Control>、元となる<xref:System.Windows.Forms.Form>を継承します。</span><span class="sxs-lookup"><span data-stu-id="c7d3c-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d3c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7d3c-138">See Also</span></span>  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c7d3c-139">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="c7d3c-139">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="c7d3c-140">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="c7d3c-140">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
