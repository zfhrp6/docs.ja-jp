---
title: "#If...Then...#Else Directives | Microsoft Docs"
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
  - "vb.#EndIf"
  - "#End If"
  - "#Then"
  - "#ElseIf"
  - "vb.#ElseIf"
  - "vb.#Else"
  - "vb.#If"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, compiling"
  - "#If directive [Visual Basic]"
  - "conditional compilation, directives"
  - "#End if directive [Visual Basic]"
  - "selective compiling"
  - "else directive (#else)"
  - "#Else directive [Visual Basic]"
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #If...Then...#Else Directives
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

式の値に基づいて、条件付きのコンパイルを行います。  
  
## 構文  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## 指定項目  
 `expression`  
 `#If` ステートメントおよび `#ElseIf` ステートメント に対しては必ず指定します。それ以外の場合は省略できます。  真 \(`True`\) または偽 \(`False`\) を評価する、1 つ以上の条件付きコンパイル定数、リテラル値、および演算子だけで構成される任意の式を指定します。  
  
 `statements`  
 `#If` ステートメント ブロックに対しては必ず指定します。それ以外の場合は省略できます。  関連付けられた式が真 \(`True`\) に評価される場合にコンパイルされる、Visual Basic のプログラム行またはコンパイラ ディレクティブを指定します。  
  
 `#End If`  
 `#If` ステートメント ブロックを終了します。  
  
## 解説  
 `#If...Then...#Else` ディレクティブの動作は、`If...Then...Else` ステートメントの動作と表面上は同じに見えます。  しかし、`#If...Then...#Else` ディレクティブはコンパイラが何をコンパイルするかを評価するのに対し、`If...Then...Else` ステートメントは実行時に条件を評価する点が異なります。  
  
 通常、条件付きコンパイルは、同じプログラムを異なるシステムでコンパイルするために使用します。  また、デバッグ コードが実行可能ファイルに表示されるのを防ぐためにも使用します。  条件付きコンパイルによって省略されたコードは、コンパイル後の実行可能ファイルからは取り除かれるため、プログラムのサイズや動作に影響しません。  
  
 評価結果に関係なく、すべての式が `Option Compare Binary` を使って評価されます。  `Option Compare` ステートメントは、`#If` ステートメントと `#ElseIf` ステートメントの式に影響しません。  
  
> [!NOTE]
>  `#If`、`#Else`、`#ElseIf`、および `#End If` ディレクティブを単体で使用することはできません。  他のコードをこれらのディレクティブと同じ行に記述することはできません。  
  
## 使用例  
 この例では、`#If...Then...#Else` ブロックを使用して、特定のステートメントをコンパイルするかどうかを決定します。  
  
 [!CODE [VbVbalrConditionalComp#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#1)]  
  
## 参照  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)