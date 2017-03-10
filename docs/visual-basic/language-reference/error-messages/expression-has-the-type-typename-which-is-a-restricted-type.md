---
title: "Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc31393"
  - "vbc31393"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31393"
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

式の評価結果が、共通言語ランタイム \(CLR\) でボックス化できない型になりますが、式はボックス化を要求するメンバーにアクセスします。  
  
 *ボックス化*とは、型を `Object` \(場合によっては <xref:System.ValueType>\) に変換するために不可欠な処理です。  共通言語ランタイムは、<xref:System.ArgIterator>、<xref:System.RuntimeArgumentHandle>、および <xref:System.TypedReference> など一部の構造体型をボックス化できません。  
  
 この式は、制限された型を使用して、<xref:System.Object.GetHashCode%2A> や <xref:System.Object.ToString%2A> などの、<xref:System.Object> または <xref:System.ValueType> から継承されたメソッドを呼び出そうとします。  このメソッドにアクセスするために、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] が暗黙のボックス化変換を実行しようとすることにより、このエラーが発生します。  
  
 **Error ID:** BC31393  
  
### このエラーを解決するには  
  
1.  問題の型に評価される式を探します。  
  
2.  ステートメントのどの部分が、<xref:System.Object> または <xref:System.ValueType> から継承されるメソッドを呼び出そうとするかを調べます。  
  
3.  ステートメントを書き直して、メソッド呼び出しが行われないようにします。  
  
## 参照  
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)