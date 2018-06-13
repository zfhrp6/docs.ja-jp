---
title: Is 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 8beca1dc8788514224f70cacc5b8ede0974f5230
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601951"
---
# <a name="is-operator-visual-basic"></a>Is 演算子 (Visual Basic)
2 つのオブジェクト参照変数を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`Boolean`値。  
  
 `object1`  
 必須。 どの`Object`名。  
  
 `object2`  
 必須。 どの`Object`名。  
  
## <a name="remarks"></a>コメント  
 `Is`演算子は、2 つのオブジェクト参照が同じオブジェクトを参照してかどうかを決定します。 ただし、値の比較は実行しません。 場合`object1`と`object2`正確な同じオブジェクト インスタンスをどちらも参照してください`result`は`True`以外の場合は一致しない場合、`result`は`False`します。  
  
 `Is` 使用することもできます、`TypeOf`キーワードを`TypeOf`しています.`Is`式で、オブジェクト変数のデータ型と互換性があるかどうかをテストします。  
  
> [!NOTE]
>  `Is`キーワードでも使用、[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)です。  
  
## <a name="example"></a>例  
 次の例では、`Is`オブジェクト参照のペアを比較する演算子です。 結果に割り当てられている、 `Boolean` 2 つのオブジェクトが同一かどうかを表す値です。  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 前の例を示しています、としてを使用して、`Is`両方をテストする演算子が事前バインドおよび遅延バインドされたオブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
