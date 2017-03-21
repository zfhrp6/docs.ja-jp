---
title: "- 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 7f45094da7bc61687d9c767d25858aa214bf1978
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-visual-basic"></a>- 演算子 (Visual Basic)
2 つの数値式または数値式の負の値の差を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須です。 任意の数式。  
  
 `expression2`  
 場合のみ必要、`–`演算子が負の値を計算します。 任意の数式。  
  
## <a name="result"></a>結果  
 結果の違いは、`expression1`と`expression2`、またはの符号反転値`expression1`です。  
  
 結果のデータ型が数値型のデータ型に適した`expression1`と`expression2`です。 「整数演算」テーブルが表示[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。  
  
## <a name="supported-types"></a>サポートされている型  
 すべての数値型。 署名なしで、浮動小数点型を含む、`Decimal`です。  
  
## <a name="remarks"></a>コメント  
 最初の使用率が、前に示した構文に示すように、`–`演算子は、*バイナリ*違いについては、2 つの数値式の間で減算演算子。  
  
 2 つ目の使用率が、前に示した構文に示すように、`–`演算子は、*単項*式の負の値を否定演算子。 符号を逆の符号を反転は、この意味で`expression1`、結果は正ように場合`expression1`が負の値。  
  
 いずれかの式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`演算子は&0; として処理します。  
  
> [!NOTE]
>  `–`演算子を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、その再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。  
  
## <a name="example"></a>例  
 次の例では、`–`演算子を計算し、2 つの数値の差を返すし、数値を否定します。  
  
 [!code-vb[VbVbalrOperators&#10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 これらのステートメントの実行される`binaryResult`124.45 が含まれていて、 `unaryResult` –334.90 が含まれています。  
  
## <a name="see-also"></a>関連項目  
 [-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

