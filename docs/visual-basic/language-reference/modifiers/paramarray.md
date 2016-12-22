---
title: "ParamArray (Visual Basic) | Microsoft Docs"
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
  - "vb.ParamArray"
  - "ParamArray"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ParamArray keyword"
  - "ParamArray keyword, syntax"
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ParamArray (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロシージャが、省略可能なパラメーターとして、指定されたデータ型の要素の配列を受け取ることを示します。  `ParamArray` は、パラメーター リストの最後のパラメーターにのみ使用できます。  
  
## 解説  
 `ParamArray` を使うと、任意の数の引数をプロシージャに渡すことができます。  `ParamArray` パラメーターは常に [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) を使って宣言されます。  
  
 `ParamArray` パラメーターには、適切なデータ型の配列を渡すか、コンマ区切りの値のリストを渡すか、または何も渡さないという方法によって、1 つ以上の引数を指定できます。  詳細については、「[Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)」の「ParamArray を呼び出す」を参照してください。  
  
> [!IMPORTANT]
>  無限に増大する配列を扱う場合、アプリケーション内部の容量を超過してしまう可能性があります。  呼び出し元のコードからパラメーターの配列を受け取る場合、その長さをテストし、アプリケーションに対して大きすぎるようであれば、適切な手順を行ってください。  
  
 `ParamArray` 修飾子は、次の場合に使用できます。  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)