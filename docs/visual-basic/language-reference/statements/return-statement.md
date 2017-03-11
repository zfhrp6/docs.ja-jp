---
title: "Return Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Return"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Return statement, syntax"
  - "control flow, returning control to expressions"
  - "Return statement"
  - "expressions [Visual Basic], returning control to"
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Return Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Function`、`Sub`、`Get`、`Set`、または `Operator` の各プロシージャを呼び出したコードに制御を戻します。  
  
## 構文  
  
```  
Return  
-or-  
Return expression  
```  
  
## 指定項目  
 `expression`  
 `Function`、`Get`、または `Operator` の各プロシージャでは、必ず指定します。  呼び出し元のコードに返す値を表す式を指定します。  
  
## 解説  
 `Sub` プロシージャまたは `Set` プロシージャでは、`Exit Sub` ステートメントまたは `Exit Property` ステートメントが `Return` ステートメントに相当します。`expression` を指定することはできません。  
  
 `Function`、`Get`、または `Operator` の各プロシージャでは、`Return` ステートメント内に `expression` を指定する必要があり、`expression` はプロシージャの戻り値の型に変換できるデータ型に評価される必要があります。  `Function` プロシージャまたは `Get` プロシージャでは、式を割り当てる代わりにプロシージャ名を戻り値として使うこともできます。その場合、`Exit Function` ステートメントまたは `Exit Property` ステートメントを実行します。  `Operator` プロシージャでは、`Return` `expression` を使用する必要があります。  
  
 適切な数の `Return` ステートメントを同じプロシージャ内に指定できます。  
  
> [!NOTE]
>  `Finally` ブロックのコードは、`Try` または `Catch` ブロックの `Return` ステートメントが見つかった後、その `Return` ステートメントが実行される前に実行されます。  `Return` のステートメントは `Finally` ブロックに含めることはできません。  
  
## 使用例  
 次のコード例では、`Return` ステートメントを何回も使って、プロシージャで何も行う必要がなくなった時点で呼び出し元のコードに制御を戻しています。  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/return-statement_1.vb)]  
  
## 参照  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)