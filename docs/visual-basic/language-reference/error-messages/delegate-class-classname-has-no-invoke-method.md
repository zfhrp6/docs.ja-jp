---
title: "Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call | Microsoft Docs"
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
  - "vbc30220"
  - "bc30220"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30220"
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Invoke` がデリゲート クラスで実装されていないため、デリゲートを通じた `Invoke` の呼び出しに失敗しました。  
  
 **Error ID:** BC30220  
  
### このエラーを解決するには  
  
1.  デリゲート クラスのインスタンスが `Dim` ステートメントによって作成されており、プロシージャが `AddressOf` 演算子によってデリゲート インスタンスに代入されているかどうかを確認します。  
  
2.  デリゲート クラスを実装するコードを探し、そこで `Invoke` プロシージャが実装されているかどうかを確認します。  
  
## 参照  
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)