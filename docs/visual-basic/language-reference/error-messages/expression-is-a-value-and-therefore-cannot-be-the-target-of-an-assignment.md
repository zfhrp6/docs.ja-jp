---
title: "Expression is a value and therefore cannot be the target of an assignment | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30068"
  - "vbc30068"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30068"
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Expression is a value and therefore cannot be the target of an assignment
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

式に値を代入しようとしているステートメントがあります。  実行時に値を代入できるのは、書き込み可能な変数、プロパティ、または配列に対してのみです。  次の例は、どのような場合にこのエラーが発生するのかを示します。  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 上記の例は、プロパティおよび配列の要素についても当てはまります。  
  
 **間接アクセス**値の型による間接アクセスでも、このエラーが発生します。  次の例では、<xref:System.Windows.Forms.Control.Location%2A> を通して間接的にアクセスすることによって <xref:System.Drawing.Point> に値を設定しようとしています。  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 上記の例で、最後のステートメントは、<xref:System.Windows.Forms.Control.Location%2A> プロパティから返される <xref:System.Drawing.Point> 構造体を一時的に割り当てているだけであるため、失敗します。  構造体は値型であり、一時的な構造体は、このステートメントの実行後には保持されません。  <xref:System.Windows.Forms.Control.Location%2A> 用の変数を宣言して使用すると、より永続的に割り当てられる <xref:System.Drawing.Point> 構造体が作成されるため、問題を解決できます。  上記例の最後のステートメントを置き換えるためのコードを次の例に示します。  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **Error ID:** BC30068  
  
### このエラーを解決するには  
  
-   ステートメントが式に値を代入する場合は、式を、書き込みできる単一の変数、プロパティ、または配列要素に置き換えます。  
  
-   ステートメントが構造体など値型を通じて間接的にアクセスする場合は、その値型を保持するための変数を作成します。  
  
-   適切な構造体 \(またはその他の値型\) を変数に代入します。  
  
-   変数を使用して、プロパティにアクセスし、値を代入します。  
  
## 参照  
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)