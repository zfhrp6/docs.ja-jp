---
title: '方法: コードのセクションを折りたたんで非表示にする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: f6c272b7ac016258d99873512cb789bba6739727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650856"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>方法: コードのセクションを折りたたんで非表示にする (Visual Basic)
`#Region`ディレクティブでは、折りたたむし、Visual Basic ファイルのコードのセクションでは非表示にすることができます。 `#Region`ディレクティブでは、Visual Studio code エディターを使用する場合は、拡張可能なコードまたは折りたたみのブロックを指定することができます。 選択的にコードを非表示にする機能より管理し、読みやすくに、ファイルになります。 詳細については、「[アウトライン](/visualstudio/ide/outlining)」を参照してください。  
  
 `#Region` ディレクティブのサポート コード ブロック セマンティクス`#If...#End If`です。 つまり、1 つのブロックの開始し、終了します。 別のことはできません。開始と終了は、同じブロック内にある必要があります。 `#Region` ディレクティブは、関数内ではサポートされていません。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>折りたたむし、コードのセクションを非表示にするには  
  
-   間でコードのセクションの配置、`#Region`と`#End Region`ステートメントは、次の例のように。  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region`ブロックを使用できる複数回コード ファイルです。 したがって、ユーザーがプロシージャと、折りたたまれていることができます、クラスの独自のブロックを定義できます。 `#Region` 内で他のブロックをネストすることも`#Region`ブロックします。  
  
    > [!NOTE]
    >  コードを非表示にする場合でも、コンパイルされないおよびには影響しません`#If...#End If`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [アウトライン](/visualstudio/ide/outlining)
