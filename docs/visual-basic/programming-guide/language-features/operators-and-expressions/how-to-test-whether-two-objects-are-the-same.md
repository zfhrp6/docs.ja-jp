---
title: "How to: Test Whether Two Objects Are the Same (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], reference"
  - "Is operator [Visual Basic], comparing objects"
  - "reference variables"
  - "variables [Visual Basic], referring to same object"
  - "objects [Visual Basic], variables referring to same"
  - "Visual Basic code, operators"
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Test Whether Two Objects Are the Same (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オブジェクトを参照する 2 つの変数がある場合は、`Is` または `IsNot` 演算子、またはその両方を使用して、2 つの変数が同じインスタンスを参照しているかどうかを確認できます。  
  
### 2 つのオブジェクトが等しいかどうかをテストするには  
  
-   2 つの変数をオペランドとして、[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) または [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)を使用します。  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 2 つのオブジェクトが同じインスタンスを参照しているかどうかに応じて、特定のアクションを実行することがあります。  前述の例では、`c` というコントロールをフォーム `f` 上のアクティブなコントロールと比較しています。  アクティブなコントロールがない場合、またはアクティブなコントロールが `c` と同じインスタンスでない場合は、`If` ステートメントが失敗し、プロシージャはこれ以上の処理を行わずに制御を返します。  
  
 `Is` と `IsNot` のどちらを使用するかは、個人的な好みの問題です。  一部の式では、どちらかの方が他方より読みやすいコードになることがあります。  
  
## 参照  
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)