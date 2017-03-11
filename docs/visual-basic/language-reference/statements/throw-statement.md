---
title: "Throw Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Throw"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structured exception handling, throw statements"
  - "try-catch exception handling, throw statements"
  - "throw statement, about throw statements"
  - "throwing exceptions, throw statement"
  - "exception handling, throw statement"
  - "On Error statement, throwing exceptions"
  - "throwing exceptions"
  - "exception handling, unstructured"
  - "throw statement"
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Throw Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャ内で例外をスローします。  
  
## 構文  
  
```  
Throw [ expression ]  
```  
  
## 指定項目  
 `expression`  
 スローする例外に関する情報を指定します。  `Catch` ステートメント内では省略可能です。それ以外の場合は必須です。  
  
## 解説  
 `Throw` ステートメントは、構造化例外処理コード \(`Try`...`Catch`...`Finally`\) または構造化しない例外処理コード \(`On Error GoTo`\) で処理できる例外をスローします。  Visual Basic では、適切な例外処理コードが見つかるまで呼び出し履歴をさかのぼるため、`Throw` ステートメントを使ってコード内のエラーをトラップできます。  
  
 式を持たない `Throw` ステートメントを使用できるのは、`Catch` ステートメント内だけです。この場合、このステートメントは、`Catch` ステートメントによって現在処理されている例外を再スローします。  
  
 `Throw` ステートメントでは、`expression` 例外の呼び出し履歴がリセットされます。  `expression` が指定されていない場合、呼び出し履歴は変更されません。  例外の呼び出し履歴には、<xref:System.Exception.StackTrace%2A> プロパティを介してアクセスできます。  
  
## 使用例  
 `Throw` ステートメントを使用して例外をスローするコードを次に示します。  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/throw-statement_1.vb)]  
  
## 必要条件  
 **名前空間**: [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール**: `Interaction`  
  
 **アセンブリ**: Visual Basic ランタイム ライブラリ \(Microsoft.VisualBasic.dll 内\)  
  
## 参照  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)