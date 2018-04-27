---
title: '方法 : ToolStripPanel コントロールを持つ MDI フォームを作成する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8c10c7a74e0562c59708b721f662ab95eadc23b4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="69adb-102">方法 : ToolStripPanel コントロールを持つ MDI フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="69adb-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="69adb-103">上下左右すべての側に <xref:System.Windows.Forms.ToolStrip> コントロールを配置したマルチ ドキュメント インターフェイス (MDI) フォームを作成できます。</span><span class="sxs-lookup"><span data-stu-id="69adb-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69adb-104">例</span><span class="sxs-lookup"><span data-stu-id="69adb-104">Example</span></span>  
 <span data-ttu-id="69adb-105">次のコード例は、ドッキングされた <xref:System.Windows.Forms.ToolStripPanel> コントロールを使用して、4 つの <xref:System.Windows.Forms.ToolStrip> コントロールを MDI ウィンドウの周囲に配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="69adb-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="69adb-106">この例では、<xref:System.Windows.Forms.ToolStripPanel.Join%2A> メソッドにより、<xref:System.Windows.Forms.ToolStrip> コントロールを、対応する <xref:System.Windows.Forms.ToolStripPanel> コントロールにアタッチしています。</span><span class="sxs-lookup"><span data-stu-id="69adb-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69adb-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="69adb-107">Compiling the Code</span></span>  
 <span data-ttu-id="69adb-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="69adb-108">This example requires:</span></span>  
  
-   <span data-ttu-id="69adb-109">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="69adb-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="69adb-110">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="69adb-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="69adb-111">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="69adb-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="69adb-112">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="69adb-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69adb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="69adb-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 <xref:System.Windows.Forms.ToolStripPanel.Join%2A>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="69adb-114">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="69adb-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
