---
title: '方法 : GridView を実装する ListView で行のスタイルを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 313ead6de45f2a137775adb0ad9aad8bd061c066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555201"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="6595f-102">方法 : GridView を実装する ListView で行のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="6595f-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="6595f-103">この例は、内の行のスタイルを設定する方法を示しています、<xref:System.Windows.Controls.ListView>を実装するコントロール、 <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A>モード。</span><span class="sxs-lookup"><span data-stu-id="6595f-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6595f-104">例</span><span class="sxs-lookup"><span data-stu-id="6595f-104">Example</span></span>  
 <span data-ttu-id="6595f-105">内の行のスタイルを設定することができます、<xref:System.Windows.Controls.ListView>コントロールを設定して、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上、<xref:System.Windows.Controls.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6595f-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="6595f-106">として表されるアイテムのスタイル設定<xref:System.Windows.Controls.ListViewItem>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6595f-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="6595f-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>参照、<xref:System.Windows.Controls.ControlTemplate>行のコンテンツの表示に使用されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6595f-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="6595f-108">次の例の抽出元である完全なサンプルは、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データベースに格納されている楽曲情報のコレクションを表示します。</span><span class="sxs-lookup"><span data-stu-id="6595f-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="6595f-109">データベースの各曲にはレーティングフィールドがあり、このフィールドの値が曲情報の行を表示する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="6595f-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="6595f-110">次の例は、定義する方法を示しています。<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>の、<xref:System.Windows.Controls.ListViewItem>曲のコレクション内の曲を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6595f-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="6595f-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>参照<xref:System.Windows.Controls.ControlTemplate>楽曲情報の行を表示する方法を指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6595f-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="6595f-112">次の例は、<xref:System.Windows.Controls.ControlTemplate>テキスト文字列を追加する`"Strongly Recommended"`行にします。</span><span class="sxs-lookup"><span data-stu-id="6595f-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="6595f-113">このテンプレートが参照されている、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>し、曲の評価がある 5 (5) の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6595f-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="6595f-114"><xref:System.Windows.Controls.ControlTemplate>が含まれています、<xref:System.Windows.Controls.GridViewRowPresenter>で定義されている列の行の内容をレイアウトするオブジェクト、<xref:System.Windows.Controls.GridView>表示モード。</span><span class="sxs-lookup"><span data-stu-id="6595f-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="6595f-115">次の例では定義<xref:System.Windows.Controls.GridView>です。</span><span class="sxs-lookup"><span data-stu-id="6595f-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="6595f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6595f-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="6595f-117">方法トピック</span><span class="sxs-lookup"><span data-stu-id="6595f-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="6595f-118">ListView の概要</span><span class="sxs-lookup"><span data-stu-id="6595f-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="6595f-119">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="6595f-119">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
