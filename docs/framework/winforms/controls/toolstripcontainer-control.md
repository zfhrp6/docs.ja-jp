---
title: "ToolStripContainer コントロール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms]
- ToolStrip control [Windows Forms], ToolStripContainer
ms.assetid: 378fa5b4-38e1-46f4-8e5c-d0c19dcd0200
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 763ce6d47b0fe40eb2d27b2e062d46cfd9e1b8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="toolstripcontainer-control"></a><span data-ttu-id="74f77-102">ToolStripContainer コントロール</span><span class="sxs-lookup"><span data-stu-id="74f77-102">ToolStripContainer Control</span></span>
<span data-ttu-id="74f77-103"><xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolStripContainer> の使用による、ビルトイン ラフティング (ドッキングされているときに、ツールの領域内の水平または垂直のスペースを共有) を備えています。</span><span class="sxs-lookup"><span data-stu-id="74f77-103"><xref:System.Windows.Forms.ToolStrip> controls feature built-in rafting (sharing of horizontal or vertical space within the tool area when docked) by using the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 <span data-ttu-id="74f77-104">このセクションのトピックでは、<xref:System.Windows.Forms.ToolStripContainer> の機能をアプリケーションに組み込むときに使用できる概念および手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74f77-104">The topics in this section describe the concepts and techniques that you can use to build <xref:System.Windows.Forms.ToolStripContainer> features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74f77-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="74f77-105">In This Section</span></span>  
 [<span data-ttu-id="74f77-106">ToolStripContainer コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="74f77-106">ToolStripContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control-overview.md)  
 <span data-ttu-id="74f77-107">Windows フォームの <xref:System.Windows.Forms.ToolStripContainer> コントロールの目的および中心となる概念を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="74f77-107">Provides topics that describe the purpose and main concepts of the Windows Forms <xref:System.Windows.Forms.ToolStripContainer> control.</span></span>  
  
 [<span data-ttu-id="74f77-108">方法: フォームに ToolStripContainer を追加する</span><span class="sxs-lookup"><span data-stu-id="74f77-108">How to: Add a ToolStripContainer to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-toolstripcontainer-to-a-form.md)  
 <span data-ttu-id="74f77-109"><xref:System.Windows.Forms.ToolStripContainer> のアプリケーションへの追加と、<xref:System.Windows.Forms.ToolStripContainer> の特定のパネルへのコントロールの追加を示します。</span><span class="sxs-lookup"><span data-stu-id="74f77-109">Demonstrates adding a <xref:System.Windows.Forms.ToolStripContainer> to an application and adding a control to a specific panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [<span data-ttu-id="74f77-110">方法: ToolStripContentPanel にコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="74f77-110">How to: Add a Control to a ToolStripContentPanel</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-toolstripcontentpanel.md)  
 <span data-ttu-id="74f77-111"><xref:System.Windows.Forms.ToolStripContentPanel> へのコントロールの追加を示します。</span><span class="sxs-lookup"><span data-stu-id="74f77-111">Demonstrates adding a control to the <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="74f77-112">参照</span><span class="sxs-lookup"><span data-stu-id="74f77-112">Reference</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <span data-ttu-id="74f77-113"><xref:System.Windows.Forms.ToolStripContainer> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="74f77-113">Provides reference documentation for the <xref:System.Windows.Forms.ToolStripContainer> control.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 <span data-ttu-id="74f77-114"><xref:System.Windows.Forms.ToolStripContainer> コントロールの <xref:System.Windows.Forms.ToolStripContentPanel> のリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="74f77-114">Provides reference documentation for the <xref:System.Windows.Forms.ToolStripContentPanel> of a <xref:System.Windows.Forms.ToolStripContainer> control.</span></span>  
  
 <span data-ttu-id="74f77-115">参照してください[ToolStripContainer タスク ダイアログ ボックス](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="74f77-115">Also see [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="74f77-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="74f77-116">Related Sections</span></span>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 <span data-ttu-id="74f77-117"><xref:System.Windows.Forms.ToolStripPanel> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="74f77-117">Provides reference documentation for the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f77-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="74f77-118">See Also</span></span>  
 [<span data-ttu-id="74f77-119">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="74f77-119">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
