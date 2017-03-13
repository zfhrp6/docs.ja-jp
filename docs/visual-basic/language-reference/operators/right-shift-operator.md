---
title: "&gt;&gt; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.>>"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator>>"
  - ">> operator [Visual Basic]"
  - "bit shift operators"
  - "operator >>"
  - "right shift operators"
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# &gt;&gt; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ビット パターンに対して算術右シフトを実行します。  
  
## 構文  
  
```  
  
result = pattern >> amount  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  整数値を指定します。  ビット パターンをシフトした結果が格納されます。  データ型は、`pattern` の型と同じになります。  
  
 `pattern`  
 必ず指定します。  整数の式を指定します。  シフトされるビット パターンです。  データ型は整数型 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`\) である必要があります。  
  
 `amount`  
 必ず指定します。  数式を指定します。  ビット パターンは、このビット数だけシフトされます。  データ型は、整数型 \(`Integer`\) であるか、整数型 \(`Integer`\) に拡大変換する必要があります。  
  
## 解説  
 数値のシフトは、循環的には行われません。つまり、一方の端からはみ出したビットが、もう一方の端に補われることはありません。  右シフトの算術演算では、右端のビット位置を超えてシフトされるビットは破棄され、左端 \(符号\) のビットは左側に空いたビット位置に移されます。  これは、`pattern` が負の値である場合、空いた位置に 1 が設定されることを示します。それ以外の場合は、ゼロが設定されます。  
  
 `Byte`、`UShort`、`UInteger`、`ULong` のデータ型には符号がないため、シフトされる符号ビットがないことに注意してください。  `pattern` が符号なしの型である場合、空いた位置には常にゼロが設定されます。  
  
 結果に保持できるビット数を超えるシフトを回避するために、Visual Basic は `pattern` のデータ型に対応するサイズ マスクを使用して、`amount` の値をマスクします。  シフト量には、これらの値のバイナリの AND が使用されます。  サイズ マスクは次のとおりです。  
  
|`pattern` のデータ型|サイズ マスク \(10 進数\)|サイズ マスク \(16 進数\)|  
|---------------------|-----------------------|-----------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 `amount` が 0 の場合、`result` の値は `pattern` の値と同じです。  `amount` が負の値である場合は、符号なしの値と解釈され、適切なサイズ マスクでマスクされます。  
  
 数値のシフトではオーバーフロー例外は発生しません。  
  
## オーバーロード  
 `>>` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `>>` 演算子を使用して整数値の算術右シフトを実行する例を次に示します。  結果のデータ型は、シフトされる前の式と常に同じ型になります。  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 この例の結果は次のようになります。  
  
-   `result1` は 2560 \(0000 1010 0000 0000\)。  
  
-   `result2` は 160 \(0000 0000 1010 0000\)。  
  
-   `result3` は 2 \(0000 0000 0000 0010\)。  
  
-   `result4` は 640 \(0000 0010 1000 0000\)。  
  
-   `result5` は 0 \(右へ 15 回シフト\)。  
  
 `result4` のシフト量は 18 AND 15 として計算され、2 になります。  
  
 負の値の算術シフトを実行する例を次に示します。  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 この例の結果は次のようになります。  
  
-   `negresult1` は \-512 \(1111 1110 0000 0000\)。  
  
-   `negresult2` は \-1 \(符号ビットがシフトされている\)。  
  
## 参照  
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [\>\>\= Operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)