---
title: "Declaration expected | Microsoft Docs"
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
  - "vbc30188"
  - "bc30188"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30188"
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declaration expected
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

代入ステートメントやループ ステートメントなどの非宣言ステートメントが、プロシージャの外側にあります。  プロシージャの外側に記述できるのは宣言だけです。  
  
 または、プログラミング要素が、`Dim` や `Const` などの宣言キーワードを使用せずに宣言されています。  
  
 **Error ID:** BC30188  
  
### このエラーを解決するには  
  
-   非宣言ステートメントをプロシージャの本体に移動します。  
  
-   適切な宣言キーワードを使用して宣言を開始します。  
  
-   宣言キーワードのスペルが正しいかどうかを確認します。  
  
## 参照  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)