---
title: '方法 : ToolStripPanel を結合する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: 395f6ad8e0da8deb08c3c537f171865d593c6933
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531844"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="d7bac-102">方法 : ToolStripPanel を結合する</span><span class="sxs-lookup"><span data-stu-id="d7bac-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="d7bac-103">実行時に <xref:System.Windows.Forms.ToolStrip> コントロールを <xref:System.Windows.Forms.ToolStripPanel> に結合でき、これによりマルチ ドキュメント インターフェイス (MDI) アプリケーションの柔軟性を提供します。</span><span class="sxs-lookup"><span data-stu-id="d7bac-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7bac-104">例</span><span class="sxs-lookup"><span data-stu-id="d7bac-104">Example</span></span>  
 <span data-ttu-id="d7bac-105">次のコード例は、<xref:System.Windows.Forms.ToolStrip> コントロールを <xref:System.Windows.Forms.ToolStripPanel> に結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d7bac-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7bac-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d7bac-106">Compiling the Code</span></span>  
 <span data-ttu-id="d7bac-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d7bac-107">This example requires:</span></span>  
  
-   <span data-ttu-id="d7bac-108">System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="d7bac-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d7bac-109">Visual Basic または Visual c# のコマンドラインからこの例のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7bac-109">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d7bac-110">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="d7bac-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="d7bac-111">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7bac-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bac-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7bac-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="d7bac-113">方法: ToolStripPanel を MDI で使用する</span><span class="sxs-lookup"><span data-stu-id="d7bac-113">How to: Use ToolStripPanels for MDI</span></span>](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
