---
title: "&lt;&lt;= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.<<="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator <<="
  - "assignment statements, compound"
  - "<<= operator [Visual Basic]"
  - "statements [Visual Basic], compound assignment"
  - "operator<<="
  - "compound assignment statements"
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# &lt;&lt;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数またはプロパティの値に左シフトの算術演算を実行し、その結果を元の変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty <<= amount  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  整数型 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` または `ULong`\) の変数またはプロパティです。  
  
 `amount`  
 必ず指定します。  整数型 \(`Integer`\) に拡大変換されるデータ型の数値表現です。  
  
## 解説  
 `<<=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `<<=` 演算子は、最初に変数またはプロパティの値の算術左シフトを実行します。  演算子は、変数またはプロパティに再度その操作の結果を代入します。  
  
 数値のシフトは、循環的には行われません。つまり、一方の端からはみ出したビットが、もう一方の端に補われることはありません。  左シフトの算術演算では、結果のデータ型の範囲を超えてシフトされるビットは破棄され、右側に空いたビット位置はゼロに設定されます。  
  
## オーバーロード  
 [\<\< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  `<<` 演算子をオーバーロードすると、`<<=` 演算子の動作に影響します。  `<<` をオーバーロードしているクラスまたは構造体で `<<=` を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `<<=` 演算子を使用して、整数型 \(`Integer`\) 変数のビット パターンを、指定されたビット数だけ左にシフトし、結果を元の変数に代入する例を、次に示します。  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## 参照  
 [\<\< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)