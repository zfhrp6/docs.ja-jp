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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6177b48cdc3bc4085cecb6d73c164684ef1c0bc6
ms.lasthandoff: 03/13/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>'For Each' 型 '&lt;typename&gt;' が型 ''system.collections.generic.ienumerable(of T)' の複数のインスタンスを実装しているために、あいまい
A`For Each`ステートメントを指定する反復子変数を&1; つ以上を持つ<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッド</xref:System.Collections.IEnumerable.GetEnumerator%2A>。  
  
 反復子変数を実装する型でなければならない、<xref:System.Collections.IEnumerable?displayProperty=fullName>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>インターフェイスのいずれかで、`Collections`の名前空間、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName> 。 それぞれの構築についての別の型引数を使用して、1 つ以上の構築されたジェネリック インターフェイスを実装するクラスのことができます。 その変数が&1; つ以上の場合はこれを行うクラスは、反復子変数の使用は、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッド</xref:System.Collections.IEnumerable.GetEnumerator%2A>。 このような場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を呼び出す方法を選択することはできません。  
  
 **エラー ID:** BC32096  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)反復子変数型を定義するインターフェイスにキャストする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを使用する</xref:System.Collections.IEnumerable.GetEnumerator%2A>。  
  
## <a name="see-also"></a>関連項目  
 [各.次のステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
