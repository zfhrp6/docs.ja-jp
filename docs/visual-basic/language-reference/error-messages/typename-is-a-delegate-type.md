---
title: "&#39;&lt;typename&gt;&#39; is a delegate type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32008"
  - "vbc32008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32008"
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &#39;&lt;typename&gt;&#39; is a delegate type
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

'\<typename\>' はデリゲート型です。デリゲート構造では、引数リストとして単一の AddressOf 式しか使用できません。AddressOf 式は、通常、デリゲート構築の代わりに使用できます。  
  
 デリゲート クラスのインスタンスを作成する `New` 句で、デリゲート コンストラクターへの無効な引数リストが指定されています。  
  
 デリゲート インスタンスを新規作成するときは、単一の `AddressOf` 式しか指定できません。  
  
 このエラーは、デリゲート コンストラクターに引数を渡していない場合、複数の引数を渡した場合、または有効な `AddressOf` 式ではない 1 つの引数を渡した場合に発生する可能性があります。  
  
 **Error ID:** BC32008  
  
### このエラーを解決するには  
  
-   `New` 句で、デリゲート クラスの引数リストに単一の `AddressOf` 式を使用します。  
  
## 参照  
 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)