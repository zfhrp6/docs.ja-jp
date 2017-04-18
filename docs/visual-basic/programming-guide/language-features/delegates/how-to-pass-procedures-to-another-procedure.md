---
title: "方法: Visual Basic での別のプロシージャに渡す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
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
ms.openlocfilehash: 9865e2d7d3786d289add3fa63b3db777317facdf
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>方法 : Visual Basic でプロシージャを別のプロシージャに渡す
この例では、デリゲートを使用してプロシージャを別のプロシージャに渡す方法を示します。  
  
 デリゲートは、その他の種類のように使用できる型[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。 `AddressOf`演算子は、プロシージャの名前に適用する場合は、デリゲート オブジェクトを返します。  
  
 この例で取得される別のプロシージャへの参照を使用できるデリゲート パラメーターを持つプロシージャには、`AddressOf`演算子。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>デリゲートと一致する手順を作成します。  
  
1.  という名前のデリゲートを作成する`MathOperator`です。  
  
     [!code-vb[VbVbalrDelegates&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  という名前のプロシージャを作成する`AddNumbers`パラメーターと戻り値の型と一致する`MathOperator`署名が一致するようにします。  
  
     [!code-vb[VbVbalrDelegates&#2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  という名前のプロシージャを作成する`SubtractNumbers`と一致するシグネチャを持つ`MathOperator`です。  
  
     [!code-vb[VbVbalrDelegates&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  という名前のプロシージャを作成する`DelegateTest`パラメーターとしてデリゲートを取得します。  
  
     この手順への参照を受け入れることができる`AddNumbers`または`SubtractNumbers`、署名が一致するので、`MathOperator`署名します。  
  
     [!code-vb[VbVbalrDelegates&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  という名前のプロシージャを作成する`Test`を呼び出す`DelegateTest`のデリゲートが&1; 回`AddNumbers`をパラメーターとして、もう一度のデリゲートを使用して`SubtractNumbers`をパラメーターとして。  
  
     [!code-vb[VbVbalrDelegates&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     `Test`が呼び出されると、その最初の結果を表示`AddNumbers`に機能している`5`と`3`は 8 です。 結果、`SubtractNumbers`に行動する`9`と`3`が表示されたら、6 であります。  
  
## <a name="see-also"></a>関連項目  
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [方法: デリゲート メソッドを呼び出す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
