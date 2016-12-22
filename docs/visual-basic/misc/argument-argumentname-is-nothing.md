---
title: "引数 &#39;&lt;argumentname&gt;&#39; は Nothing です | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_InvalidNullValue1"
ms.assetid: abbde904-c191-4911-8822-c9dd2f81d616
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引数 &#39;&lt;argumentname&gt;&#39; は Nothing です
式には、null 引数が含まれています。  
  
### このエラーを解決するには  
  
1.  式の引数のスペルを確認します。 変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に作成されることがあります。  
  
2.  式の変数 \(特に、他のプロシージャから引数としてプロシージャに渡されたもの\) に対してこれまで実行した操作を確認します。  
  
## 参照  
 [Passing Arguments by Value and by Reference](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Parameter Passing Mechanism for Visual Basic 6.0 Users](http://msdn.microsoft.com/ja-jp/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)