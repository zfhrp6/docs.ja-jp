---
title: "Ansi (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Ansi"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Declare statement, marshaling strings"
  - "ANSI, Visual Basic"
  - "ANSI"
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Ansi (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言されている外部プロシージャの名前に関係なく、すべての文字列を米国規格協会 \(ANSI\) 値にマーシャリングすることを指定します。  
  
 プロジェクトの外部に定義されたプロシージャを呼び出すと、Visual Basic コンパイラはプロシージャを正しく呼び出すために必要な情報にアクセスできません。  この情報には、プロシージャの場所、識別方法、呼び出しシーケンスと戻り値のデータ型、使用する文字列の文字セットが含まれます。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) は、外部プロシージャへの参照を作成し、この必須情報を提供します。  
  
 `Declare` ステートメントの `charsetmodifier` は、外部プロシージャの呼び出し時に文字列をマーシャリングするための文字セットの情報を提供します。  また、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。  `Ansi` 修飾子を指定すると、Visual Basic はすべての文字列を ANSI 値にマーシャリングし、プロシージャの検索中にプロシージャ名を変更しなくなります。  
  
 文字セットの修飾子を指定しない場合は `Ansi` が既定値です。  
  
## 解説  
 `Ansi` 修飾子は次の構文で使用します。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## スマート デバイス開発者のためのメモ  
 このキーワードはサポートされていません。  
  
## 参照  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)