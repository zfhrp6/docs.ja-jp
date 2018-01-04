---
title: "方法 : MDI アプリケーションでメニューの自動マージを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14f9d956763685b5c03419515780ee2a6c3ede7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="a0b13-102">方法 : MDI アプリケーションでメニューの自動マージを設定する</span><span class="sxs-lookup"><span data-stu-id="a0b13-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="a0b13-103">次の手順でマルチ ドキュメント インターフェイス (MDI) アプリケーション内の自動マージを設定するための基本的な手順は、<xref:System.Windows.Forms.MenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="a0b13-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="a0b13-104">メニューの自動マージを設定するには</span><span class="sxs-lookup"><span data-stu-id="a0b13-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="a0b13-105">設定して、MDI 親フォームを作成、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="a0b13-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="a0b13-106">追加、 <xref:System.Windows.Forms.MenuStrip> MDI 親の設定をその<xref:System.Windows.Forms.Form.MainMenuStrip%2A>にプロパティ<xref:System.Windows.Forms.MenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="a0b13-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="a0b13-107">MDI 子フォームを作成し、設定、<xref:System.Windows.Forms.Form.MdiParent%2A>プロパティを親フォームの名前にします。</span><span class="sxs-lookup"><span data-stu-id="a0b13-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="a0b13-108">追加、 <xref:System.Windows.Forms.MenuStrip> MDI 子フォームにします。</span><span class="sxs-lookup"><span data-stu-id="a0b13-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="a0b13-109">子フォームで、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>のプロパティ、<xref:System.Windows.Forms.MenuStrip>に`false`です。</span><span class="sxs-lookup"><span data-stu-id="a0b13-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="a0b13-110">メニュー項目に子フォームの追加<xref:System.Windows.Forms.MenuStrip>親フォームのマージする<xref:System.Windows.Forms.MenuStrip>子フォームがアクティブになったとき。</span><span class="sxs-lookup"><span data-stu-id="a0b13-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="a0b13-111">使用して、<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>子フォームの 項目をメニューのプロパティ<xref:System.Windows.Forms.MenuStrip>を親フォームにマージする方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="a0b13-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b13-112">参照</span><span class="sxs-lookup"><span data-stu-id="a0b13-112">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="a0b13-113">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="a0b13-113">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
