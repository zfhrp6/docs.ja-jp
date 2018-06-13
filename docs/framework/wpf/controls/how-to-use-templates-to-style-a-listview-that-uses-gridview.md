---
title: '方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 481d92d4301401f8ba87c4912cd44b17c5104b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553833"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="db22e-102">方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="db22e-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="db22e-103">この例を使用する方法を示しています、<xref:System.Windows.DataTemplate>と<xref:System.Windows.Style>の外観を指定するオブジェクト、<xref:System.Windows.Controls.ListView>を使用するコントロール、<xref:System.Windows.Controls.GridView>表示モード。</span><span class="sxs-lookup"><span data-stu-id="db22e-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db22e-104">例</span><span class="sxs-lookup"><span data-stu-id="db22e-104">Example</span></span>  
 <span data-ttu-id="db22e-105">次の例に示さ<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>列のヘッダーの外観をカスタマイズするオブジェクト、<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="db22e-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="db22e-106">次の例は、これらを使用する方法を示しています。<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>を設定するオブジェクト、<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>のプロパティ、<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="db22e-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="db22e-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティは、列のセルのコンテンツを定義します。</span><span class="sxs-lookup"><span data-stu-id="db22e-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="db22e-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>は 2 つの列ヘッダーの外観をカスタマイズに使用できるいくつかのプロパティののみ、<xref:System.Windows.Controls.GridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="db22e-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="db22e-109">詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db22e-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="db22e-110">次の例は、定義する方法を示します、<xref:System.Windows.DataTemplate>内のセルの外観をカスタマイズする、<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="db22e-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="db22e-111">次の例は、これを使用する方法を示しています。<xref:System.Windows.DataTemplate>のコンテンツを定義する、<xref:System.Windows.Controls.GridViewColumn>セル。</span><span class="sxs-lookup"><span data-stu-id="db22e-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="db22e-112">代わりにこのテンプレートを使用、 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 、前に表示されるプロパティ<xref:System.Windows.Controls.GridViewColumn>例です。</span><span class="sxs-lookup"><span data-stu-id="db22e-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="db22e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="db22e-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="db22e-114">GridView の概要</span><span class="sxs-lookup"><span data-stu-id="db22e-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="db22e-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="db22e-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="db22e-116">ListView の概要</span><span class="sxs-lookup"><span data-stu-id="db22e-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
