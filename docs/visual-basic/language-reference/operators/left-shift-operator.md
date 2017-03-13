---
title: "&lt;&lt; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.<<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "bit shift operators"
  - "<< operator [Visual Basic]"
  - "operator <<, Visual Basic left shift operator"
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# &lt;&lt; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ビット パターンに対して算術左シフトを実行します。  
  
## 構文  
  
```  
  
result = pattern << amount  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  整数値を指定します。  ビット パターンをシフトした結果が格納されます。  データ型は、`pattern` の型と同じになります。  
  
 `pattern`  
 必ず指定します。  整数の式を指定します。  シフトされるビット パターンです。  データ型は整数型 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`\) である必要があります。  
  
 `amount`  
 必ず指定します。  数式を指定します。  ビット パターンは、このビット数だけシフトされます。  データ型は、整数型 \(`Integer`\) であるか、整数型 \(`Integer`\) に拡大変換する必要があります。  
  
## 解説  
 数値のシフトは、循環的には行われません。つまり、一方の端からはみ出したビットが、もう一方の端に補われることはありません。  左シフトの算術演算では、結果のデータ型の範囲を超えてシフトされるビットは破棄され、右側に空いたビット位置はゼロに設定されます。  
  
 結果に保持できるビット数を超えるシフトを回避するために、Visual Basic は `pattern` のデータ型に対応するサイズ マスクを使用して、`amount` の値をマスクします。  シフト量には、これらの値のバイナリの AND が使用されます。  サイズ マスクは次のとおりです。  
  
|`pattern` のデータ型|サイズ マスク \(10 進数\)|サイズ マスク \(16 進数\)|  
|---------------------|-----------------------|-----------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 `amount` が 0 の場合、`result` の値は `pattern` の値と同じです。  `amount` が負の値である場合は、符号なしの値と解釈され、適切なサイズ マスクでマスクされます。  
  
 数値のシフトではオーバーフロー例外は発生しません。  
  
> [!NOTE]
>  `<<` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `<<` 演算子を使用して整数値の算術左シフトを実行する例を次に示します。  結果のデータ型は、シフトされる前の式と常に同じ型になります。  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 この例の結果は、次のようになります。  
  
-   `result1` は 192 \(0000 0000 1100 0000\) です。  
  
-   `result2` は 3072 \(0000 1100 0000 0000\) です。  
  
-   `result3` は \-32768 \(1000 0000 0000 0000\) です。  
  
-   `result4` は 384 \(0000 0001 1000 0000\) です。  
  
-   `result5` は 0 \(15 桁左にシフト\) です。  
  
 `result4` のシフト量は 17 AND 15 として計算され、1 になります。  
  
## 参照  
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [\<\<\= Operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)