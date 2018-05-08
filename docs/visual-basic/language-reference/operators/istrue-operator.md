---
title: IsTrue 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: fc01b074d9aba245b1c55b75b841a7f195f7ec04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="istrue-operator-visual-basic"></a>IsTrue 演算子 (Visual Basic)
式は、かどうかを判断`True`です。  
  
 呼び出すことはできません`IsTrue`明示的に、コードが、Visual Basic のコンパイラが使用できるからコードを生成する`OrElse`句。 クラスまたは構造体を定義しでその型の変数を使用する場合、`OrElse`を定義する必要があります句、`IsTrue`そのクラスまたは構造にします。  
  
 コンパイラは、`IsTrue`と`IsFalse`演算子として、*ペア*です。 つまり、それらのいずれかを定義する場合をする必要がありますも定義、もう 1 つです。  
  
## <a name="compiler-use-of-istrue"></a>IsTrue のコンパイラの使用  
 クラスまたは構造体を定義したらでその型の変数を使用することができます、 `For`、 `If`、 `Else``If`、または`While`ステートメント、または、`When`句。 これを行う場合、コンパイラは、演算子に、型に変換する`Boolean`条件をテストするための値します。 これは、適切な演算子は次の順序で検索します。  
  
1.  クラスまたは構造から拡大変換演算子`Boolean`です。  
  
2.  クラスまたは構造から拡大変換演算子`Boolean?`です。  
  
3.  `IsTrue`クラスまたは構造体で演算子。  
  
4.  縮小変換`Boolean?`からの変換を含まない`Boolean`に`Boolean?`です。  
  
5.  クラスまたは構造から縮小変換演算子`Boolean`です。  
  
 変換を定義していない場合`Boolean`または`IsTrue`演算子、コンパイラがエラーを通知します。  
  
> [!NOTE]
>  `IsTrue`演算子を指定できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できますその動作のオペランドは、そのクラスまたは構造体の型を持つときにすることを意味します。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次のコード例の定義を含む構造体の輪郭の定義、`IsFalse`と`IsTrue`演算子。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [方法 : 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
