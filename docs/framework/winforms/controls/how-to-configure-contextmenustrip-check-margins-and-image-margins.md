---
title: '方法 : ContextMenuStrip のチェックの余白とイメージの余白を設定する'
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
- context menus [Windows Forms], configuring check and image margins
- ContextMenuStrips [Windows Forms], configuring check and image margins
- margins [Windows Forms], setting check and image in Windows Forms ContextMenuStrips
ms.assetid: 3391c4c2-0c9e-4aa4-9492-13ff7644bdf2
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de047adfee28a6c92819695678201558959b1639
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-contextmenustrip-check-margins-and-image-margins"></a><span data-ttu-id="27de5-102">方法 : ContextMenuStrip のチェックの余白とイメージの余白を設定する</span><span class="sxs-lookup"><span data-stu-id="27de5-102">How to: Configure ContextMenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="27de5-103"><xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> プロパティと <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> プロパティをさまざまな組み合わせで設定することにより、<xref:System.Windows.Forms.ContextMenuStrip> をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="27de5-103">You can customize a <xref:System.Windows.Forms.ContextMenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27de5-104">例</span><span class="sxs-lookup"><span data-stu-id="27de5-104">Example</span></span>  
 <span data-ttu-id="27de5-105">次のコード例では、<xref:System.Windows.Forms.ContextMenuStrip> のチェックの余白とイメージの余白をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27de5-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check and image margins.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27de5-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="27de5-106">Compiling the Code</span></span>  
 <span data-ttu-id="27de5-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="27de5-107">This example requires:</span></span>  
  
-   <span data-ttu-id="27de5-108">System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="27de5-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="27de5-109">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="27de5-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="27de5-110">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="27de5-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="27de5-111">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="27de5-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27de5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="27de5-112">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="27de5-113">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="27de5-113">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="27de5-114">方法: ContextMenuStrip コントロールでチェックの余白とイメージの余白を有効にする</span><span class="sxs-lookup"><span data-stu-id="27de5-114">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
