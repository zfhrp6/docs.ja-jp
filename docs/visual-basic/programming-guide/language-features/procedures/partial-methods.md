---
title: "Partial Methods (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.PartialMethod"
  - "PartialMethod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "custom logic into code [Visual Basic]"
  - "partial methods [Visual Basic]"
  - "partial, methods [Visual Basic]"
  - "methods [Visual Basic], partial methods"
  - "inserting custom logic into code"
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Partial Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

開発者は、部分メソッドを使用して、カスタム ロジックをコードに挿入できます。  通常、このコードは、デザイナーによって生成されるクラスの一部です。  部分メソッドは、コード ジェネレーターによって作成される部分クラスの中に定義され、何かが変更されていることを通知するためによく使用されます。  開発者は、これらを使用して、変更に応答する独自の動作を指定できます。  
  
 コード ジェネレーターのデザイナーは、メソッド シグネチャと、メソッドへの 1 つ以上の呼び出しだけを定義します。  生成されるコードの動作をカスタマイズする場合、開発者は、メソッドの実装を用意できます。  実装の用意がない場合、メソッドへの呼び出しはコンパイラによって削除され、パフォーマンスのオーバーヘッドの追加は発生しません。  
  
## 宣言  
 生成されるコードでは、シグネチャ行の先頭に `Partial` キーワードを配置することで、部分メソッドの定義をマークします。  
  
```vb#  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 この定義は、次の条件を満たす必要があります。  
  
-   メソッドは、`Function` ではなく、`Sub` である必要があります。  
  
-   メソッドの本体は、空のままにする必要があります。  
  
-   アクセス修飾子は、`Private` にする必要があります。  
  
## 実装  
 実装は、主に、部分メソッドの本体に入力することで構成されます。  実装は、通常は定義から分離した部分クラスであり、生成されるコードを拡張する開発者によって記述されます。  
  
```vb#  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 上の例では、宣言内のシグネチャを正確に複製しますが、他の指定も可能です。  具体的には、`Overloads` や `Overrides` などの修飾子を追加できます。  `Overrides` 修飾子は 1 つだけ使用できます。  メソッドの修飾子の詳細については、「[Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)」を参照してください。  
  
## \[条件\]  
 部分メソッドは、他の `Sub` プロシージャと同じように呼び出します。  メソッドが実装されている場合は、引数が評価され、メソッドの本体が実行されます。  ただし、部分メソッドの実装は省略可能です。  メソッドが実装されない場合、メソッドに対する呼び出しは無効であり、メソッドに引数として渡された式は評価されません。  
  
## 例  
 Product.Designer.vb という名前のファイルに、`Quantity` プロパティがある `Product` クラスを定義します。  
  
 [!code-vb[VbVbalrPartialMeths#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Product.vb という名前のファイルに、`QuantityChanged` の実装を用意します。  
  
 [!code-vb[VbVbalrPartialMeths#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 最後に、プロジェクトの Main メソッド内で `Product` インスタンスを宣言し、`Quantity` プロパティの初期値を指定します。  
  
 [!code-vb[VbVbalrPartialMeths#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 次のメッセージを表示するメッセージ ボックスが表示されます。  
  
 `Quantity was changed to 100`  
  
## 参照  
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Code Generation in LINQ to SQL](../Topic/Code%20Generation%20in%20LINQ%20to%20SQL.md)   
 [Adding Business Logic By Using Partial Methods](../Topic/Adding%20Business%20Logic%20By%20Using%20Partial%20Methods.md)