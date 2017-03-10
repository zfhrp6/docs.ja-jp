---
title: "REM Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.'"
  - "vb.Rem"
  - "Rem"
  - "'"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "REM statement"
  - "comments, Visual Basic code"
  - "code comments, Visual Basic"
  - "Visual Basic code, comments"
  - "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# REM Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プログラムのソース コード内にコメントを記述するときに指定します。  
  
## 構文  
  
```  
REM comment  
' comment  
```  
  
## 指定項目  
 `comment`  
 省略可能です。  記述するコメント本文を指定します。  スペースが必要です、 `REM`キーワードと`comment`。  
  
## 解説  
 `REM` ステートメントを 1 行に単独で記述する方法と、別のステートメントの後に記述する方法があります。  `REM` ステートメントを記述した行では、`REM` ステートメントの後に別のステートメントを記述しないでください。  別のステートメントの後に `REM` ステートメントを記述する場合は、前のステートメントとの間にスペースを挿入する必要があります。  
  
 `REM` の代わりに一重引用符 \(`'`\) を使用できます。  これは、コメントを別のステートメントの後に記述する場合にも、1 行に単独で記述する場合にも当てはまります。  
  
> [!NOTE]
>  行連結シーケンス \(`_`\) を使用して `REM` ステートメントを続けて記述しないでください。  コンパイラは、コメントの開始点以降、文字に特別な意味があるかどうかをチェックしません。  複数行にコメントを記述する場合は、各行に `REM` ステートメントまたはコメント記号 \(`'`\) を記述してください。  
  
## 使用例  
 `REM` ステートメントを使ってプログラムにコメントを記述するコード例は、次のとおりです。  次の例では、`REM` の代わりに一重引用符 \(`'`\) を使用する方法も示します。  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/rem-statement_1.vb)]  
  
## 参照  
 [Comments in Code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)   
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)