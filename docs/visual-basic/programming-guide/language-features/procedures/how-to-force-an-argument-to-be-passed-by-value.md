---
title: '方法: 引数の値渡しを強制する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: adc58c34150030eb0fc82050576bfecc453e21ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651078"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>方法: 引数の値渡しを強制する (Visual Basic)
プロシージャ宣言では、引き渡し方法を決定します。 パラメーターが宣言されている場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、参照によって、対応する引数を渡す Visual Basic が必要です。 これにより、呼び出し元のコードで引数の基になるプログラミング要素の値を変更する手順です。 このような変更を基になる要素を保護する場合は、オーバーライドできます、`ByRef`引き渡し方法の手順では引数の名前をかっこで囲んだ呼び出します。 このかっこは、呼び出しで引数リストを囲むかっこだけでなく、します。  
  
 呼び出し元のコードがオーバーライドすることはできません、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)メカニズムです。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>引数の値渡しを強制するには  
  
-   対応するパラメーターが宣言されている場合`ByVal`の手順では、追加の手順を実行する必要はありません。 Visual Basic は、既に、値渡しの引数が必要です。  
  
-   対応するパラメーターが宣言されている場合`ByRef`の手順で、プロシージャ呼び出しでのかっこ内に引数を囲みます。  
  
## <a name="example"></a>例  
 次の例よりも優先、`ByRef`パラメーター宣言します。 強制する呼び出しで`ByVal`かっこの 2 つのレベルに注意してください。  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 ときに`str`引数リスト内で余分なかっこで囲まれて、`setNewString`プロシージャが呼び出し元のコードでは、その値を変更ことはできませんと`MsgBox`ByVal を越えた場合は、「を置換できません」が表示されます。 ときに`str`囲まれていない追加のかっこ内にプロシージャを変更できますが、および`MsgBox`「inString 引数の新しい値はこのです」が表示されます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 参照によって変数を渡す際に使用する必要あります、`ByRef`このメカニズムを指定するキーワードです。  
  
 Visual Basic では既定では、引数の値渡しです。 いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これにより、コードを読みやすくします。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 プロシージャ パラメーターを宣言する場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、正しいコードの実行は呼び出し元のコードに基になる要素を変更することに依存しています。 呼び出し元のコードは、引数をかっこで囲んででこの呼び出し元のメカニズムをオーバーライドする場合、または変更できない引数を渡す場合は、プロシージャは、基になる要素を変更できません。 これにより、呼び出し元のコードで予期しない結果が生じる可能性があります。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し元のコードで引数の基になる値を変更するプロシージャを許可するのには潜在的なリスクは常にします。 この値を変更してを使用する前の有効性を確認する準備を行うことを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)  
 [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
