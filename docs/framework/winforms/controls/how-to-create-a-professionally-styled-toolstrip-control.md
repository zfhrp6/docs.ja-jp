---
title: "方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する"
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5f026092131b4dee6b432a175d5bcbe353b20c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="6eaed-102">方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="6eaed-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="6eaed-103"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> 型から派生する独自のクラスを記述することで、アプリケーションの <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観と動作 (操作性) を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="6eaed-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="6eaed-104">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]に、この機能の広範なサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="6eaed-104">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="6eaed-105">「[チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eaed-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eaed-106">例</span><span class="sxs-lookup"><span data-stu-id="6eaed-106">Example</span></span>  
 <span data-ttu-id="6eaed-107">次のコード例は、使用する方法を示します<xref:System.Windows.Forms.ToolStrip>を模倣した複合コントロールを作成するコントロール、**ナビゲーション ウィンドウ**Microsoft® Outlook® によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="6eaed-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6eaed-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6eaed-108">Compiling the Code</span></span>  
 <span data-ttu-id="6eaed-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6eaed-109">This example requires:</span></span>  
  
-   <span data-ttu-id="6eaed-110">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="6eaed-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6eaed-111">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eaed-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6eaed-112">また、コードを新しいプロジェクトに貼り付けることにより、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6eaed-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6eaed-113">「[チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成](http://msdn.microsoft.com/library/ms233664\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eaed-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eaed-114">参照</span><span class="sxs-lookup"><span data-stu-id="6eaed-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="6eaed-115">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="6eaed-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="6eaed-116">方法: フォームに標準メニュー項目を追加する</span><span class="sxs-lookup"><span data-stu-id="6eaed-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
