---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 076289ff303dce58f036d6c7cb1505b151da19f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602984"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
呼び出されたプロシージャまたはプロパティが呼び出し元のコードで引数の基になる変数の値を変更できないように引数が渡されることを指定します。  
  
## <a name="remarks"></a>コメント  
 `ByVal` 修飾子は、次のコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>例  
 次の例での使用、`ByVal`参照型の引数の渡しのパラメーターです。 例では、引数は`c1`、クラスのインスタンス`Class1`です。 `ByVal` 手順でコードの参照の引数の基になる値の変更を防止`c1`、アクセス可能なフィールドおよびのプロパティは保護されませんが、`c1`です。  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
