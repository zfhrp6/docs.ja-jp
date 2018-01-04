---
title: "方法: DataGrid コントロールに行の詳細を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f65eb9e916fad83deb1476c1d8f0def4981d08d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="9d444-102">方法: DataGrid コントロールに行の詳細を追加する</span><span class="sxs-lookup"><span data-stu-id="9d444-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="9d444-103">使用する場合、<xref:System.Windows.Controls.DataGrid>コントロール、行の詳細セクションを追加することによってデータの表示をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="9d444-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="9d444-104">行の詳細セクションを追加するには、必要に応じて表示されるか、折りたたまれる、テンプレート内のデータをグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="9d444-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="9d444-105">行の詳細を追加するなど、<xref:System.Windows.Controls.DataGrid>内の各行のデータの概要のみを表示する、<xref:System.Windows.Controls.DataGrid>が、ユーザーが行を選択したときに、他のデータ フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d444-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="9d444-106">行の詳細セクション内のテンプレートを定義する、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9d444-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="9d444-107">次の図は、行の詳細セクションの例を示します。</span><span class="sxs-lookup"><span data-stu-id="9d444-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="9d444-108">![行の詳細を表示する DataGrid](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="9d444-108">![DataGrid shown with row details](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="9d444-109">リソースとして、または、インライン XAML としては、行の詳細テンプレートを定義します。</span><span class="sxs-lookup"><span data-stu-id="9d444-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="9d444-110">次の手順では、両方の方法が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d444-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="9d444-111">リソースとして追加されるデータ テンプレートは、テンプレートを再作成しなくても、プロジェクト全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d444-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="9d444-112">インライン XAML からのみアクセス コントロールが定義されているように追加されるデータ テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="9d444-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="9d444-113">インライン XAML を使用して行の詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="9d444-113">To display row details by using inline XAML</span></span>  
  
1.  <span data-ttu-id="9d444-114">作成、<xref:System.Windows.Controls.DataGrid>データ ソースからデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d444-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="9d444-115"><xref:System.Windows.Controls.DataGrid> 要素に、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="9d444-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3.  <span data-ttu-id="9d444-116">作成、<xref:System.Windows.DataTemplate>行の詳細セクションの外観を定義します。</span><span class="sxs-lookup"><span data-stu-id="9d444-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="9d444-117">次の XAML 示します、<xref:System.Windows.Controls.DataGrid>および定義する方法、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>インラインです。</span><span class="sxs-lookup"><span data-stu-id="9d444-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="9d444-118"><xref:System.Windows.Controls.DataGrid>表示 3 つの値の各の行の 3 つ以上の値、行が選択されているときにします。</span><span class="sxs-lookup"><span data-stu-id="9d444-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="9d444-119">次のコードに表示されるデータを選択するために使用するクエリを示しています、<xref:System.Windows.Controls.DataGrid>です。</span><span class="sxs-lookup"><span data-stu-id="9d444-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="9d444-120">この例では、クエリは、顧客情報を含むエンティティからデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d444-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="9d444-121">リソースを使用して行の詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="9d444-121">To display row details by using a resource</span></span>  
  
1.  <span data-ttu-id="9d444-122">作成、<xref:System.Windows.Controls.DataGrid>データ ソースからデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d444-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="9d444-123">追加、<xref:System.Windows.FrameworkElement.Resources%2A>ルート要素の要素など、<xref:System.Windows.Window>コントロールまたは<xref:System.Windows.Controls.Page>制御、または追加、<xref:System.Windows.Application.Resources%2A>要素を<xref:System.Windows.Application>App.xaml (または Application.xaml) ファイル内のクラスです。</span><span class="sxs-lookup"><span data-stu-id="9d444-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3.  <span data-ttu-id="9d444-124">リソース要素で作成、<xref:System.Windows.DataTemplate>行の詳細セクションの外観を定義します。</span><span class="sxs-lookup"><span data-stu-id="9d444-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="9d444-125">次の XAML 示します、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>で定義されている、<xref:System.Windows.Application>クラスです。</span><span class="sxs-lookup"><span data-stu-id="9d444-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <span data-ttu-id="9d444-126"><xref:System.Windows.DataTemplate>、設定、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)データ テンプレートを一意に識別する値にします。</span><span class="sxs-lookup"><span data-stu-id="9d444-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5.  <span data-ttu-id="9d444-127"><xref:System.Windows.Controls.DataGrid>要素、設定、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>前の手順で定義されたリソースへのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="9d444-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="9d444-128">静的リソースとしてリソースを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9d444-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="9d444-129">次の XAML 示します、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>プロパティを前の例からリソースに設定します。</span><span class="sxs-lookup"><span data-stu-id="9d444-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="9d444-130">表示を設定し、行の詳細を水平方向にスクロールを回避するには</span><span class="sxs-lookup"><span data-stu-id="9d444-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1.  <span data-ttu-id="9d444-131">必要に応じて、設定、<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>プロパティを<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>値。</span><span class="sxs-lookup"><span data-stu-id="9d444-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="9d444-132">既定では、値に設定<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>です。</span><span class="sxs-lookup"><span data-stu-id="9d444-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="9d444-133">設定することができます<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>のすべての行の詳細を表示または<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>すべての行の詳細を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="9d444-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2.  <span data-ttu-id="9d444-134">必要に応じて、設定、<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A>プロパティを`true`を防ぐため、行の詳細セクションの水平方向にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="9d444-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
