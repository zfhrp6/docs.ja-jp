---
title: '方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する'
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
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8b2d67f38f9533e60575b45df011f50e7ec091d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="bcbfb-102">方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="bcbfb-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="bcbfb-103"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> 型から派生する独自のクラスを記述することで、アプリケーションの <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観と動作 (操作性) を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="bcbfb-104">Visual Studio では、この機能の広範なサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="bcbfb-105">「[チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcbfb-106">例</span><span class="sxs-lookup"><span data-stu-id="bcbfb-106">Example</span></span>  
 <span data-ttu-id="bcbfb-107">次のコード例は、使用する方法を示します<xref:System.Windows.Forms.ToolStrip>を模倣した複合コントロールを作成するコントロール、**ナビゲーション ウィンドウ**Microsoft® Outlook® によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bcbfb-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bcbfb-108">Compiling the Code</span></span>  
 <span data-ttu-id="bcbfb-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-109">This example requires:</span></span>  
  
-   <span data-ttu-id="bcbfb-110">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bcbfb-111">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bcbfb-112">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="bcbfb-113">「[チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成](http://msdn.microsoft.com/library/ms233664\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcbfb-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbfb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcbfb-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="bcbfb-115">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="bcbfb-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="bcbfb-116">方法: フォームに標準メニュー項目を追加する</span><span class="sxs-lookup"><span data-stu-id="bcbfb-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
