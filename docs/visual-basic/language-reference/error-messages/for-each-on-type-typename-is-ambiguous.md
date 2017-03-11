---
title: "&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32096"
  - "bc32096"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32096"
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# &#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`For Each` ステートメントが複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを持つ反復子変数を指定しています。  
  
 反復子変数の型は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のいずれかの `Collections` 名前空間の <xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> インターフェイスを実装する型にする必要があります。  1 つのクラスには、複数の構築されたジェネリック インターフェイスが実装されていることがあります。これは、各ジェネリック インターフェイスの構築に異なる型引数を使用することで達成できます。  このようなクラスを反復子変数に使用した場合、この変数は複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを持つことになります。  その場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] はどのメソッドを呼び出せばよいかを判断できません。  
  
 **Error ID:** BC32096  
  
### このエラーを解決するには  
  
-   [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) または [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) を使用して、反復子変数の型を、目的の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを定義しているインターフェイスへとキャストします。  
  
## 参照  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)