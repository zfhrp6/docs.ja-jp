---
title: "&#39;です。各 &#39; の型 &#39; で&lt;typename&gt;&#39; の複数のインスタンス &#39; 型が実装されているためには、あいまいです'System.collections.generic.ienumerable(of (Of T) &#39;"
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
ms.openlocfilehash: a74178f3f0b2e7589b87046973473582993f3ed9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;です。各 &#39; の型 &#39; で&lt;typename&gt;&#39; の複数のインスタンス &#39; 型が実装されているためには、あいまいです'System.collections.generic.ienumerable(of (Of T) &#39;
A`For Each`ステートメントで指定されている複数の反復子変数<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドです。  
  
 反復子変数を実装する型にする必要があります、<xref:System.Collections.IEnumerable?displayProperty=nameWithType>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>インターフェイスのいずれかで、`Collections`の名前空間、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。 それぞれの構築に別の型引数を使用して、構築された 1 つ以上のジェネリック インターフェイスを実装するクラスのことができます。 これを行うクラスは、反復子変数、その変数が 1 つ以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドです。 このような場合は、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を呼び出す方法を選択することはできません。  
  
 **エラー ID:** BC32096  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)反復子変数型を定義するインターフェイスにキャストする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを使用します。  
  
## <a name="see-also"></a>関連項目  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
