---
title: "Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39; | Microsoft Docs"
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
  - "bc30941"
  - "vbc30941"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30941"
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

構造体定義には、非共有変数および非共有の非カスタム イベントを含めることができません。  
  
 各構造体には、全インスタンスで共有 \([Shared](../../../visual-basic/language-reference/modifiers/shared.md)\) するのではなく、特定のインスタンスそれぞれに適用される変数またはイベントが必要です。  非共有の定数、プロパティ、およびプロシージャはこの要件を満たしません。  また、非共有の変数がなく、非共有のイベントが 1 つだけ存在する場合に、そのイベントを `Custom` イベントにすることはできません。  
  
 **Error ID:** BC30941  
  
### このエラーを解決するには  
  
-   `Shared` ではない変数またはイベントを 1 つ以上定義します。  イベントを 1 つだけ定義する場合には、そのイベントを非カスタムかつ非共有にする必要があります。  
  
## 参照  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)