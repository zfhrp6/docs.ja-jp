---
title: '方法 : MenuStrip のチェックの余白とイメージの余白を設定する'
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
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3ee49ec226c99a28322822983fa086954f0ef3e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="2794f-102">方法 : MenuStrip のチェックの余白とイメージの余白を設定する</span><span class="sxs-lookup"><span data-stu-id="2794f-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="2794f-103"><xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> プロパティと <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> プロパティをさまざまな組み合わせで設定することにより、<xref:System.Windows.Forms.MenuStrip> をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="2794f-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2794f-104">例</span><span class="sxs-lookup"><span data-stu-id="2794f-104">Example</span></span>  
 <span data-ttu-id="2794f-105">次のコード例では、<xref:System.Windows.Forms.ContextMenuStrip> のチェックの余白とイメージの余白をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2794f-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="2794f-106">手順は <xref:System.Windows.Forms.ContextMenuStrip> または <xref:System.Windows.Forms.MenuStrip> と同じです。</span><span class="sxs-lookup"><span data-stu-id="2794f-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2794f-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2794f-107">Compiling the Code</span></span>  
 <span data-ttu-id="2794f-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2794f-108">This example requires:</span></span>  
  
-   <span data-ttu-id="2794f-109">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="2794f-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2794f-110">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="2794f-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2794f-111">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="2794f-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="2794f-112">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="2794f-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2794f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2794f-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="2794f-114">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="2794f-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="2794f-115">方法: ContextMenuStrip コントロールでチェックの余白とイメージの余白を有効にする</span><span class="sxs-lookup"><span data-stu-id="2794f-115">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
