---
title: "Error Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, types"
  - "errors [Visual Basic], types"
  - "errors [Visual Basic], logic"
  - "errors [Visual Basic], syntax"
  - "logic errors, Visual Basic"
  - "run-time errors, types of errors"
  - "syntax errors, Visual Basic"
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Error Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のエラー \(*例外*とも呼ばれます\) は、構文エラー、ランタイム エラー、および論理エラーの 3 つに分類できます。  
  
## 構文エラー  
 *構文エラー*は、コードを記述している間に検出されます。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、**コード エディター** ウィンドウでコードを入力しているときにチェックされ、単語のスペルミスした場合や、言語の要素を不正に使用した場合など間違いがあったときに警告が出ます。  構文エラーは最も一般的なエラーです。  エラーが発生したときに、その場で簡単に修正できます。  
  
> [!NOTE]
>  `Option Explicit` ステートメントは、構文エラーを防ぐ方法の 1 つです。  このステートメントを指定した場合、事前に宣言してからでないとアプリケーション内で変数を使用できません。  このため、宣言した変数をコード内で使用するときに入力ミスなどのエラーがあるとすぐに検出され、エラーを修正できます。  
  
## ランタイム エラー  
 *ランタイム エラー*は、コードをコンパイルして実行してからでないと発生しないエラーです。  構文エラーがなく、正しいように見えたのに実行できないコードなどがこれに該当します。  たとえば、ファイルを開くコード行を正しく記述したとします。  このとき、そのファイルが破損していると、アプリケーションは `Open` 関数を実行できないため停止します。  ほとんどのランタイム エラーは、問題のあるコードを書き直して再コンパイルおよび再実行することによって修正できます。  
  
## 論理エラー  
 *論理エラー*は、アプリケーションが実際に使用されるようになってから発生するエラーです。  これは、通常、ユーザーによる操作の結果として発生する、好ましくないまたは予期しない結果です。  たとえば、キーが間違って入力されるなどの外的要因によって、予測されているパラメーターの範囲内でアプリケーションが機能しなくなったり、アプリケーション全体が停止したりする場合があります。  論理エラーは、原因が必ずしも明らかではないため、一般に最も修正が難しいエラーです。  
  
## 参照  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [デバッガーの基本事項](/visual-studio/debugger/debugger-basics)