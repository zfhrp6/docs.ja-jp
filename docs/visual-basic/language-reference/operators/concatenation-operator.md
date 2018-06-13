---
title: '&amp; 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 28d8cdb22974d77edf055ab9b2c6c767872e6783
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604303"
---
# <a name="amp-operator-visual-basic"></a>&amp; 演算子 (Visual Basic)
2 つの式の文字列の連結を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`String`または`Object`変数。  
  
 `expression1`  
 必須。 データ型に拡大変換を持つ任意の式`String`です。  
  
 `expression2`  
 必須。 データ型に拡大変換を持つ任意の式`String`です。  
  
## <a name="remarks"></a>コメント  
 データ型の場合`expression1`または`expression2`は`String`に拡大変換が`String`に変換されます`String`です。 かどうか、データ型のいずれかが拡大変換されないに`String`、コンパイラ エラーが発生します。  
  
 データ型`result`は`String`します。 1 つまたは両方の式が評価される場合[Nothing](../../../visual-basic/language-reference/nothing.md)またはの値が<xref:System.DBNull.Value?displayProperty=nameWithType>の値を文字列として扱われます""です。  
  
> [!NOTE]
>  `&`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
> [!NOTE]
>  型として変数を識別する、アンパサンド (&) 文字を使用することができますも`Long`します。 詳細については、次を参照してください。[型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)です。  
  
## <a name="example"></a>例  
 この例では、`&`演算子を強制的に文字列を連結します。 結果は、2 つの文字列オペランドの連結を表す文字列値です。  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [& = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic の連結演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
