---
title: "CType 関数 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="367f6-102">CType 関数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367f6-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="367f6-103">任意の式を、指定されたデータ型、オブジェクト、構造体、クラス、またはインターフェイスに明示的に変換し、その結果を返します。</span><span class="sxs-lookup"><span data-stu-id="367f6-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="367f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="367f6-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="367f6-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="367f6-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="367f6-106">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="367f6-106">Any valid expression.</span></span> <span data-ttu-id="367f6-107">`expression` の値が `typename` で許可されている範囲内でない場合、Visual Basic が例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="367f6-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="367f6-108">`As` ステートメントの `Dim` 句で有効な任意の式。つまり、任意のデータ型、オブジェクト、構造体、クラス、またはインターフェイスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="367f6-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="367f6-109">コメント</span><span class="sxs-lookup"><span data-stu-id="367f6-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="367f6-110">次の関数を使用して型変換を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="367f6-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="367f6-111">特定のデータ型への変換を実行する、`CByte`、`CDbl`、`CInt` などの型変換関数。</span><span class="sxs-lookup"><span data-stu-id="367f6-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="367f6-112">詳細については、次を参照してください。[型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="367f6-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="367f6-113">[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="367f6-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="367f6-114">これらの演算子では、一方の型が他方の型を継承または実装している必要があります。</span><span class="sxs-lookup"><span data-stu-id="367f6-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="367f6-115">これらの場合は、`CType` データ型との間で変換を行うときに、`Object` よりもいくらかパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="367f6-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="367f6-116">`CType` は、インラインでコンパイルされます。つまり、変換コードは、式を評価するコードに含まれます。</span><span class="sxs-lookup"><span data-stu-id="367f6-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="367f6-117">場合によっては、変換を実行するプロシージャが呼び出されないため、コードの実行速度が速くなります。</span><span class="sxs-lookup"><span data-stu-id="367f6-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="367f6-118">`expression` から `typename` など、`Integer` から `Date` への変換が定義されていない場合、Visual Basic はコンパイル時のエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="367f6-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="367f6-119">実行時に変換が失敗すると、適切な例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="367f6-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="367f6-120">縮小変換が失敗した場合、最もよくスローされるのは <xref:System.OverflowException> です。</span><span class="sxs-lookup"><span data-stu-id="367f6-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="367f6-121">変換が定義されていない場合、<xref:System.InvalidCastException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="367f6-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="367f6-122">たとえば、これは、`expression` が `Object` 型で、実行時の型が `typename` への変換を持たない場合に起こります。</span><span class="sxs-lookup"><span data-stu-id="367f6-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="367f6-123">`expression` または `typename` のデータ型が、定義したクラスまたは構造体の場合、そのクラスまたは構造体に `CType` を変換演算子として定義できます。</span><span class="sxs-lookup"><span data-stu-id="367f6-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="367f6-124">これにより、`CType`として機能する*オーバー ロードされた演算子*です。</span><span class="sxs-lookup"><span data-stu-id="367f6-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="367f6-125">この方法を利用する場合、定義したクラスまたは構造体からの変換、またはこのクラスまたは構造体への変換の動作 (スローする例外など) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="367f6-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="367f6-126">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="367f6-126">Overloading</span></span>  
 <span data-ttu-id="367f6-127">`CType` 演算子も、コードの外部で定義されたクラスまたは構造体でオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="367f6-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="367f6-128">このようなクラスまたは構造体からの変換、またはこのクラスまたは構造体への変換を行う場合は、その `CType` 演算子の動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="367f6-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="367f6-129">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="367f6-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="367f6-130">動的オブジェクトの変換</span><span class="sxs-lookup"><span data-stu-id="367f6-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="367f6-131">動的オブジェクトの型変換は、<xref:System.Dynamic.DynamicObject.TryConvert%2A> メソッドまたは <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> メソッドを使用するユーザー定義の動的変換によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="367f6-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="367f6-132">動的オブジェクトを使用する場合は、<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> メソッドを使用して動的オブジェクトを変換します。</span><span class="sxs-lookup"><span data-stu-id="367f6-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="367f6-133">例</span><span class="sxs-lookup"><span data-stu-id="367f6-133">Example</span></span>  
 <span data-ttu-id="367f6-134">`CType` 関数を使用して任意の式を `Single` データ型に変換する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="367f6-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 <span data-ttu-id="367f6-135">その他の例では、次を参照してください。[暗黙的および明示的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)です。</span><span class="sxs-lookup"><span data-stu-id="367f6-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367f6-136">参照</span><span class="sxs-lookup"><span data-stu-id="367f6-136">See Also</span></span>  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="367f6-137">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="367f6-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="367f6-138">変換関数</span><span class="sxs-lookup"><span data-stu-id="367f6-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="367f6-139">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="367f6-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="367f6-140">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="367f6-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="367f6-141">.NET Framework における型変換</span><span class="sxs-lookup"><span data-stu-id="367f6-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
