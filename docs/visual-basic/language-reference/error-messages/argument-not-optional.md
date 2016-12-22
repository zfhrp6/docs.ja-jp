---
title: "Argument not optional (Visual Basic) | Microsoft Docs"
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
  - "vbrID449"
dev_langs: 
  - "VB"
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argument not optional (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

引数の数と型が合っていません。  引数の数が間違っているか、または省略できない引数が省略されています。  ユーザー定義のプロシージャの呼び出しで省略できるのは、プロシージャ定義で `Optional` として宣言されている引数だけです。  
  
### このエラーを解決するには  
  
1.  必要な引数をすべて指定します。  
  
2.  省略した引数が省略可能であることを確認します。  省略可能でない場合は、その引数を指定するか、またはプロシージャ定義で `Optional` として宣言します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)