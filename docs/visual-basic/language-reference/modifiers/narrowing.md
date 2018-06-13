---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 54a18d0cc10e42829b48b0ef75bb77ab0d47b45f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597459"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
示します変換演算子 (`CType`) クラスまたは構造体を元のクラスまたは構造体の有効値の一部を保持することができない可能性がある型に変換します。  
  
## <a name="converting-with-the-narrowing-keyword"></a>縮小のキーワードを使用して変換します。  
 変換のプロシージャを指定する必要があります`Public Shared`に加えて`Narrowing`です。  
  
 縮小変換は常にではありません、実行時に成功し失敗したり、データの損失を伴うできます。 例としては、`Long`に`Integer`、`String`に`Date`、および派生型に基本型です。 基本データ型が派生型のすべてのメンバーを含めることはできず、そのため、派生型のインスタンスではないために、この最後の変換は縮小します。  
  
 場合`Option Strict`は`On`では、使用コードを使用する必要があります`CType`のすべての縮小変換します。  
  
 `Narrowing`キーワードは、このコンテキストで使用できます。  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [方法 : 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
