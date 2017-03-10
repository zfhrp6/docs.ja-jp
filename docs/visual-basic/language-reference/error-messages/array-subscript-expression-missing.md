---
title: "Array subscript expression missing | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30306"
  - "vbc30306"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30306"
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Array subscript expression missing
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

配列の初期化において、配列の範囲を定義する添字が 1 つ以上見つかりません。  たとえば、ステートメントに `myArray (5,5,,10)` のような式が含まれているとします。この場合、3 番目の添字が抜けています。  
  
 **Error ID:** BC30306  
  
### このエラーを解決するには  
  
-   不足しているインデックスを指定します。  
  
## 参照  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)