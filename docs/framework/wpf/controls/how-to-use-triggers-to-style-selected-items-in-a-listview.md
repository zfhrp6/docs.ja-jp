---
title: "方法 : トリガーを使用して、ListView で選択された項目のスタイルを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f8965ee524d6a5cb03a54ac07d8889ff9801440
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="b1078-102">方法 : トリガーを使用して、ListView で選択された項目のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="b1078-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="b1078-103">この例は、定義する方法を示します<xref:System.Windows.Style.Triggers%2A>の<xref:System.Windows.Controls.ListViewItem>コントロールできるように時のプロパティの値、 <xref:System.Windows.Controls.ListViewItem> 、変更、<xref:System.Windows.Style>の<xref:System.Windows.Controls.ListViewItem>対応する変更点です。</span><span class="sxs-lookup"><span data-stu-id="b1078-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1078-104">例</span><span class="sxs-lookup"><span data-stu-id="b1078-104">Example</span></span>  
 <span data-ttu-id="b1078-105">場合は、<xref:System.Windows.Style>の<xref:System.Windows.Controls.ListViewItem>プロパティの変更に応答を変更するには、定義<xref:System.Windows.Style.Triggers%2A>の<xref:System.Windows.Style>を変更します。</span><span class="sxs-lookup"><span data-stu-id="b1078-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="b1078-106">次の例では定義、<xref:System.Windows.Trigger>が設定された、<xref:System.Windows.Controls.Control.Foreground%2A>プロパティを<xref:System.Windows.Media.Brushes.Blue%2A>し、変更、<xref:System.Windows.FrameworkElement.Cursor%2A>を表示する、<xref:System.Windows.Input.CursorType.Hand>ときに、<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティに対する変更を`true`です。</span><span class="sxs-lookup"><span data-stu-id="b1078-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="b1078-107">次の例では定義、<xref:System.Windows.MultiTrigger>が設定された、<xref:System.Windows.Controls.Control.Foreground%2A>のプロパティ、<xref:System.Windows.Controls.ListViewItem>に<xref:System.Windows.Media.Brushes.Yellow%2A>ときに、<xref:System.Windows.Controls.ListViewItem>選択された項目し、キーボード フォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="b1078-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="b1078-108">参照</span><span class="sxs-lookup"><span data-stu-id="b1078-108">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="b1078-109">方法トピック</span><span class="sxs-lookup"><span data-stu-id="b1078-109">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="b1078-110">ListView の概要</span><span class="sxs-lookup"><span data-stu-id="b1078-110">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="b1078-111">GridView の概要</span><span class="sxs-lookup"><span data-stu-id="b1078-111">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
