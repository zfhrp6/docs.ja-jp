---
title: "Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement | Microsoft Docs"
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
  - "vbc30157"
  - "bc30157"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30157"
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`With` ブロックの外部にピリオド \(.\) または感嘆符 \(\!\) がありますが、その左に式が記述されていません。  メンバー アクセス \(`.`\) およびディクショナリ メンバー アクセス \(`!`\) では、そのメンバーを含む要素を指定する式が必要です。  この式は、アクセサーのすぐ左に記述するか、メンバー アクセスを含む `With` ブロックのターゲットとして記述する必要があります。  
  
 **Error ID:** BC30157  
  
### このエラーを解決するには  
  
1.  `With` ブロックの書式が正しいことを確認します。  
  
2.  `With` ブロックがない場合は、アクセサーの左側に、メンバーを含む定義済みの要素に評価される式を追加します。  
  
## 参照  
 [Special Characters in Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)