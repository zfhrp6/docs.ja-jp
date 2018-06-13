---
title: '方法: 2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647606"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>方法: 2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)
オブジェクトを参照する 2 つの変数があれば、いずれかを使用できる、`Is`または`IsNot`演算子、またはその両方を同じインスタンスを参照しているかどうかを判断します。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>2 つのオブジェクトが等しいかどうかをテストするには  
  
-   使用して、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)または[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)オペランドとして 2 つの変数にします。  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 2 つのオブジェクトが同じインスタンスを参照するかどうかに応じて、特定のアクションを実行する可能性があります。 上記の例では、コントロール`c`フォームでアクティブなコントロールに対して`f`です。 アクティブなコントロールはありませんかがある場合はこれ以上が場合と同じコントロール インスタンス`c`、`If`ステートメントは失敗し、手順は、さらに処理することがなくを返します。  
  
 使用するかどうか`Is`または`IsNot`に個人の利便性の問題です。 1 つを指定された式に他方より読みやすくする可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
