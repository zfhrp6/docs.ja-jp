---
title: '方法 : ToolStrip の項目を動的に追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 9db50c1966d7a6c2baa344857b03e568dbe2a2ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526322"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="56101-102">方法 : ToolStrip の項目を動的に追加する</span><span class="sxs-lookup"><span data-stu-id="56101-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="56101-103">メニューが開くときに <xref:System.Windows.Forms.ToolStrip> コントロールのメニュー項目コレクションを動的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="56101-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56101-104">例</span><span class="sxs-lookup"><span data-stu-id="56101-104">Example</span></span>  
 <span data-ttu-id="56101-105">次のコード例は、<xref:System.Windows.Forms.ContextMenuStrip> コントロールに項目を動的に追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="56101-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="56101-106">この例は、フォーム上の 3 つの異なるコントロールに同じ <xref:System.Windows.Forms.ContextMenuStrip> を再利用する方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="56101-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="56101-107">この例では、<xref:System.Windows.Forms.ToolStripDropDown.Opening> イベント ハンドラーがメニュー項目コレクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="56101-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="56101-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> イベント ハンドラーは、<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> プロパティと <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> プロパティを調べて、ソース管理を示す <xref:System.Windows.Forms.ToolStripItem> を追加します。</span><span class="sxs-lookup"><span data-stu-id="56101-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56101-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="56101-109">Compiling the Code</span></span>  
 <span data-ttu-id="56101-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="56101-110">This example requires:</span></span>  
  
-   <span data-ttu-id="56101-111">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="56101-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="56101-112">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="56101-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="56101-113">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="56101-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56101-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="56101-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 [<span data-ttu-id="56101-115">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="56101-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
