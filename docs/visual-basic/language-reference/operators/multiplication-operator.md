---
title: '* 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 4e2d1000afcf8951e8914335f7b5a278b49f6277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603627"
---
# <a name="-operator-visual-basic"></a>* 演算子 (Visual Basic)
2 つの数値を乗算します。  
  
## <a name="syntax"></a>構文  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`number1`|必須。 任意の数式。|  
|`number2`|必須。 任意の数式。|  
  
## <a name="result"></a>結果  
 結果は、製品の`number1`と`number2`です。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含むすべての数値型と`Decimal`です。  
  
## <a name="remarks"></a>コメント  
 結果のデータ型は、オペランドの型によって異なります。 次の表では、結果のデータ型を決定する方法を示します。  
  
|オペランドのデータ型|結果のデータ型|  
|---|---|  
|両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|数値データ型のデータ型に適した`number1`と`number2`です。 「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。|  
|両方の式が[10 進数](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|両方の式が[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|いずれかの式は、浮動小数点データ型 (`Single`または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)) 両方ではなく`Single`(注`Decimal`浮動小数点データ型ではない)|`Double`|  
  
 式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
## <a name="overloading"></a>オーバーロード  
 `*`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 この例では、`*`演算子を 2 つの数値を乗算します。 2 つのオペランドの積になります。  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [*= 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
