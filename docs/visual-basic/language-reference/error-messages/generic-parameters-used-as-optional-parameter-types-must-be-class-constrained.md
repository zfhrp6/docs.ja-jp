---
title: "Generic parameters used as optional parameter types must be class constrained | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32124"
  - "bc32124"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32124"
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Generic parameters used as optional parameter types must be class constrained
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型パラメーターを使用する省略可能なパラメーターを定義してプロシージャが宣言されましたが、この型パラメーターが参照型に制限されていません。  
  
 各省略可能なパラメーターには、必ず既定値を指定する必要があります。  パラメーターが参照型の場合、オプションの既定値は必ず `Nothing` になります。この値はすべての参照型において有効です。  しかし、パラメーターが値型である場合、その型は Visual Basic で定義済みの基本データ型であることが必要です。  この理由は、ユーザー定義の構造体などの複合値型に有効な既定値がないためです。  
  
 省略可能なパラメーターに型パラメーターを使用する場合は、有効な既定値を持たない値型が使用されるのを防ぐために、型パラメーターを必ず参照型にする必要があります。  つまり、型パラメーターを `Class` キーワードまたは特定のクラスの名前を使って制限する必要があります。  
  
 **Error ID:** BC32124  
  
### このエラーを解決するには  
  
-   参照型だけを受け取るように型パラメーターを制限するか、省略可能なパラメーターに型パラメーターを使わないようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)