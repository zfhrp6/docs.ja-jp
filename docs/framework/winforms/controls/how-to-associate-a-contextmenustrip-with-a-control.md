---
title: '方法 : ContextMenuStrip をコントロールに関連付ける'
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
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 04b5394a5e5f64228635d7c23df150df9391fa44
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="0f44f-102">方法 : ContextMenuStrip をコントロールに関連付ける</span><span class="sxs-lookup"><span data-stu-id="0f44f-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="0f44f-103">コントロールとショートカット メニューを作成した後、次の手順を使用することによって、ユーザーがコントロールを右クリックした時点で特定のショートカット メニューを表示します。</span><span class="sxs-lookup"><span data-stu-id="0f44f-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="0f44f-104">これらの手順は、<xref:System.Windows.Forms.ContextMenuStrip> を Windows フォームと <xref:System.Windows.Forms.ToolStrip> コントロールに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="0f44f-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="0f44f-105">ContextMenuStrip を Windows フォームに関連付けるには</span><span class="sxs-lookup"><span data-stu-id="0f44f-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="0f44f-106"><xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティを関連付けられている <xref:System.Windows.Forms.ContextMenuStrip> の名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="0f44f-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="0f44f-107">ContextMenuStrip を ToolStrip コントロールに関連付けるには</span><span class="sxs-lookup"><span data-stu-id="0f44f-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="0f44f-108">コントロールの <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティを関連付けられている <xref:System.Windows.Forms.ContextMenuStrip> の名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="0f44f-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f44f-109">例</span><span class="sxs-lookup"><span data-stu-id="0f44f-109">Example</span></span>  
 <span data-ttu-id="0f44f-110">次のコード例では、Windows フォームと <xref:System.Windows.Forms.ToolStrip> を作成して、別の <xref:System.Windows.Forms.ContextMenuStrip> コントロールをそれぞれに関連付けています。</span><span class="sxs-lookup"><span data-stu-id="0f44f-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f44f-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0f44f-111">Compiling the Code</span></span>  
 <span data-ttu-id="0f44f-112">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f44f-112">This example requires:</span></span>  
  
-   <span data-ttu-id="0f44f-113">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="0f44f-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0f44f-114">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f44f-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0f44f-115">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="0f44f-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0f44f-116">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f44f-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f44f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f44f-117">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="0f44f-118">方法: メニュー項目を ContextMenuStrip に追加する</span><span class="sxs-lookup"><span data-stu-id="0f44f-118">How to: Add Menu Items to a ContextMenuStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [<span data-ttu-id="0f44f-119">ContextMenuStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="0f44f-119">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
