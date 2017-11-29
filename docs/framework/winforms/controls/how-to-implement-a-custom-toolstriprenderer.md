---
title: "方法 : カスタムの ToolStripRenderer を実装する"
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
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd8953d6fe2e4a22e6c3b5fcc294855ef3a1c8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="db2b0-102">方法 : カスタムの ToolStripRenderer を実装する</span><span class="sxs-lookup"><span data-stu-id="db2b0-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="db2b0-103"><xref:System.Windows.Forms.ToolStripRenderer> から派生するクラスを実装することで、<xref:System.Windows.Forms.ToolStrip> コントロールの外観をカスタマイズできます</span><span class="sxs-lookup"><span data-stu-id="db2b0-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="db2b0-104">これによって、<xref:System.Windows.Forms.ToolStripProfessionalRenderer> クラスや <xref:System.Windows.Forms.ToolStripSystemRenderer> クラスで提供される外観とは異なる外観を柔軟に作成できます。</span><span class="sxs-lookup"><span data-stu-id="db2b0-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db2b0-105">例</span><span class="sxs-lookup"><span data-stu-id="db2b0-105">Example</span></span>  
 <span data-ttu-id="db2b0-106">次のコード例は、カスタムの <xref:System.Windows.Forms.ToolStripRenderer> クラスを実装する方法を示しています</span><span class="sxs-lookup"><span data-stu-id="db2b0-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="db2b0-107">この例では、`GridStrip` コントロールでタイルをスライドさせるパズルを実装します。これは、ユーザーがテーブル レイアウト内のタイルを移動して 1 つの画像を作成するパズルです。</span><span class="sxs-lookup"><span data-stu-id="db2b0-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="db2b0-108">カスタムの <xref:System.Windows.Forms.ToolStrip> コントロールで、グリッド レイアウトの <xref:System.Windows.Forms.ToolStripButton> コントロールを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="db2b0-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="db2b0-109">レイアウトには空のセルが 1 つ含まれており、ユーザーは、ドラッグ アンド ドロップ操作を使用することにより、隣接するタイルを空のセルにスライドできます。</span><span class="sxs-lookup"><span data-stu-id="db2b0-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="db2b0-110">ユーザーが移動できるタイルは強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="db2b0-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="db2b0-111">`GridStripRenderer` クラスでは `GridStrip` コントロールの外観を 3 つの点でカスタマイズしています。</span><span class="sxs-lookup"><span data-stu-id="db2b0-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="db2b0-112">`GridStrip` の境界線</span><span class="sxs-lookup"><span data-stu-id="db2b0-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="db2b0-113"><xref:System.Windows.Forms.ToolStripButton> の境界線</span><span class="sxs-lookup"><span data-stu-id="db2b0-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="db2b0-114"><xref:System.Windows.Forms.ToolStripButton> のイメージ</span><span class="sxs-lookup"><span data-stu-id="db2b0-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="db2b0-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="db2b0-115">Compiling the Code</span></span>  
 <span data-ttu-id="db2b0-116">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="db2b0-116">This example requires:</span></span>  
  
-   <span data-ttu-id="db2b0-117">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="db2b0-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="db2b0-118">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db2b0-118">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="db2b0-119">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="db2b0-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="db2b0-120">「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="db2b0-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2b0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="db2b0-121">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="db2b0-122">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="db2b0-122">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
