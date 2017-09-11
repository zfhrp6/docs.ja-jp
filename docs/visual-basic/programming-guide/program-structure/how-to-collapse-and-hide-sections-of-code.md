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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4dcd5cd5d79629fd008534112cb72d5bcfec476e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="b3a45-102">方法: コードのセクションを折りたたんで非表示にする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3a45-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="b3a45-103">`#Region`ディレクティブを使用すると、内のコードのセクションでは非表示にしたり、折りたたんだり[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b3a45-103">The `#Region` directive enables you to collapse and hide sections of code in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files.</span></span> <span data-ttu-id="b3a45-104">`#Region`ディレクティブを使用する場合は、したり折りたたんだり展開可能なコードのブロックを指定できます、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="b3a45-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] code editor.</span></span> <span data-ttu-id="b3a45-105">選択的にコードを非表示にするようにできるため、ファイルは管理性と、読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="b3a45-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="b3a45-106">詳細については、「[アウトライン](https://docs.microsoft.com/visualstudio/ide/outlining)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3a45-106">For more information, see [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="b3a45-107">`#Region`ディレクティブのサポート コード ブロックのセマンティクス`#If...#End If`します。</span><span class="sxs-lookup"><span data-stu-id="b3a45-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="b3a45-108">つまり、1 つのブロックの開始し、は別の終了ことはできません。開始と終了は、同じブロックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3a45-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="b3a45-109">`#Region`ディレクティブは、関数内ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b3a45-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="b3a45-110">折りたたむし、コードのセクションを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="b3a45-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="b3a45-111">間でコードのセクションに配置、`#Region`と`#End Region`ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b3a45-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     <span data-ttu-id="b3a45-112">[!code-vb[VbVbalrConditionalComp&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b3a45-112">[!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span></span>  
  
     <span data-ttu-id="b3a45-113">`#Region`ブロックは、コード ファイルで複数回使用できる。 したがって、ユーザーが手順およびさらに、折りたたまれていることができます、クラスの独自のブロックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b3a45-113">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="b3a45-114">`#Region`その他のブロックをネストすることも`#Region`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="b3a45-114">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b3a45-115">コンパイルされないは防止されず、使用しないコードを非表示`#If...#End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b3a45-115">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a45-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3a45-116">See Also</span></span>  
 <span data-ttu-id="b3a45-117">[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="b3a45-117">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<span data-ttu-id="b3a45-118"> [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="b3a45-118"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="b3a45-119"> [#If.#Else ディレクティブ。](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="b3a45-119"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="b3a45-120"> [アウトライン](https://docs.microsoft.com/visualstudio/ide/outlining)</span><span class="sxs-lookup"><span data-stu-id="b3a45-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining)</span></span>
