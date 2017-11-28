---
title: "&#39;です。各 &#39; の型 &#39; で&lt;typename&gt;&#39; の複数のインスタンス &#39; 型が実装されているためには、あいまいです'System.collections.generic.ienumerable(of (Of T) &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords: BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a74178f3f0b2e7589b87046973473582993f3ed9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="3cd4d-102">&#39;です。各 &#39; の型 &#39; で&lt;typename&gt;&#39; の複数のインスタンス &#39; 型が実装されているためには、あいまいです'System.collections.generic.ienumerable(of (Of T) &#39;</span><span class="sxs-lookup"><span data-stu-id="3cd4d-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="3cd4d-103">A`For Each`ステートメントで指定されている複数の反復子変数<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3cd4d-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="3cd4d-104">反復子変数を実装する型にする必要があります、<xref:System.Collections.IEnumerable?displayProperty=nameWithType>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>インターフェイスのいずれかで、`Collections`の名前空間、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3cd4d-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="3cd4d-105">それぞれの構築に別の型引数を使用して、構築された 1 つ以上のジェネリック インターフェイスを実装するクラスのことができます。</span><span class="sxs-lookup"><span data-stu-id="3cd4d-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="3cd4d-106">これを行うクラスは、反復子変数、その変数が 1 つ以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3cd4d-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="3cd4d-107">このような場合は、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を呼び出す方法を選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="3cd4d-107">In such a case, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="3cd4d-108">**エラー ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="3cd4d-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3cd4d-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3cd4d-109">To correct this error</span></span>  
  
-   <span data-ttu-id="3cd4d-110">使用して[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)反復子変数型を定義するインターフェイスにキャストする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3cd4d-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd4d-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cd4d-111">See Also</span></span>  
 [<span data-ttu-id="3cd4d-112">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="3cd4d-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="3cd4d-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cd4d-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
