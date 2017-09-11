---
title: "&quot;For Each&quot; 型 &quot;&lt;typename&gt;&quot; が型 &quot;&quot;system.collections.generic.ienumerable(of T)&quot; の複数のインスタンスを実装しているために、あいまい |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
dev_langs:
- VB
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 783c741a8acb0d27ef6ff5c52939bd12a026ba74
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="42967-102">'For Each' 型 '&lt;typename&gt;' が型 ''system.collections.generic.ienumerable(of T)' の複数のインスタンスを実装しているために、あいまい</span><span class="sxs-lookup"><span data-stu-id="42967-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="42967-103">A`For Each`ステートメントを指定する反復子変数を&1; つ以上を持つ<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッド</xref:System.Collections.IEnumerable.GetEnumerator%2A>。</span><span class="sxs-lookup"><span data-stu-id="42967-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="42967-104">反復子変数を実装する型でなければならない、<xref:System.Collections.IEnumerable?displayProperty=fullName>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>インターフェイスのいずれかで、`Collections`の名前空間、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="42967-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="42967-105">それぞれの構築についての別の型引数を使用して、1 つ以上の構築されたジェネリック インターフェイスを実装するクラスのことができます。</span><span class="sxs-lookup"><span data-stu-id="42967-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="42967-106">その変数が&1; つ以上の場合はこれを行うクラスは、反復子変数の使用は、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッド</xref:System.Collections.IEnumerable.GetEnumerator%2A>。</span><span class="sxs-lookup"><span data-stu-id="42967-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="42967-107">このような場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を呼び出す方法を選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="42967-107">In such a case, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="42967-108">**エラー ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="42967-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42967-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="42967-109">To correct this error</span></span>  
  
-   <span data-ttu-id="42967-110">使用して[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)反復子変数型を定義するインターフェイスにキャストする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを使用する</xref:System.Collections.IEnumerable.GetEnumerator%2A>。</span><span class="sxs-lookup"><span data-stu-id="42967-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42967-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="42967-111">See Also</span></span>  
 <span data-ttu-id="42967-112">[各.次のステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="42967-112">[For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="42967-113"> [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="42967-113"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
