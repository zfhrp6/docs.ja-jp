---
title: "10 進型 (Decimal) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a>10 進型 (Decimal) (Visual Basic)
可変 10 の累乗によってスケーリング 96 ビット (12 バイト) 整数値を表す 128 ビット (16 バイト) 値の符号付き保持します。 スケール ファクターです。 小数点の右側にある数字の数を指定します。範囲は 0 から 28 です。 最大有効値は 0 (小数点は除く) の小数点以下桁数、79,228,162,514,264,337,593,543,950,335 +/-(7 +/-.9228162514264337593543950335E + 28)。 小数点以下桁数が 28 7.9228162514264337593543950335 については、最大値し、(1 e ~ 28) +/-+/-0.0000000000000000000000000001 は、0 以外の最小値。  
  
## <a name="remarks"></a>コメント  
 `Decimal`データ型有効桁数の最大数を提供しています。 最大 29 桁をサポートしており 7.9228 x 10 を超える値を表すことができる ^28 です。 など、計算に特に適しています財務、桁の数字の数が多い必要がありますが、丸め誤差が許容することはできません。  
  
 `Decimal` の既定値は 0 です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **有効桁数です。** `Decimal`浮動小数点データ型がありません。 `Decimal`構造体は、符号ビット、およびスケール ファクター値のどの部分が、小数を指定する整数のバイナリ整数値を保持します。 このため、`Decimal`番号より正確な表現を持つ浮動小数点型よりもメモリ内 (`Single`と`Double`)。  
  
-   **パフォーマンス。** `Decimal`データ型はすべての数値型の最も遅い。 データ型を選択する前にパフォーマンスと精度の重要性を比較検討する必要があります。  
  
-   **拡大します。** `Decimal`拡大変換後のデータ型`Single`または`Double`です。 つまり、変換することができます`Decimal`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。  
  
-   **後続のゼロです。** Visual Basic では、後続の 0 は格納されません、`Decimal`リテラルです。 ただし、`Decimal`変数には、計算に必要なすべての後続のゼロが保持されます。 次に例を示します。  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     出力`MsgBox`前の例では、次のようにします。  
  
     d1 2.375、d2 を = = 1.625、d3 4.000、d4 = 4 を =  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `D` を付けると、そのリテラルは `Decimal` に変換されます。 ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 (`Decimal`) に変換されます。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Decimal?displayProperty=nameWithType> 構造体です。  
  
## <a name="range"></a>範囲  
 使用する必要があります、`D`に大きな値を代入する文字を入力、`Decimal`変数または定数。 この要件は、コンパイラが、リテラルとして解釈されるので`Long`リテラルの型文字以下の例のように、リテラルに依存しない限り、します。  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 宣言`bigDec1`に割り当てられている値の範囲に収まるので、オーバーフローを生成しない`Long`です。 `Long`に値を割り当てることができます、`Decimal`変数。  
  
 宣言`bigDec2`用に割り当てられている値が大きすぎるために、オーバーフロー エラーが発生`Long`です。 数値リテラルとして最初に解釈できないため、`Long`に割り当てることができない、`Decimal`変数。  
  
 `bigDec3`、リテラルの型文字`D`としてリテラルを解釈するコンパイラを強制することで問題が解決、`Decimal`の代わりとして、`Long`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Single データ型](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Double 型](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
