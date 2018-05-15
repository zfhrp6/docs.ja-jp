---
title: '方法 : StatusStrip 内で Spring プロパティを対話的に使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: e3818beb96a7c005ea02bc04e9ea740b28a54707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="c23c5-102">方法 : StatusStrip 内で Spring プロパティを対話的に使用する</span><span class="sxs-lookup"><span data-stu-id="c23c5-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="c23c5-103"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティを使用して、<xref:System.Windows.Forms.StatusStrip> コントロールに <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールを配置できます。</span><span class="sxs-lookup"><span data-stu-id="c23c5-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="c23c5-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティは、<xref:System.Windows.Forms.ToolStripStatusLabel> コントロールが <xref:System.Windows.Forms.StatusStrip> コントロールの使用可能な領域を自動的に入力するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c23c5-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c23c5-105">例</span><span class="sxs-lookup"><span data-stu-id="c23c5-105">Example</span></span>  
 <span data-ttu-id="c23c5-106">次のコード例は、<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティを使用して、<xref:System.Windows.Forms.StatusStrip> コントロールに <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c23c5-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="c23c5-107"><xref:System.Windows.Forms.ToolStripItem.Click> イベント ハンドラーは、exclusive-or (XOR) 演算を実行して、<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティの値を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c23c5-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="c23c5-108">このコード例を使用するコンパイルおよびアプリケーションを実行してをクリックして**中間 (スプリング)** 上、<xref:System.Windows.Forms.StatusStrip>コントロールの値を切り替えるには、<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c23c5-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c23c5-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c23c5-109">Compiling the Code</span></span>  
 <span data-ttu-id="c23c5-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c23c5-110">This example requires:</span></span>  
  
-   <span data-ttu-id="c23c5-111">System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="c23c5-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c23c5-112">Visual Basic または Visual c# のコマンドラインからこの例のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="c23c5-112">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c23c5-113">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="c23c5-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c23c5-114">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23c5-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23c5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c23c5-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="c23c5-116">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="c23c5-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
