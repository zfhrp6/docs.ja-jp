---
title: "方法 : CheckBox を持つ ListViewItem を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6ebb3671dcc65d690fde5d4796c9034553eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="1e0f6-102">方法 : CheckBox を持つ ListViewItem を作成する</span><span class="sxs-lookup"><span data-stu-id="1e0f6-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="1e0f6-103">この例は、の列を表示する方法を示しています。<xref:System.Windows.Controls.CheckBox>コントロールで、<xref:System.Windows.Controls.ListView>を使用するコントロール、<xref:System.Windows.Controls.GridView>です。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e0f6-104">例</span><span class="sxs-lookup"><span data-stu-id="1e0f6-104">Example</span></span>  
 <span data-ttu-id="1e0f6-105">含む列を作成する<xref:System.Windows.Controls.CheckBox>コントロールで、 <xref:System.Windows.Controls.ListView>、作成、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.CheckBox>です。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="1e0f6-106">設定して、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>の<xref:System.Windows.Controls.GridViewColumn>を<xref:System.Windows.DataTemplate>です。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="1e0f6-107">次の例は、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.CheckBox>です。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="1e0f6-108">例では、バインド、<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>のプロパティ、<xref:System.Windows.Controls.CheckBox>を<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>のプロパティの値、<xref:System.Windows.Controls.ListViewItem>含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="1e0f6-109">したがって、<xref:System.Windows.Controls.ListViewItem>を格納している、<xref:System.Windows.Controls.CheckBox>が選択されている、<xref:System.Windows.Controls.CheckBox>がチェックします。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="1e0f6-110">次の例は、の列を作成する方法を示しています。<xref:System.Windows.Controls.CheckBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="1e0f6-111">、、の例のセットの列に設定、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>のプロパティ、<xref:System.Windows.Controls.GridViewColumn>を、<xref:System.Windows.DataTemplate>です。</span><span class="sxs-lookup"><span data-stu-id="1e0f6-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="1e0f6-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e0f6-112">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="1e0f6-113">ListView の概要</span><span class="sxs-lookup"><span data-stu-id="1e0f6-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="1e0f6-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="1e0f6-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="1e0f6-115">GridView の概要</span><span class="sxs-lookup"><span data-stu-id="1e0f6-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
