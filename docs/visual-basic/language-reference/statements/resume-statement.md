---
title: "Resume Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Resume"
  - "vb.ResumeNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Next statement, Resume"
  - "Resume Next statement"
  - "execution, resuming"
  - "run-time errors, resuming after"
  - "Resume statement, syntax"
  - "errors [Visual Basic], resuming after"
  - "Error statement, and Resume statement"
  - "execution"
  - "Resume statement"
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Resume Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

エラー処理ルーチンが終了した後で実行を再開します。  
  
 ここでは構造化されていない例外処理と `On Error` と `Resume` のステートメントを使用するよりも構造化例外処理を使用することをお勧めします。  詳細については、「[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
## 構文  
  
```  
Resume [ Next | line ]  
```  
  
## 指定項目  
 `Resume`  
 必ず指定します。  エラー ハンドラーと同じプロシージャでエラーが発生した場合は、エラーの原因となったステートメントから実行が再開されます。  呼び出されたプロシージャでエラーが発生した場合は、エラー処理ルーチンを含むプロシージャから最後に呼び出されたステートメントから実行が再開されます。  
  
 `Next`  
 省略可能です。  エラー ハンドラーと同じプロシージャでエラーが発生した場合は、エラーの原因となったステートメントの直後のステートメントから実行が再開されます。  呼び出されたプロシージャでエラーが発生した場合は、エラー処理ルーチン \(または `On Error Resume Next` ステートメント\) を含むプロシージャから最後に呼び出されたステートメントの直後のステートメントから実行が再開されます。  
  
 `line`  
 省略可能です。  必須の `line` 引数で指定した行から実行が再開されます。  引数 `line` は行ラベルまたは行番号で、エラー ハンドラーと同じプロシージャに含まれる必要があります。  
  
## 解説  
  
> [!NOTE]
>  ここでは構造化されていない例外処理と `On Error` と `Resume` のステートメントを使用するよりも構造化例外処理を使用することをお勧めします。  詳細については、「[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
 エラー処理ルーチン以外で `Resume` ステートメントを使用すると、エラーが発生します。  
  
 `Try...Catch...Finally` ステートメントを含むプロシージャ内では、`Resume` ステートメントは使用できません。  
  
## 使用例  
 この例では、`Resume` ステートメントを使用して、プロシージャ内のエラー処理を終了させ、エラーが発生したステートメントの実行を再開します。  `Resume` ステートメントの用途を示すために、エラー番号 55 を生成します。  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## 必要条件  
 **名前空間**: [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ**: Visual Basic ランタイム ライブラリ \(Microsoft.VisualBasic.dll 内\)  
  
## 参照  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)