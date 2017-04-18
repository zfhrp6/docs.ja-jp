---
title: "-= 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
dev_langs:
- VB
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f640bd288c677954bae189c2e86ef096e7a73a2b
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-visual-basic"></a>-= 演算子 (Visual Basic)
変数またはプロパティの値から式の値を減算し、その結果を変数やプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須です。 任意の数値変数またはプロパティを使用しています。  
  
 `expression`  
 必須です。 任意の数式。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`-=`演算子は単純なスカラー変数、プロパティ、または配列の要素があります。 変数やプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
 `-=`演算子は最初に、変数または (演算子の左側にある) のプロパティの値から (演算子の右側にある) の式の値を減算します。 演算子は、その操作の結果を変数やプロパティを割り当てます。  
  
## <a name="overloading"></a>オーバーロード  
 [-演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)を指定できます*過負荷になって*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。 オーバー ロード、`-`演算子の動作に影響、`-=`演算子。 コードで使用する場合`-=`クラスまたは構造体をオーバー ロードで`-`、その再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。  
  
## <a name="example"></a>例  
 次の例では、 `-=`&1; を減算する演算子を`Integer`から別の変数と割り当て、その結果、後者の変数をします。  
  
 [!code-vb[VbVbalrOperators&#11;](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [-演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)   
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)

