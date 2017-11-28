---
title: "方法 : ToolStripContentPanel にコントロールを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150dd8939077052d4e6d947925c047da0d0432c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a><span data-ttu-id="3bc41-102">方法 : ToolStripContentPanel にコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="3bc41-102">How to: Add a Control to a ToolStripContentPanel</span></span>
<span data-ttu-id="3bc41-103"><xref:System.Windows.Forms.ToolStripContentPanel> に対して、1 つまたは複数のコントロールをプログラムで追加できます。</span><span class="sxs-lookup"><span data-stu-id="3bc41-103">You can programmatically add one or more controls to a <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bc41-104">例</span><span class="sxs-lookup"><span data-stu-id="3bc41-104">Example</span></span>  
 <span data-ttu-id="3bc41-105">次のコード例は、<xref:System.Windows.Forms.RichTextBox> を <xref:System.Windows.Forms.ToolStripContentPanel> に追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3bc41-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.RichTextBox> to a <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3bc41-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3bc41-106">Compiling the Code</span></span>  
 <span data-ttu-id="3bc41-107">このコード例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3bc41-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="3bc41-108">System、System.Data、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="3bc41-108">References to the System, System.Data and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3bc41-109">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細は、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bc41-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3bc41-110">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3bc41-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="3bc41-111">また、「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」または「[[ToolStripContainer タスク] ダイアログ ボックス](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bc41-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc41-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bc41-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="3bc41-113">ToolStripContainer コントロール</span><span class="sxs-lookup"><span data-stu-id="3bc41-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="3bc41-114">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="3bc41-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
