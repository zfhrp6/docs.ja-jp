---
title: "&gt;&gt;= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.>>="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator >>= [Visual Basic]"
  - "compound assignment statements"
  - ">>= operator [Visual Basic]"
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# &gt;&gt;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数またはプロパティの値に右シフトの算術演算を実行し、その結果を元の変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty >>= amount  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  整数型 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` または `ULong`\) の変数またはプロパティです。  
  
 `amount`  
 必ず指定します。  整数型 \(`Integer`\) に拡大変換されるデータ型の数値表現です。  
  
## 解説  
 `>>=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `>>=` 演算子は、最初に変数またはプロパティの値の算術右シフトを実行します。  演算子は、変数またはプロパティに再度その操作の結果を代入します。  
  
 数値のシフトは、循環的には行われません。つまり、一方の端からはみ出したビットが、もう一方の端に補われることはありません。  右シフトの算術演算では、右端のビット位置を超えてシフトされるビットは破棄され、左端のビットは左側に空いたビット位置に移されます。  これは、`variableorproperty` が負の値である場合、空いた位置に 1 が設定されることを示します。  `variableorproperty` が正の値である場合、またはデータ型が unsigned 型である場合、空いた位置にはゼロが設定されます。  
  
## オーバーロード  
 [\>\> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  `>>` 演算子のオーバーロードは、`>>=` 演算子の動作に影響を与えます。  コード内で、`>>` をオーバーロードするクラスや構造体で `>>=` が使用されている場合は、再定義された後の動作を必ず理解するようにしてください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `>>=` 演算子を使って、整数型 \(`Integer`\) 変数のビット パターンを、指定されたビット数だけ右にシフトし、結果を元の変数に代入する例を次に示します。  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## 参照  
 [\>\> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)