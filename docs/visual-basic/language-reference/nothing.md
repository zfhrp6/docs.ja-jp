---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6932fee01ec6f39f67fb1a26a9a5b5cbd47d9767
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nothing-visual-basic"></a><span data-ttu-id="4cc13-102">Nothing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cc13-102">Nothing (Visual Basic)</span></span>
<span data-ttu-id="4cc13-103">任意のデータ型の既定値を表します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-103">Represents the default value of any data type.</span></span> <span data-ttu-id="4cc13-104">参照型の場合、既定値は、`null`参照します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-104">For reference types, the default value is the `null` reference.</span></span> <span data-ttu-id="4cc13-105">値型の場合、既定値は値の型が null 値を許容するかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-105">For value types, the default value depends on whether the value type is nullable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cc13-106">Null 非許容値型の場合は、 `Nothing` Visual Basic では異なって`null`(C#)。</span><span class="sxs-lookup"><span data-stu-id="4cc13-106">For non-nullable value types, `Nothing` in Visual Basic differs from `null` in C#.</span></span> <span data-ttu-id="4cc13-107">Visual Basic の場合に null 非許容値型の変数を設定した場合に`Nothing`変数が宣言された型の既定値に設定されています。</span><span class="sxs-lookup"><span data-stu-id="4cc13-107">In Visual Basic, if you set a variable of a non-nullable value type to `Nothing`, the variable is set to the default value for its declared type.</span></span> <span data-ttu-id="4cc13-108">C# の場合、null 非許容値型の変数を割り当てる場合`null`コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-108">In C#, if you assign a variable of a non-nullable value type to `null`, a compile-time error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cc13-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4cc13-109">Remarks</span></span>  
 <span data-ttu-id="4cc13-110">`Nothing`データ型の既定値を表します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-110">`Nothing` represents the default value of a data type.</span></span> <span data-ttu-id="4cc13-111">既定値は、変数が、値の型または参照型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="4cc13-111">The default value depends on whether the variable is of a value type or of a reference type.</span></span>  
  
 <span data-ttu-id="4cc13-112">変数、*値の型*直接その値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4cc13-112">A variable of a *value type* directly contains its value.</span></span> <span data-ttu-id="4cc13-113">値の型は、すべての数値データ型を含める`Boolean`、 `Char`、 `Date`、すべての構造体、およびすべての列挙体です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-113">Value types include all numeric data types, `Boolean`, `Char`, `Date`, all structures, and all enumerations.</span></span> <span data-ttu-id="4cc13-114">変数、*型参照*メモリ内オブジェクトのインスタンスへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-114">A variable of a *reference type* stores a reference to an instance of the object in memory.</span></span> <span data-ttu-id="4cc13-115">参照型には、クラス、配列、デリゲート、および文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4cc13-115">Reference types include classes, arrays, delegates, and strings.</span></span> <span data-ttu-id="4cc13-116">詳細については、「 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4cc13-116">For more information, see [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
 <span data-ttu-id="4cc13-117">変数は、値の場合は入力の動作`Nothing`かどうか、変数が null 許容型のデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="4cc13-117">If a variable is of a value type, the behavior of `Nothing` depends on whether the variable is of a nullable data type.</span></span> <span data-ttu-id="4cc13-118">Null 許容値型を表す、追加、`?`型名を修飾子です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-118">To represent a nullable value type, add a `?` modifier to the type name.</span></span> <span data-ttu-id="4cc13-119">割り当てる`Nothing`null 許容変数に値を設定`null`です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-119">Assigning `Nothing` to a nullable variable sets the value to `null`.</span></span> <span data-ttu-id="4cc13-120">詳細と例については、次を参照してください。 [null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-120">For more information and examples, see [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>  
  
 <span data-ttu-id="4cc13-121">変数が null 許容ではない値型である場合、割り当てる`Nothing`ことのセットには、既定値に、宣言された型。</span><span class="sxs-lookup"><span data-stu-id="4cc13-121">If a variable is of a value type that is not nullable, assigning `Nothing` to it sets it to the default value for its declared type.</span></span> <span data-ttu-id="4cc13-122">その型の変数のメンバーが含まれている場合はすべて、既定値に設定します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-122">If that type contains variable members, they are all set to their default values.</span></span> <span data-ttu-id="4cc13-123">次の例は、スカラー型の場合、これを示しています。</span><span class="sxs-lookup"><span data-stu-id="4cc13-123">The following example illustrates this for scalar types.</span></span>  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 <span data-ttu-id="4cc13-124">変数が参照型である場合、割り当てる`Nothing`変数設定、`null`変数の型の参照。</span><span class="sxs-lookup"><span data-stu-id="4cc13-124">If a variable is of a reference type, assigning `Nothing` to the variable sets it to a `null` reference of the variable's type.</span></span> <span data-ttu-id="4cc13-125">設定されている変数、`null`参照に関連付けられていない任意のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4cc13-125">A variable that is set to a `null` reference is not associated with any object.</span></span> <span data-ttu-id="4cc13-126">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-126">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 <span data-ttu-id="4cc13-127">変数は参照 (または null 許容の値を入力) するかどうかをチェックするときに`null`、使用しない`= Nothing`または`<> Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-127">When checking whether a reference (or nullable value type) variable is `null`, do not use `= Nothing` or `<> Nothing`.</span></span> <span data-ttu-id="4cc13-128">常に使用する`Is Nothing`または`IsNot Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-128">Always use `Is Nothing` or `IsNot Nothing`.</span></span>  
  
 <span data-ttu-id="4cc13-129">Visual Basic における文字列、空の文字列と同じ`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-129">For strings in Visual Basic, the empty string equals `Nothing`.</span></span> <span data-ttu-id="4cc13-130">したがって、`"" = Nothing`は true です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-130">Therefore, `"" = Nothing` is true.</span></span>  
  
 <span data-ttu-id="4cc13-131">次の例を使用する比較を示しています、`Is`と`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="4cc13-131">The following example shows comparisons that use the `Is` and `IsNot` operators.</span></span>  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 <span data-ttu-id="4cc13-132">使用せずに変数を宣言する場合、`As`句には、設定と`Nothing`、変数の型を持つ`Object`します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-132">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="4cc13-133">この例は、`Dim something = Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="4cc13-133">An example of this is `Dim something = Nothing`.</span></span> <span data-ttu-id="4cc13-134">ここでは、コンパイル時エラーが発生したときに`Option Strict`上と`Option Infer`は無効になってです。</span><span class="sxs-lookup"><span data-stu-id="4cc13-134">A compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is off.</span></span>  
  
 <span data-ttu-id="4cc13-135">割り当てると`Nothing`を object 変数にその参照しなく任意のオブジェクト インスタンスにします。</span><span class="sxs-lookup"><span data-stu-id="4cc13-135">When you assign `Nothing` to an object variable, it no longer refers to any object instance.</span></span> <span data-ttu-id="4cc13-136">場合は、変数インスタンスを参照していたに設定すると`Nothing`インスタンス自体は終了しません。</span><span class="sxs-lookup"><span data-stu-id="4cc13-136">If the variable had previously referred to an instance, setting it to `Nothing` does not terminate the instance itself.</span></span> <span data-ttu-id="4cc13-137">インスタンスが終了し、ガベージ コレクター (GC) では、アクティブな参照が残ってがないことが検出された後にのみ関連付けられているメモリとシステム リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="4cc13-137">The instance is terminated, and the memory and system resources associated with it are released, only after the garbage collector (GC) detects that there are no active references remaining.</span></span>  
  
 <span data-ttu-id="4cc13-138">`Nothing`異なります、<xref:System.DBNull>初期化されていないバリアントまたは存在しないデータベース列を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4cc13-138">`Nothing` differs from the <xref:System.DBNull> object, which represents an uninitialized variant or a nonexistent database column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc13-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cc13-139">See Also</span></span>  
 [<span data-ttu-id="4cc13-140">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="4cc13-140">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="4cc13-141">オブジェクトの有効期間 : オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="4cc13-141">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="4cc13-142">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="4cc13-142">Lifetime in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="4cc13-143">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="4cc13-143">Is Operator</span></span>](../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="4cc13-144">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="4cc13-144">IsNot Operator</span></span>](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="4cc13-145">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="4cc13-145">Nullable Value Types</span></span>](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
