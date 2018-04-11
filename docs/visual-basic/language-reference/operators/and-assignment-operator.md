---
title: '&amp;= 演算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 929a9e8c3384451679fc52ad478eb03219d67192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a>&amp;= 演算子 (Visual Basic)
連結、`String`式を`String`変数またはプロパティと、結果を変数またはプロパティに割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須です。 どの`String`変数またはプロパティ。  
  
 `expression`  
 必須です。 任意のブール型 (`String`) の式を指定します。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`&=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。 `&=`演算子は、連結、 `String` 、右辺の式、`String`変数またはプロパティの左側にし、変数またはプロパティの左側に結果を代入します。  
  
## <a name="overloading"></a>オーバーロード  
 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合は。 オーバー ロード、`&`演算子の動作に影響、`&=`演算子。 コードで使用する場合`&=`クラスまたはオーバー ロードする構造体で`&`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例で、`&=`を 2 つ連結演算子`String`変数と、その結果、最初の変数を割り当てます。  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
