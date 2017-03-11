---
title: "&#39;Optional&#39; expected | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30202"
  - "vbc30202"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30202"
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Optional&#39; expected
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャ宣言内の省略可能な引数に続いて必須引数が指定されています。  省略可能な引数の後に続く引数も、すべて省略可能であることが必要です。  
  
 **Error ID:** BC30202  
  
### このエラーを解決するには  
  
1.  引数を必須にする場合は、引数リスト内で最初の省略可能な引数の前に移動します。  
  
2.  引数を省略可能にする場合は、`Optional` キーワードを使用します。  
  
## 参照  
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)