---
title: "方法: コード (Visual Basic) のセクションを非表示にしたり、折りたたんだり |Microsoft ドキュメント"
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
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
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
ms.openlocfilehash: 200a90b6983277d46b6e5c7b27ee4a90ecf88c40
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>方法: コードのセクションを折りたたんで非表示にする (Visual Basic)
`#Region`ディレクティブを使用すると、内のコードのセクションでは非表示にしたり、折りたたんだり[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ファイルです。 `#Region`ディレクティブを使用する場合は、したり折りたたんだり展開可能なコードのブロックを指定できます、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コード エディターです。 選択的にコードを非表示にするようにできるため、ファイルは管理性と、読みやすくします。 詳細については、「[アウトライン](https://docs.microsoft.com/visualstudio/ide/outlining)」を参照してください。  
  
 `#Region`ディレクティブのサポート コード ブロックのセマンティクス`#If...#End If`します。 つまり、1 つのブロックの開始し、は別の終了ことはできません。開始と終了は、同じブロックにする必要があります。 `#Region`ディレクティブは、関数内ではサポートされていません。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>折りたたむし、コードのセクションを非表示にするには  
  
-   間でコードのセクションに配置、`#Region`と`#End Region`ステートメントの例を次に示します。  
  
     [!code-vb[VbVbalrConditionalComp&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region`ブロックは、コード ファイルで複数回使用できる。 したがって、ユーザーが手順およびさらに、折りたたまれていることができます、クラスの独自のブロックを定義できます。 `#Region`その他のブロックをネストすることも`#Region`ブロックします。  
  
    > [!NOTE]
    >  コンパイルされないは防止されず、使用しないコードを非表示`#If...#End If`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)   
 [#If.#Else ディレクティブ。](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [アウトライン](https://docs.microsoft.com/visualstudio/ide/outlining)
