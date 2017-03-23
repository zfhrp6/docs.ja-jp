---
title: "How to: Create a Variable that Does Not Change in Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], read-only"
  - "variables [Visual Basic], constant value"
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a Variable that Does Not Change in Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

値の変わらない変数という概念は、一見矛盾しているように見えます。  しかし、場合によっては定数を使用できないこともあり、そのようなときに固定値を持つ変数を使用すると便利です。  このような場合に、[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) キーワードを使用してメンバー変数を定義できます。  
  
 次のような場合は、[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) を使用して定数を宣言し、値を割り当てることはできません。  
  
-   `Const` ステートメントが、使用するデータ型を受け付けない。  
  
-   コンパイル時には値がわからない。  
  
-   コンパイル時に定数値を計算できない。  
  
### 値の変わらない変数を作成するには  
  
1.  モジュール レベルで、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を指定してメンバー変数を宣言し、[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) キーワードを含めます。  
  
    ```  
  
    Dim ReadOnly timeStarted  
    ```  
  
     メンバー変数に対してのみ `ReadOnly` を指定します。  これは、プロシージャ外部で、モジュール レベルの変数を定義することが必要であることを意味します。  
  
2.  コンパイル時に単一のステートメントで値を計算できる場合は、`Dim` ステートメントで初期化の句を指定します。  [As](../../../../visual-basic/language-reference/statements/as-clause.md) 句の後ろに等号 \(`=`\) を付け、式を続けます。  コンパイラでこの式を定数値に評価できることを確認します。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     `ReadOnly` 変数に値を割り当てることができるのは 1 回だけです。  この値を割り当てた後は、いずれのコードもこの値を変更することはできません。  
  
     コンパイル時に値がわからない、またはコンパイル時に単一ステートメントではこれを計算できない場合は、実行時にコンストラクター内で値を割り当てることができます。  実行時に値を割り当てるには、クラス レベルまたは構造体レベルで `ReadOnly` 変数を宣言する必要があります。  そのクラスまたは構造体のコンストラクター内では、変数の固定値を計算し、コンストラクターから返される前にその値を変数に割り当てます。  
  
## 参照  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)