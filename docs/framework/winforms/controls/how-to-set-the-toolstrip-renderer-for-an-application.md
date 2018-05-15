---
title: '方法 : アプリケーションの ToolStrip レンダラーを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: f4189b19b78ce3cda1981220caa1fce3f2ec708d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="6cd83-102">方法 : アプリケーションの ToolStrip レンダラーを設定する</span><span class="sxs-lookup"><span data-stu-id="6cd83-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="6cd83-103"><xref:System.Windows.Forms.ToolStrip> コントロールの外観を個別にカスタマイズすることも、アプリケーションのすべての <xref:System.Windows.Forms.ToolStrip> コントロールをカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6cd83-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cd83-104">例</span><span class="sxs-lookup"><span data-stu-id="6cd83-104">Example</span></span>  
 <span data-ttu-id="6cd83-105">次のコード例は、カスタムのレンダラーを <xref:System.Windows.Forms.ToolStrip> コントロールと <xref:System.Windows.Forms.MenuStrip> コントロールに選択的に適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6cd83-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="6cd83-106">このコード例を使用するには、アプリケーションをコンパイルして実行し、<xref:System.Windows.Forms.ComboBox> コントロールからのカスタム表示の範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="6cd83-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="6cd83-107">**[適用]** をクリックしてレンダラーを設定します。</span><span class="sxs-lookup"><span data-stu-id="6cd83-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="6cd83-108">カスタム メニュー項目の表示を表示するには、選択、<xref:System.Windows.Forms.MenuStrip>オプションを<xref:System.Windows.Forms.ComboBox>コントロール をクリックして**適用**を開き、**ファイル**メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="6cd83-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="6cd83-109">アプリケーションのすべての <xref:System.Windows.Forms.ToolStrip> コントロールにカスタム レンダラーを適用するよう <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6cd83-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="6cd83-110">カスタム レンダラーを各 <xref:System.Windows.Forms.ToolStrip> コントロールに適用するよう <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6cd83-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6cd83-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6cd83-111">Compiling the Code</span></span>  
 <span data-ttu-id="6cd83-112">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6cd83-112">This example requires:</span></span>  
  
-   <span data-ttu-id="6cd83-113">System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="6cd83-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6cd83-114">Visual Basic または Visual c# のコマンドラインからこの例のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="6cd83-114">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6cd83-115">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="6cd83-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6cd83-116">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd83-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd83-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6cd83-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [<span data-ttu-id="6cd83-118">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="6cd83-118">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
