---
title: "#Const Directive | Microsoft Docs"
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
  - "vb.#Const"
  - "#vb.Const"
  - "#Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "#Const directive"
  - "conditional compilation, directives"
  - "Const directive (#Const)"
  - "Visual Basic compiler, compiler directives"
  - "constants, Const directive"
  - "constants, declaring"
  - "Const statement [Visual Basic], directive (#Const)"
  - "declaring constants, #const directive"
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #Const Directive
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic の条件付きコンパイル定数を定義します。  
  
## 構文  
  
```  
#Const constname = expression  
```  
  
## 指定項目  
 `constname`  
 必ず指定します。  定義する定数の名前。  
  
 `expression`  
 必ず指定します。  リテラル値、その他の条件付きコンパイル定数、算術演算子や論理演算子 \(`Is` を除く\) を任意に組み合わせた式を指定します。  
  
## 解説  
 条件付きコンパイル定数は、定義されているファイル内でだけ参照できるプライベート定数です。  `#Const` ディレクティブを使ってパブリックなコンパイル定数を作成することはできません。パブリックなコンパイル定数はユーザー インターフェイス内かまたは `/define` コンパイラ オプションを使ってしか作成できません。  
  
 `expression` に使用できるのは、条件付きコンパイル定数とリテラル値だけです。  `Const` で定義された通常の定数を使用すると、エラーが発生します。  逆に言えば、`#Const` キーワードで定義された定数は、条件付きコンパイル以外には使えません。  定数を未定義のまま使用することもできます。未定義の定数の値は `Nothing` になります。  
  
## 使用例  
 `#Const` ディレクティブの使用例を次に示します。  
  
 [!CODE [VbVbalrConditionalComp#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#3)]  
  
## 参照  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)