---
title: "Static (Visual Basic) | Microsoft Docs"
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
  - "vb.Static"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "static modifier"
  - "Static keyword"
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Static (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

1 つ以上のローカル変数が、それらが宣言されたプロシージャの終了後も存在し続け、最後に設定された値を保持することを指定します。  
  
## 解説  
 通常、プロシージャ内のローカル変数は、プロシージャが停止した直後に削除されます。  静的変数はプロシージャの終了後も存在し続け、最後に設定された値を保持します。  次回、コードからそのプロシージャを呼び出したとき、変数は初期化し直されることなく、最後に割り当てられた値をそのまま保持します。  静的変数は、自らが定義されたクラスやモジュールの有効期間中存在し続けます。  
  
## 規則  
  
-   **宣言コンテキスト。** `Static` はローカル変数にのみ使用できます。  つまり、`Static` 変数は、プロシージャまたはプロシージャ内のブロックのコンテキストで宣言される必要があり、ソース ファイル、名前空間、クラス、構造体、またはモジュールのコンテキストでは宣言できません。  
  
     `Static` は、構造体のプロシージャの内部では使用できません。  
  
-   `Static` ローカル変数のデータ型は推論できません。  詳細については、「[Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  
  
-   **結合された修飾子。**同じ変数宣言で `Static` を、`ReadOnly`、`Shadows` または `Shared` と同時に指定することはできません。  
  
## \[動作\]  
 `Shared` プロシージャの静的変数を宣言する場合、静的変数に 1 回だけがアプリケーション全体に使用できます。  クラス名クラスのインスタンスをポイントする変数ではなくを使用して `Shared` プロシージャをダイヤルします。  
  
 `Shared`ではないプロシージャの静的変数を宣言する場合、変数に 1 回だけがクラスの各インスタンスで使用できます。  クラスの特定のインスタンスをポイントする変数を使用して、非共有されたプロシージャをダイヤルします。  
  
## 使用例  
 次の例は `Static` の使い方を示しています。  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 `Static` 変数 `totalSales` は、一度だけ 0 に初期化されます。  `updateSales` を何度入力しても、`totalSales` は最後に計算された値をそのまま保持します。  
  
 `Static` 修飾子は次の構文で使用します。  
  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## 参照  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)