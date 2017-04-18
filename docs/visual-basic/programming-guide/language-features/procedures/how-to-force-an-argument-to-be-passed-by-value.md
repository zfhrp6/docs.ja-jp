---
title: "方法: 引数 (Visual Basic) を値渡しを強制する |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
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
ms.openlocfilehash: eea3466534f1797170ae4bc72afbcba899929911
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>方法: 引数の値渡しを強制する (Visual Basic)
プロシージャの宣言では、引き渡し方法を決定します。 パラメーターが宣言されている場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]参照によって、対応する引数を渡すが必要です。 これにより、呼び出し元のコードで引数を基になるプログラミングの要素の値を変更する手順です。 このような変更を基になる要素を保護する場合をオーバーライドできます、`ByRef`引き渡し方法の手順で呼び出す引数の名前をかっこで囲みます。 このかっこは、呼び出しで引数リストを囲むかっこに追加します。  
  
 呼び出し元のコードを上書きできません、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)メカニズムです。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>引数の値渡しを強制するには  
  
-   対応するパラメーターが宣言されている場合`ByVal`の手順では、追加の手順を実行する必要はありません。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]既に、引数の値渡しを期待しています。  
  
-   対応するパラメーターが宣言されている場合`ByRef`の手順でプロシージャの呼び出しにかっこで囲まれた引数を囲みます。  
  
## <a name="example"></a>例  
 次の例では、オーバーライド、`ByRef`パラメーター宣言します。 強制的の呼び出しで`ByVal`かっこの&2; つのレベルに注意してください。  
  
 [!code-vb[VbVbcnProcedures&#39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&40;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 `str`引数リスト内で余分なかっこで囲まれた、`setNewString`プロシージャが呼び出し元のコードにはその値を変更できませんと`MsgBox`ByVal が渡された場合は、「を置き換えることはできません」が表示されます。 `str`囲まれていない余分なかっこで囲まれた、プロシージャを変更できますが、および`MsgBox`「inString 引数の新しい値はこれです。」が表示されます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 参照渡しで変数を渡す場合は、使用、`ByRef`キーワードを明示的に指定します。  
  
 既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。 いずれかを指定することをお勧めします[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これは、コードを読みやすくするためです。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 プロシージャ パラメーターを宣言する場合は、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)コードの適切な実行は呼び出し元のコードの基になる要素に変更できることを依存している可能性があります。 呼び出し元のコードは、引数をかっこで囲んででこの呼び出し元のメカニズムをオーバーライドする場合、または変更できない引数を渡す場合は、プロシージャは、基になる要素を変更できません。 これは、呼び出し元のコードで予期しない結果となる可能性があります。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し元のコードで引数を基になる値を変更する手順を可能にすることは潜在的なリスクは常にします。 この値を変更し、使用する前に有効性を確認する準備を期待することを確認します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)   
 [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md)   
 [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [値と参照渡しの引数を渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)   
 [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
