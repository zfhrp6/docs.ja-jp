---
title: "/= 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab0a007f039d3dbda989bb605cb80fcf5fc7460a
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>/= 演算子 (Visual Basic)
変数またはプロパティの値を式の値で除算し、浮動小数点の結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須です。 任意の数値変数またはプロパティを使用しています。  
  
 `expression`  
 必須です。 任意の数式。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`/=`演算子は単純なスカラー変数、プロパティ、または配列の要素があります。 変数やプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
 `/=`演算子は最初、(演算子の右側にある) の式の値で変数または (演算子の左側にある) のプロパティの値を除算します。 演算子は、その操作の浮動小数点の結果を変数やプロパティを割り当てます。  
  
 このステートメントは、代入、`Double`変数または左のプロパティの値。 If `Option Strict` is `On`, `variableorproperty` must be a `Double`. 場合`Option Strict`は`Off`、Visual Basic の暗黙的な変換を実行およびに結果として得られる値を代入`variableorproperty`、実行時に潜在的なエラーとします。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。  
  
## <a name="overloading"></a>オーバーロード  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。 オーバー ロード、`/`演算子の動作に影響、`/=`演算子。 コードで使用する場合`/=`クラスまたは構造体をオーバー ロードで`/`、その再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。  
  
## <a name="example"></a>例  
 次の例では、`/=`演算子を&1; つに分割`Integer`秒を割り当て、最初の変数に、商により変数です。  
  
 [!code-vb[VbVbalrOperators&17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)

