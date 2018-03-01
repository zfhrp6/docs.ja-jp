---
title: "反復子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd6c0b1fa422dc4ab659d8c59472e5c098c729bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="34fbe-102">反復子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34fbe-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="34fbe-103">指定する関数または`Get`アクセサーが反復子。</span><span class="sxs-lookup"><span data-stu-id="34fbe-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34fbe-104">コメント</span><span class="sxs-lookup"><span data-stu-id="34fbe-104">Remarks</span></span>  
 <span data-ttu-id="34fbe-105">*反復子*コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="34fbe-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="34fbe-106">反復子を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)を一度に 1 つ、コレクション内の各要素を返すステートメントです。</span><span class="sxs-lookup"><span data-stu-id="34fbe-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="34fbe-107">ときに、`Yield`ステートメントに達すると、コードの現在の位置が保持されます。</span><span class="sxs-lookup"><span data-stu-id="34fbe-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="34fbe-108">次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="34fbe-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="34fbe-109">関数、またはとして、反復子を実装することができます、`Get`プロパティ定義のアクセサー。</span><span class="sxs-lookup"><span data-stu-id="34fbe-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="34fbe-110">`Iterator`反復子関数の宣言に修飾子が表示されますか`Get`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="34fbe-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="34fbe-111">使用して、クライアント コードから反復子を呼び出す、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="34fbe-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="34fbe-112">反復子関数の戻り値の型または`Get`アクセサーを指定することができます<xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>です。</span><span class="sxs-lookup"><span data-stu-id="34fbe-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="34fbe-113">反復子には指定できません`ByRef`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="34fbe-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="34fbe-114">反復子を、イベント、インスタンス コンストラクター、静的コンストラクター、静的デストラクターで指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="34fbe-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="34fbe-115">反復子は、匿名の関数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="34fbe-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="34fbe-116">詳細については、「 [反復子](../../programming-guide/concepts/iterators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34fbe-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="34fbe-117">使用法</span><span class="sxs-lookup"><span data-stu-id="34fbe-117">Usage</span></span>  
 <span data-ttu-id="34fbe-118">`Iterator` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="34fbe-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="34fbe-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="34fbe-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="34fbe-120">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="34fbe-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="34fbe-121">例</span><span class="sxs-lookup"><span data-stu-id="34fbe-121">Example</span></span>  
 <span data-ttu-id="34fbe-122">次の例では、iterator 関数を示します。</span><span class="sxs-lookup"><span data-stu-id="34fbe-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="34fbe-123">Iterator 関数が、`Yield`内にあるステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。</span><span class="sxs-lookup"><span data-stu-id="34fbe-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="34fbe-124">各反復処理、[各](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント本体で`Main`への呼び出しを作成、 `Power` iterator 関数。</span><span class="sxs-lookup"><span data-stu-id="34fbe-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="34fbe-125">Iterator 関数を呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の反復処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="34fbe-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="34fbe-126">例</span><span class="sxs-lookup"><span data-stu-id="34fbe-126">Example</span></span>  
 <span data-ttu-id="34fbe-127">次の例は、反復子である `Get` アクセサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="34fbe-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="34fbe-128">`Iterator`プロパティ宣言では、修飾子です。</span><span class="sxs-lookup"><span data-stu-id="34fbe-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="34fbe-129">その他の例では、次を参照してください。[反復子](../../programming-guide/concepts/iterators.md)です。</span><span class="sxs-lookup"><span data-stu-id="34fbe-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fbe-130">参照</span><span class="sxs-lookup"><span data-stu-id="34fbe-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="34fbe-131">反復子</span><span class="sxs-lookup"><span data-stu-id="34fbe-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)  
 [<span data-ttu-id="34fbe-132">Yield ステートメント</span><span class="sxs-lookup"><span data-stu-id="34fbe-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
