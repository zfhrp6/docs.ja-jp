---
title: '方法: プロシージャ引数の値を変更する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: 118dd3389804794801d39e7d67b68ab195bbad3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655838"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>方法: プロシージャ引数の値を変更する (Visual Basic)
プロシージャを呼び出すときに指定する各引数はプロシージャで定義されているパラメーターのいずれかに対応します。 場合によっては、プロシージャのコードは、呼び出し元のコードで引数の基になる値を変更できます。 それ以外の場合に、プロシージャは、引数のローカル コピーのみを変更できます。  
  
 Visual Basic が渡されるすべての引数のローカル コピーを作成して、プロシージャを呼び出すときに[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。 渡された各引数に対して[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic は、プロシージャ コード、呼び出し元のコードで引数の基になるこのプログラミング要素への直接参照します。  
  
 呼び出し元のコードに基になる要素が変更可能な引数が渡される場合`ByRef`、プロシージャ コードは、直接的な参照を使用して、呼び出し元のコード内の要素の値を変更します。  
  
## <a name="changing-the-underlying-value"></a>基になる値を変更します。  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>呼び出し元のコードでプロシージャ引数の基になる値を変更するには  
  
1.  プロシージャ宣言で指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引数に対応するパラメーターです。  
  
2.  呼び出し元のコードでは、変更可能なプログラミング要素を引数として渡します。  
  
3.  呼び出し元のコードで囲まないでください引数、引数リストのかっこでします。  
  
4.  プロシージャのコードでは、呼び出し元のコードに基になる要素に値を代入するのにパラメーターの名前を使用します。  
  
 例を参照してください。 詳しくは、デモについてはします。  
  
## <a name="changing-local-copies"></a>ローカル コピーを変更します。  
 呼び出し元のコードに基になる要素が、変更不可能な要素である場合、または引数が渡される`ByVal`プロシージャが呼び出し元のコードでは、その値を変更できません。 ただし、プロシージャは、このような引数のローカル コピーを変更することができます。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>プロシージャ コードでプロシージャ引数のコピーを変更するには  
  
1.  プロシージャ宣言で指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)引数に対応するパラメーターです。  
  
     - または -  
  
     呼び出し元のコードでは、引数、引数リストのかっこで囲みます。 これは、Visual Basic での値で、引数を渡す場合でも強制的に対応するパラメーターを指定`ByRef`です。  
  
2.  プロシージャのコードでは、引数のローカル コピーに値を代入するのにパラメーターの名前を使用します。 呼び出し元のコードに基になる値は変更されません。  
  
## <a name="example"></a>例  
 次の例では、その要素の配列変数を行い、操作を 2 つの手順を示します。 `increase`プロシージャが単に各要素に 1 を追加します。 `replace`プロシージャがパラメーターに新しい配列を割り当てます`a()`し、各要素に 1 を追加します。  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。 配列`n`、参照型では、`replace`引き渡し方法になっても、そのメンバーを変更できます`ByVal`です。  
  
 2 番目`MsgBox`表示を呼び出して"目後: 101、201、301"です。 `n`渡される`ByRef`、`replace`変数を変更できます`n`呼び出し元のコードと割り当てを新しい配列にします。 `n` 、参照型では、`replace`そのメンバーを変更することもできます。  
  
 プロシージャは、呼び出し元のコードでは、変数自体を変更されないようにできます。 参照してください[する方法: プロシージャ引数の値が変化しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 参照によって変数を渡す際に使用する必要あります、`ByRef`このメカニズムを指定するキーワードです。  
  
 Visual Basic では既定では、引数の値渡しです。 いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これにより、コードを読みやすくします。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し元のコードで引数の基になる値を変更するプロシージャを許可するのには潜在的なリスクは常にします。 この値を変更してを使用する前の有効性を確認する準備を行うことを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
