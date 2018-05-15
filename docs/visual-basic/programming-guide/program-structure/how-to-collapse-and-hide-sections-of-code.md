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
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="cf051-102">方法: コードのセクションを折りたたんで非表示にする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf051-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="cf051-103">`#Region`ディレクティブでは、折りたたむし、Visual Basic ファイルのコードのセクションでは非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf051-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="cf051-104">`#Region`ディレクティブでは、Visual Studio code エディターを使用する場合は、拡張可能なコードまたは折りたたみのブロックを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="cf051-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="cf051-105">選択的にコードを非表示にする機能より管理し、読みやすくに、ファイルになります。</span><span class="sxs-lookup"><span data-stu-id="cf051-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="cf051-106">詳細については、「[アウトライン](/visualstudio/ide/outlining)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf051-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="cf051-107">`#Region` ディレクティブのサポート コード ブロック セマンティクス`#If...#End If`です。</span><span class="sxs-lookup"><span data-stu-id="cf051-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="cf051-108">つまり、1 つのブロックの開始し、終了します。 別のことはできません。開始と終了は、同じブロック内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf051-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="cf051-109">`#Region` ディレクティブは、関数内ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cf051-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="cf051-110">折りたたむし、コードのセクションを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="cf051-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="cf051-111">間でコードのセクションの配置、`#Region`と`#End Region`ステートメントは、次の例のように。</span><span class="sxs-lookup"><span data-stu-id="cf051-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="cf051-112">`#Region`ブロックを使用できる複数回コード ファイルです。 したがって、ユーザーがプロシージャと、折りたたまれていることができます、クラスの独自のブロックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="cf051-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="cf051-113">`#Region` 内で他のブロックをネストすることも`#Region`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="cf051-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf051-114">コードを非表示にする場合でも、コンパイルされないおよびには影響しません`#If...#End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="cf051-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf051-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf051-115">See Also</span></span>  
 [<span data-ttu-id="cf051-116">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="cf051-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="cf051-117">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="cf051-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="cf051-118">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="cf051-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="cf051-119">アウトライン</span><span class="sxs-lookup"><span data-stu-id="cf051-119">Outlining</span></span>](/visualstudio/ide/outlining)
