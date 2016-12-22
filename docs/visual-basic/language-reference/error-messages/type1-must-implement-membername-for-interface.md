---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30154"
  - "bc30154"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30154"
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<typename\>' は、インターフェイス '\<interfacename\>' に対して '\<membername\>' を実装しなければなりません。プロパティの実装では、'ReadOnly' 指定子または 'WriteOnly' 指定子が一致している必要があります。  
  
 クラスまたは構造体はインターフェイスを実装しますが、インターフェイスによって定義されたプロシージャ、プロパティ、またはイベントは実装しません。  インターフェイスのすべてのメンバーを実装する必要があります。  
  
 **Error ID:** BC30154  
  
### このエラーを解決するには  
  
1.  インターフェイスで定義された名前とシグネチャを使用して、メンバーを宣言します。  少なくとも `End Function` ステートメント、`End Sub` ステートメント、または `End Property` ステートメントを記述する必要があります。  
  
2.  `Implements` 句を `Function` ステートメント、`Sub` ステートメント、`Property` ステートメント、または `Event` ステートメントの末尾に追加します。  次に例を示します。  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  プロパティを実装するときは、`ReadOnly` または `WriteOnly` をインターフェイス定義の場合と同様に使用します。  
  
4.  プロパティを実装するときは、必要に応じて `Get` プロシージャおよび `Set` プロシージャを宣言します。  
  
## 参照  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)