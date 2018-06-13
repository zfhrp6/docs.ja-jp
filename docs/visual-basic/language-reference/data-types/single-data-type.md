---
title: 単精度浮動小数点型 (Single) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 770961f225b139aaddf34b42327bca63638c725d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590786"
---
# <a name="single-data-type-visual-basic"></a>単精度浮動小数点型 (Single) (Visual Basic)
IEEE 32 ビット (4 バイト) の単精度浮動小数点数が 3.4028235 e + 38 までの値の範囲の符号付き - 1.401298E を通じて-1.401298E と負の値の 45-から 3.4028235 e + 38 正の値の 45。 単精度の数値は、実数の概算値を格納します。  
  
## <a name="remarks"></a>コメント  
 使用して、`Single`データ型の完全なデータの幅を必要としない浮動小数点値を含む`Double`です。 場合によっては、共通言語ランタイムがパックすることがあります、`Single`変数密接に関連しておよびメモリの消費量を保存します。  
  
 `Single` の既定値は 0 です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **有効桁数です。** 浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに留意してください。 これにより予期しない結果を比較値などの特定の操作から、`Mod`演算子。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。  
  
-   **拡大します。** `Single`拡大変換後のデータ型`Double`です。 つまり、変換することができます`Single`に`Double`遭遇することがなく、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。  
  
-   **後続のゼロです。** 浮動小数点データ型には、末尾の 0 文字の任意の内部表現はありません。 たとえば、それらによって区別されません 4.2000 および 4.2 です。 その結果、後続の 0 文字では、表示または浮動小数点値を印刷するときに表示されません。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `F` を付けると、そのリテラルは `Single` に変換されます。 ある識別子に識別子の型文字 `!` を付けると、その識別子は整数型 (`Single`) に変換されます。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Single?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Single?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal データ型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double 型](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
