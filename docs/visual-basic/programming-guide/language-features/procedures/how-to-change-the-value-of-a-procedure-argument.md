---
title: "方法: プロシージャ引数 (Visual Basic) の値を変更 |Microsoft ドキュメント"
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
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
ms.openlocfilehash: 6c42a50b75bcc70ae0a3f70771b9e1f85626004b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>方法: プロシージャ引数の値を変更する (Visual Basic)
プロシージャを呼び出すときに指定する各引数はプロシージャで定義されているパラメーターの&1; つに対応します。 場合によっては、プロシージャのコードは呼び出し元のコードで引数を基になる値を変更できます。 それ以外の場合で、手順は、引数のローカル コピーのみを変更できます。  
  
 プロシージャを呼び出すときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]渡される引数は、すべてのローカル コピーを作成[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。 渡された各引数に対して[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャのコードに呼び出し元のコードで引数を基になるプログラミング要素への直接の参照を提供します。  
  
 呼び出し元のコードに基になる要素が変更可能な引数が渡された場合`ByRef`プロシージャのコードが直接参照を使用して呼び出し元のコードに、要素の値に変更します。  
  
## <a name="changing-the-underlying-value"></a>基になる値を変更します。  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>呼び出し元のコードでプロシージャ引数の基になる値を変更するには  
  
1.  プロシージャの宣言で指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引数に対応するパラメーターです。  
  
2.  呼び出し元のコードで変更可能なプログラミング要素を引数として渡します。  
  
3.  呼び出し元のコードで囲む必要はありません引数リスト内のかっこで囲まれた引数です。  
  
4.  プロシージャのコードでは、呼び出し元のコードで基になる要素に値を代入するのにパラメーター名を使用します。  
  
 この例を参照してくださいデモのさらに下です。  
  
## <a name="changing-local-copies"></a>ローカル コピーを変更します。  
 呼び出し元のコード内の基になる要素が、変更不可能な要素である場合、または引数が渡された場合`ByVal`プロシージャが呼び出し元のコードにはその値を変更できません。 ただし、プロシージャは、このような引数のローカル コピーを変更することができます。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>プロシージャ コード内でプロシージャの引数のコピーを変更するには  
  
1.  プロシージャの宣言で指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)引数に対応するパラメーターです。  
  
     または  
  
     呼び出し元のコードでは、引数、引数リストのかっこで囲みます。 これにより、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]場合でも、対応するパラメーターを指定値で、引数を渡す`ByRef`します。  
  
2.  プロシージャ コード内でパラメーター名を使用して、引数のローカル コピーに値を代入します。 呼び出し元のコードで基になる値は変更されません。  
  
## <a name="example"></a>例  
 次の例では、その要素の配列変数を実行して、操作を&2; つの手順を示します。 `increase`プロシージャが単に各要素に&1; を追加します。 `replace`プロシージャでは、パラメーターに新しい配列を割り当てます`a()`し、各要素に&1; を追加します。  
  
 [!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。 配列`n`、参照型では、`replace`引き渡し方法は、そのメンバーを変更できます`ByVal`します。  
  
 2 番目`MsgBox`表示を呼び出して"目後: 101、201、301"です。 `n`は`ByRef`、`replace`変数を変更できます`n`呼び出し元のコードと割り当てを新しい配列にします。 `n` 、参照型では、`replace`そのメンバーを変更することもできます。  
  
 プロシージャを防ぐため、呼び出し元のコードでは、変数自体を変更できないことができます。 参照してください[方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 参照渡しで変数を渡す場合は、使用、`ByRef`キーワードを明示的に指定します。  
  
 既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。 いずれかを指定することをお勧めします[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これは、コードを読みやすくするためです。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し元のコードで引数を基になる値を変更する手順を可能にすることは潜在的なリスクは常にします。 この値を変更し、使用する前に有効性を確認する準備を期待することを確認します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)   
 [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md)   
 [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [値と参照渡しの引数を渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
