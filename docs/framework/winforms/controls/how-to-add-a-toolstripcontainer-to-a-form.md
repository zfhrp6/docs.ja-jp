---
title: '方法 : フォームに ToolStripContainer を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 7e9b12505c0e80cdafe56967321f46d41305b799
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524681"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="b844c-102">方法 : フォームに ToolStripContainer を追加する</span><span class="sxs-lookup"><span data-stu-id="b844c-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="b844c-103">プログラムで Windows フォームに <xref:System.Windows.Forms.ToolStripContainer> を追加し、そこにコントロールを配置できます。</span><span class="sxs-lookup"><span data-stu-id="b844c-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b844c-104">例</span><span class="sxs-lookup"><span data-stu-id="b844c-104">Example</span></span>  
 <span data-ttu-id="b844c-105">次のコード例は、Windows フォームに <xref:System.Windows.Forms.ToolStripContainer> および <xref:System.Windows.Forms.ToolStrip> を追加する方法、<xref:System.Windows.Forms.ToolStrip> に項目を追加する方法、<xref:System.Windows.Forms.ToolStripContainer> の <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> に <xref:System.Windows.Forms.ToolStrip> を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b844c-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b844c-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b844c-106">Compiling the Code</span></span>  
 <span data-ttu-id="b844c-107">このコード例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b844c-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="b844c-108">System.Drawing、System.Text、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="b844c-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b844c-109">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="b844c-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b844c-110">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="b844c-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b844c-111">また、「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」または「[[ToolStripContainer タスク] ダイアログ ボックス](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="b844c-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b844c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b844c-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="b844c-113">ToolStripContainer コントロール</span><span class="sxs-lookup"><span data-stu-id="b844c-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="b844c-114">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="b844c-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
