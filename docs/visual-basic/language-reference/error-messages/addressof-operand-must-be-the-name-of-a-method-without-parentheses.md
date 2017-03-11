---
title: "&#39;AddressOf&#39; operand must be the name of a method (without parentheses) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30577"
  - "bc30577"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30577"
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;AddressOf&#39; operand must be the name of a method (without parentheses)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。  構文は次のとおりです。  
  
 `AddressOf` `procedurename`  
  
 `AddressOf` の後の引数をかっこで囲んでありますが、このかっこは必要ありません。  
  
 **Error ID:** BC30577  
  
### このエラーを解決するには  
  
1.  `AddressOf` の後の引数を囲んでいるかっこを削除します。  
  
2.  引数がメソッド名であることを確認します。  
  
## 参照  
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)