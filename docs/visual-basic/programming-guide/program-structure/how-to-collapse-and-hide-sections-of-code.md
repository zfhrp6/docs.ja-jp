---
title: "方法: コードのセクションを折りたたんで非表示にする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a31f0c8af9b84e87ebe1e5191d72d19be8340f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>方法: コードのセクションを折りたたんで非表示にする (Visual Basic)
`#Region`ディレクティブを使用すると、折りたたみし、コードのセクションを非表示[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ファイル。 `#Region`ディレクティブを使用する場合は、拡張可能なコードまたは折りたたみのブロックを指定できます、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]コード エディター。 選択的にコードを非表示にする機能より管理し、読みやすくに、ファイルになります。 詳細については、「[アウトライン](/visualstudio/ide/outlining)」を参照してください。  
  
 `#Region`ディレクティブのサポート コード ブロック セマンティクス`#If...#End If`です。 つまり、1 つのブロックの開始し、終了します。 別のことはできません。開始と終了は、同じブロック内にある必要があります。 `#Region`ディレクティブは、関数内ではサポートされていません。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>折りたたむし、コードのセクションを非表示にするには  
  
-   間でコードのセクションの配置、`#Region`と`#End Region`ステートメントは、次の例のように。  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region`ブロックを使用できる複数回コード ファイルです。 したがって、ユーザーがプロシージャと、折りたたまれていることができます、クラスの独自のブロックを定義できます。 `#Region`内で他のブロックをネストすることも`#Region`ブロックします。  
  
    > [!NOTE]
    >  コードを非表示にする場合でも、コンパイルされないおよびには影響しません`#If...#End If`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [アウトライン](/visualstudio/ide/outlining)
