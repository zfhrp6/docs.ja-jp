---
title: "方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9abc19ca14cf512deff898f5f20d23870b8b7847
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="4e1e4-102">方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="4e1e4-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="4e1e4-103">この例を使用する方法を示しています、<xref:System.Windows.DataTemplate>と<xref:System.Windows.Style>の外観を指定するオブジェクト、<xref:System.Windows.Controls.ListView>を使用するコントロール、<xref:System.Windows.Controls.GridView>表示モード。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e1e4-104">例</span><span class="sxs-lookup"><span data-stu-id="4e1e4-104">Example</span></span>  
 <span data-ttu-id="4e1e4-105">次の例に示さ<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>列のヘッダーの外観をカスタマイズするオブジェクト、<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="4e1e4-106">次の例は、これらを使用する方法を示しています。<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>を設定するオブジェクト、<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>のプロパティ、<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="4e1e4-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティは、列のセルのコンテンツを定義します。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="4e1e4-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>は 2 つの列ヘッダーの外観をカスタマイズに使用できるいくつかのプロパティののみ、<xref:System.Windows.Controls.GridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="4e1e4-109">詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="4e1e4-110">次の例は、定義する方法を示します、<xref:System.Windows.DataTemplate>内のセルの外観をカスタマイズする、<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="4e1e4-111">次の例は、これを使用する方法を示しています。<xref:System.Windows.DataTemplate>のコンテンツを定義する、<xref:System.Windows.Controls.GridViewColumn>セル。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="4e1e4-112">代わりにこのテンプレートを使用、 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 、前に表示されるプロパティ<xref:System.Windows.Controls.GridViewColumn>例です。</span><span class="sxs-lookup"><span data-stu-id="4e1e4-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="4e1e4-113">参照</span><span class="sxs-lookup"><span data-stu-id="4e1e4-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="4e1e4-114">GridView の概要</span><span class="sxs-lookup"><span data-stu-id="4e1e4-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="4e1e4-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="4e1e4-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="4e1e4-116">ListView の概要</span><span class="sxs-lookup"><span data-stu-id="4e1e4-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
