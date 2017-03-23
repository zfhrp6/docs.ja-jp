---
title: "方法: プロシージャ引数の値が変更された (Visual Basic) を保護する |Microsoft ドキュメント"
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
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
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
ms.openlocfilehash: 6e18f7ceefeec9c1f422d0eae4e727700ebd8b6e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>方法: プロシージャ引数の値が変化しないようにする (Visual Basic)
プロシージャとパラメーターを宣言する場合は、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャのコードに呼び出し元のコードで引数を基になるプログラミング要素への直接の参照を提供します。 これにより、呼び出し元のコードで引数を基になる値を変更するプロシージャです。 場合によってはの呼び出し元のコードは、このような変更から保護します。  
  
 対応するパラメーターを宣言することで、引数を変更から常に保護することができます[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)の手順です。 によって自動的に指定した引数を変更できるようにする場合、それを宣言できます`ByRef`させて、呼び出し元のコードの各呼び出しにおいて引き渡し方法を決定します。 これは、対応する引数を値渡しするかっこで囲むか、参照渡しにかっこで囲まないとで実行します。 詳細については、次を参照してください。[方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)します。  
  
## <a name="example"></a>例  
 次の例では、その要素の配列変数を実行して、操作を&2; つの手順を示します。 `increase`プロシージャが単に各要素に&1; を追加します。 `replace`プロシージャでは、パラメーターに新しい配列を割り当てます`a()`し、各要素に&1; を追加します。 ただし、再割り当てには、呼び出し元のコードで基になる配列変数は変わりません。  
  
 [!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。 配列`n`、参照型では、`replace`引き渡し方法は、そのメンバーを変更できます`ByVal`します。  
  
 2 番目`MsgBox`表示を呼び出して"目後: 11、21、31、41"です。 `n`は`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることで呼び出し元のコードにします。 ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`して呼び出し元のコードに渡されます。 メンバーが変更されたとき`a`、ローカルの配列のみ`k`が影響を受けます。 したがって、`replace`配列の値は増分されません`n`呼び出し元のコードにします。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。 いずれかを指定することをお勧めします[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これは、コードを読みやすくするためです。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)   
 [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md)   
 [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [値と参照渡しの引数を渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)   
 [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
