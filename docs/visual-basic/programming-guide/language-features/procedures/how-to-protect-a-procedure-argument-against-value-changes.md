---
title: '方法: プロシージャ引数の値が変化しないようにする (Visual Basic)'
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
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: d2e131b770d8498a634d946a5900f9b373ca7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651519"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>方法: プロシージャ引数の値が変化しないようにする (Visual Basic)
プロシージャがパラメーターとしてを宣言する場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic は、プロシージャ コード、呼び出し元のコードで引数の基になるこのプログラミング要素への直接参照します。 これにより、プロシージャが呼び出し元のコードで引数の基になる値を変更します。 場合によっては呼び出し元のコードは、このような変更を防ぐためにする可能性があります。  
  
 対応するパラメーターを宣言することで、変更から引数を保護できます常に[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)の手順でします。 によって自動的に指定された引数を変更できるようにする場合は、宣言できる`ByRef`させて、呼び出し元のコードの各呼び出しに渡すメカニズムを確認します。 これは、対応する引数を値渡しをかっこで囲むか、参照渡しをかっこで囲まないとで実行します。 詳細については、次を参照してください。[する方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)です。  
  
## <a name="example"></a>例  
 次の例では、その要素の配列変数を行い、操作を 2 つの手順を示します。 `increase`プロシージャが単に各要素に 1 を追加します。 `replace`プロシージャがパラメーターに新しい配列を割り当てます`a()`し、各要素に 1 を追加します。 ただし、再割り当てでは、呼び出し元のコードに基になる、配列変数には影響しません。  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。 配列`n`、参照型では、`replace`引き渡し方法になっても、そのメンバーを変更できます`ByVal`です。  
  
 2 番目`MsgBox`表示を呼び出して"目後: 41、11、21、31"です。 `n`渡される`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることによって、呼び出し元のコードにします。 ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`呼び出し元のコードで渡される入力します。 メンバーが変更されたとき`a`、ローカルの配列のみ`k`が影響を受けます。 したがって、`replace`配列の値をインクリメントしない`n`呼び出し元のコードにします。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Visual Basic では既定では、引数の値渡しです。 いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これにより、コードを読みやすくします。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)  
 [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
