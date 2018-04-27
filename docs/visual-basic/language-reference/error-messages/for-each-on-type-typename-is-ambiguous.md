---
title: "&#39;各&#39;型&#39; &lt;typename&gt; &#39;型の複数のインスタンスを実装するためがあいまいです&#39;'system.collections.generic.ienumerable(of T)&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81cb37cc4b61fa96e64f59150d95356b2fb0a355
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;各&#39;型&#39; &lt;typename&gt; &#39;型の複数のインスタンスを実装するためがあいまいです&#39;'system.collections.generic.ienumerable(of T)&#39;
A`For Each`ステートメントで指定されている複数の反復子変数<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドです。  
  
 反復子変数を実装する型にする必要があります、<xref:System.Collections.IEnumerable?displayProperty=nameWithType>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>インターフェイスのいずれかで、`Collections`の名前空間、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。 それぞれの構築に別の型引数を使用して、構築された 1 つ以上のジェネリック インターフェイスを実装するクラスのことができます。 これを行うクラスは、反復子変数、その変数が 1 つ以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドです。 このような場合は、Visual Basic にどのメソッドを呼び出すことはできませんを選択します。  
  
 **エラー ID:** BC32096  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)反復子変数型を定義するインターフェイスにキャストする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを使用します。  
  
## <a name="see-also"></a>関連項目  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
