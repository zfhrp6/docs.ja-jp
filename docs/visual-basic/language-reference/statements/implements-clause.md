---
title: "Implements Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ImplementsClause"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interface implementation, reimplementation"
  - "interface members, reimplementation"
  - "interface members, Implements keyword"
  - "interface members"
  - "members, reimplementation"
  - "interface implementation, Implements keyword"
  - "interface members, implementing"
  - "Implements keyword"
  - "Implements statement, about Implements"
  - "members, implementing"
  - "members, Implements keyword"
  - "reimplementation"
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Implements Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスまたは構造体のメンバーが、インターフェイスで定義されているメンバーを実装することを示すキーワードです。  
  
## 解説  
 `Implements` キーワードは、[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md) とは異なります。  `Implements` ステートメントは、クラスまたは構造体が 1 つ以上のインターフェイスを実装することを指定するために使用します。そして、各メンバーがどのインターフェイスのどのメンバーを実装しているかを、`Implements` キーワードを使って指定します。  
  
 クラスまたは構造体がインターフェイスを実装する場合は、[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) または [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) の直後に `Implements` ステートメントを記述し、インターフェイスで定義されているすべてのメンバーを実装する必要があります。  
  
## 再実装  
 派生クラスでは、基本クラスで既に実装されているインターフェイスのメンバーを再実装できます。  これは次の点で基本クラスのメンバーのオーバーライドとは異なります。  
  
-   基本クラスのメンバーは、再実装するために [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) する必要がありません。  
  
-   メンバーを別の名前で再実装できます。  
  
 キーワード `Implements` は、次の構文で使用します。  
  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)