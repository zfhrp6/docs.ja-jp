---
title: "方法 : メニューのマージと ToolStrip コントロールを使用して MDI フォームを作成する"
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
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61b218f7485c76e5b3ab98e9ece2d05cd78da885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="1c7ef-102">方法 : メニューのマージと ToolStrip コントロールを使用して MDI フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="1c7ef-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="1c7ef-103"><xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、マルチ ドキュメント インターフェイス (MDI) アプリケーションをサポートし、<xref:System.Windows.Forms.MenuStrip> コントロールはメニューの結合をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="1c7ef-104">MDI フォームは、<xref:System.Windows.Forms.ToolStrip> コントロールもサポートします。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="1c7ef-105">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]に、この機能の広範なサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-105">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="1c7ef-106">「[チュートリアル: メニューのマージと ToolStrip コントロールのある MDI フォームを作成する](http://msdn.microsoft.com/library/ms233676\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](http://msdn.microsoft.com/library/ms233676\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c7ef-107">例</span><span class="sxs-lookup"><span data-stu-id="1c7ef-107">Example</span></span>  
 <span data-ttu-id="1c7ef-108">次のコード例は、<xref:System.Windows.Forms.ToolStripPanel> コントロールを MDI フォームで使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="1c7ef-109">フォームは、子メニューをマージするメニューもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c7ef-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1c7ef-110">Compiling the Code</span></span>  
 <span data-ttu-id="1c7ef-111">このコード例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="1c7ef-112">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1c7ef-113">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-113">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1c7ef-114">また、コードを新しいプロジェクトに貼り付けることにより、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="1c7ef-115">「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c7ef-115">Also sssee [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7ef-116">参照</span><span class="sxs-lookup"><span data-stu-id="1c7ef-116">See Also</span></span>  
 [<span data-ttu-id="1c7ef-117">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="1c7ef-117">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
