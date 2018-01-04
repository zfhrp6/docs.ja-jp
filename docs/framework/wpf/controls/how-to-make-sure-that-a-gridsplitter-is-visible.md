---
title: "方法 : GridSplitter を表示されるようにする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7587a093b2b43856a05693bb785a0465211782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="7f81b-102">方法 : GridSplitter を表示されるようにする</span><span class="sxs-lookup"><span data-stu-id="7f81b-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="7f81b-103">この例を確認する方法を示しています、<xref:System.Windows.Controls.GridSplitter>コントロールは非表示でその他のコントロールによって、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="7f81b-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f81b-104">例</span><span class="sxs-lookup"><span data-stu-id="7f81b-104">Example</span></span>  
 <span data-ttu-id="7f81b-105"><xref:System.Windows.Controls.Panel.Children%2A>の<xref:System.Windows.Controls.Grid>コントロールは、マークアップやコード内に定義された順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f81b-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="7f81b-106"><xref:System.Windows.Controls.GridSplitter>コントロールを非表示にする他のコントロールでの最後の要素として定義する実行されていない場合、<xref:System.Windows.Controls.Panel.Children%2A>コレクションまたはかどうかを指定するその他の制御が大きいほど<xref:System.Windows.Controls.Panel.ZIndexProperty>です。</span><span class="sxs-lookup"><span data-stu-id="7f81b-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="7f81b-107">防ぐために非表示<xref:System.Windows.Controls.GridSplitter>コントロールは、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f81b-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="7f81b-108">確認して<xref:System.Windows.Controls.GridSplitter>コントロールは、最後の<xref:System.Windows.Controls.Panel.Children%2A>に追加された、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="7f81b-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="7f81b-109">次の例は、<xref:System.Windows.Controls.GridSplitter>の最後の要素として、<xref:System.Windows.Controls.Panel.Children%2A>のコレクション、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="7f81b-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="7f81b-110">設定、<xref:System.Windows.Controls.Panel.ZIndexProperty>上、<xref:System.Windows.Controls.GridSplitter>はそれを非表示にするコントロールよりも高くします。</span><span class="sxs-lookup"><span data-stu-id="7f81b-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="7f81b-111">次の例では、<xref:System.Windows.Controls.GridSplitter>制御が大きいほど<xref:System.Windows.Controls.Panel.ZIndexProperty>よりも、<xref:System.Windows.Controls.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7f81b-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="7f81b-112">非表示にはそれ以外の場合、コントロールの余白を設定、<xref:System.Windows.Controls.GridSplitter>できるように、<xref:System.Windows.Controls.GridSplitter>公開されます。</span><span class="sxs-lookup"><span data-stu-id="7f81b-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="7f81b-113">次の例は、オーバーレイのそれ以外の場合は、コントロールと非表示に余白を設定、<xref:System.Windows.Controls.GridSplitter>です。</span><span class="sxs-lookup"><span data-stu-id="7f81b-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="7f81b-114">参照</span><span class="sxs-lookup"><span data-stu-id="7f81b-114">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="7f81b-115">データ バインドに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="7f81b-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
