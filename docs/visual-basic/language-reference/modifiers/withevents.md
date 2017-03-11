---
title: "WithEvents (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.WithEvents"
  - "WithEvents"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "WithEvents keyword"
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# WithEvents (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言された 1 つ以上のメンバー変数が、イベントを発生させる可能性のあるクラスのインスタンスを参照していることを指定します。  
  
## 解説  
 `WithEvents` を使って変数を定義すると、その変数のイベントを、メソッドが `Handles` キーワードを使用して処理することを宣言によって指定できます。  
  
 `WithEvents` は、クラス レベルまたはモジュール レベルでのみ使用できます。  つまり、`WithEvents` 変数の宣言コンテキストは、ソース ファイル、名前空間、構造体、プロシージャではなく、クラスまたはモジュールである必要があります。  
  
 `WithEvents` は、構造体のメンバーに対しては使用できません。  
  
 `WithEvents` を使って宣言できるのは、個々の変数だけです \(配列は不可\)。  
  
## 規則  
  
-   **要素の型。** `WithEvents` はオブジェクト変数に宣言して、変数がクラスのインスタンスを参照できるようにする必要があります。  ただし、`Object` 型で宣言することはできません。  イベントを発生できる特定のクラスとして宣言する必要があります。  
  
 `WithEvents` 修飾子は、[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) の構文で使用します。  
  
## 参照  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)