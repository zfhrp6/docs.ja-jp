---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30149"
  - "bc30149"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30149"
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスまたは構造体はインターフェイスを実装しますが、インターフェイスによって定義されたプロシージャは実装しません。  インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **Error ID:** BC30149  
  
### このエラーを解決するには  
  
1.  インターフェイスで定義された名前とシグネチャを使用して、プロシージャを宣言します。  少なくとも `End Function` ステートメントまたは `End Sub` ステートメントを記述する必要があります。  
  
2.  `Implements` 句を `Function` ステートメントまたは `Sub` ステートメントの末尾に追加します。  次に例を示します。  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## 参照  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)