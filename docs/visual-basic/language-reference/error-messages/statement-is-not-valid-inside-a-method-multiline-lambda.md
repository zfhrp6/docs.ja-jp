---
title: "Statement is not valid inside a method/multiline lambda | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30024"
  - "bc30024"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30024"
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Statement is not valid inside a method/multiline lambda
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このステートメントは、`Sub`、`Function`、プロパティ `Get` プロシージャ、および、プロパティ `Set` プロシージャ内では有効ではありません。  一部のステートメントは、モジュール レベルまたはクラス レベルで配置できます。  `Option Strict` などのその他のステートメントは、名前空間レベルで指定し、その他すべての宣言に先行する必要があります。  
  
 **Error ID:** BC30024  
  
### このエラーを解決するには  
  
-   問題のステートメントをプロシージャから削除します。  
  
## 参照  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)