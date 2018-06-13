---
title: '方法: DataGrid コントロールでデータをグループ化、並べ替え、およびフィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 675c1441201fa1578023d6ed758f389a38f3b79a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557031"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="48bbc-102">方法: DataGrid コントロールでデータをグループ化、並べ替え、およびフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="48bbc-102">How to: Group, Sort, and Filter Data in the DataGrid Control</span></span>
<span data-ttu-id="48bbc-103">内のデータを表示すると便利です、<xref:System.Windows.Controls.DataGrid>によってグループ化、並べ替え、およびデータのフィルター処理のさまざまな方法でします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="48bbc-104">グループ化、並べ替え、およびデータをフィルター処理、<xref:System.Windows.Controls.DataGrid>にバインドする、<xref:System.Windows.Data.CollectionView>これらの関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="48bbc-105">内のデータを操作することができますし、<xref:System.Windows.Data.CollectionView>基になるソース データには影響しません。</span><span class="sxs-lookup"><span data-stu-id="48bbc-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="48bbc-106">コレクション ビューの変更に反映されます、<xref:System.Windows.Controls.DataGrid>ユーザー インターフェイス (UI)。</span><span class="sxs-lookup"><span data-stu-id="48bbc-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>  
  
 <span data-ttu-id="48bbc-107"><xref:System.Windows.Data.CollectionView>クラスには、グループ化および並べ替えを実装するデータ ソースの機能が用意されています、<xref:System.Collections.IEnumerable>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="48bbc-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="48bbc-108"><xref:System.Windows.Data.CollectionViewSource>クラスでは、プロパティを設定することができます、 <xref:System.Windows.Data.CollectionView> XAML からです。</span><span class="sxs-lookup"><span data-stu-id="48bbc-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>  
  
 <span data-ttu-id="48bbc-109">この例では、コレクションで`Task`にオブジェクトがバインドされて、<xref:System.Windows.Data.CollectionViewSource>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="48bbc-110"><xref:System.Windows.Data.CollectionViewSource>として使用される、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.DataGrid>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="48bbc-111">グループ化、並べ替え、およびフィルター処理を実行、<xref:System.Windows.Data.CollectionViewSource>に表示されると、 <xref:System.Windows.Controls.DataGrid> UI。</span><span class="sxs-lookup"><span data-stu-id="48bbc-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="48bbc-112">![データ グリッド内のデータをグループ化](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span><span class="sxs-lookup"><span data-stu-id="48bbc-112">![Grouped data in a DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span></span>  
<span data-ttu-id="48bbc-113">DataGrid のグループ化されたデータ</span><span class="sxs-lookup"><span data-stu-id="48bbc-113">Grouped Data in a DataGrid</span></span>  
  
## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="48bbc-114">ItemsSource として、CollectionViewSource を使用します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-114">Using a CollectionViewSource as an ItemsSource</span></span>  
 <span data-ttu-id="48bbc-115">グループ、並べ替え、およびデータのフィルター処理する、<xref:System.Windows.Controls.DataGrid>コントロールをバインドする、<xref:System.Windows.Controls.DataGrid>を<xref:System.Windows.Data.CollectionView>これらの関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="48bbc-116">この例では、<xref:System.Windows.Controls.DataGrid>にバインドされて、<xref:System.Windows.Data.CollectionViewSource>のこれらの関数を提供する、<xref:System.Collections.Generic.List%601>の`Task`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="48bbc-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>  
  
#### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="48bbc-117">CollectionViewSource に DataGrid をバインドするには</span><span class="sxs-lookup"><span data-stu-id="48bbc-117">To bind a DataGrid to a CollectionViewSource</span></span>  
  
1.  <span data-ttu-id="48bbc-118">実装するデータ コレクションを作成、<xref:System.Collections.IEnumerable>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="48bbc-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
     <span data-ttu-id="48bbc-119">使用する場合<xref:System.Collections.Generic.List%601>、コレクションを作成するから継承する新しいクラスを作成する必要があります<xref:System.Collections.Generic.List%601>のインスタンスをインスタンス化ではなく<xref:System.Collections.Generic.List%601>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="48bbc-120">XAML 内のコレクションへのデータ バインドにできます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-120">This enables you to data bind to the collection in XAML.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48bbc-121">コレクション内のオブジェクトを実装する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged>変更されたインターフェイスと<xref:System.ComponentModel.IEditableObject>インターフェイスの順序で、<xref:System.Windows.Controls.DataGrid>プロパティの変更と編集に正しく応答します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="48bbc-122">詳細については、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48bbc-122">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  <span data-ttu-id="48bbc-123">XAML では、コレクション クラスのインスタンスを作成し、設定、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
3.  <span data-ttu-id="48bbc-124">XAML では、インスタンスを作成、<xref:System.Windows.Data.CollectionViewSource>クラスは、設定、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)、としてコレクション クラスのインスタンスを設定し、<xref:System.Windows.Data.CollectionViewSource.Source%2A>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  <span data-ttu-id="48bbc-125">インスタンスを作成、<xref:System.Windows.Controls.DataGrid>クラス、し、設定、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティを<xref:System.Windows.Data.CollectionViewSource>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  <span data-ttu-id="48bbc-126">アクセスする、 <xref:System.Windows.Data.CollectionViewSource> 、コードから使用して、<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>への参照を取得するメソッド、<xref:System.Windows.Data.CollectionViewSource>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="48bbc-127">データ グリッド内の項目をグループ化</span><span class="sxs-lookup"><span data-stu-id="48bbc-127">Grouping items in a DataGrid</span></span>  
 <span data-ttu-id="48bbc-128">項目をグループ化する方法を指定する、<xref:System.Windows.Controls.DataGrid>を使用する、<xref:System.Windows.Data.PropertyGroupDescription>ソース ビュー内の項目をグループ化する型。</span><span class="sxs-lookup"><span data-stu-id="48bbc-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>  
  
#### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="48bbc-129">XAML を使用してデータ グリッド内のアイテムをグループ化</span><span class="sxs-lookup"><span data-stu-id="48bbc-129">To group items in a DataGrid using XAML</span></span>  
  
1.  <span data-ttu-id="48bbc-130">作成、<xref:System.Windows.Data.PropertyGroupDescription>グループ化するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="48bbc-131">XAML またはコードでは、プロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-131">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="48bbc-132">XAML では、設定、<xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A>グループ化するプロパティの名前にします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>  
  
    2.  <span data-ttu-id="48bbc-133">コードでは、コンス トラクターにグループ化するプロパティの名前を渡します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-133">In code, pass the name of the property to group by to the constructor.</span></span>  
  
2.  <span data-ttu-id="48bbc-134">追加、<xref:System.Windows.Data.PropertyGroupDescription>を<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>コレクション。</span><span class="sxs-lookup"><span data-stu-id="48bbc-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="48bbc-135">追加のインスタンスの追加<xref:System.Windows.Data.PropertyGroupDescription>を<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>複数レベルのグループ化を追加するコレクション。</span><span class="sxs-lookup"><span data-stu-id="48bbc-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  <span data-ttu-id="48bbc-136">グループを削除するには、削除、<xref:System.Windows.Data.PropertyGroupDescription>から、<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="48bbc-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
5.  <span data-ttu-id="48bbc-137">すべてのグループを削除するには、呼び出し、<xref:System.Collections.ObjectModel.Collection%601.Clear%2A>のメソッド、<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="48bbc-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 <span data-ttu-id="48bbc-138">項目をグループ化するときに、 <xref:System.Windows.Controls.DataGrid>、定義することができます、<xref:System.Windows.Controls.GroupStyle>各グループの外観を指定します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="48bbc-139">適用する、<xref:System.Windows.Controls.GroupStyle>に追加することによって、 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid のコレクション。</span><span class="sxs-lookup"><span data-stu-id="48bbc-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="48bbc-140">複数のレベルのグループ化した場合は、グループ レベルごとに異なるスタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="48bbc-141">スタイルは定義されている順序で適用されます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="48bbc-142">たとえば、2 つのスタイルを定義する場合、最初は最上位レベルの行グループに適用します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="48bbc-143">2 番目のスタイルは、第 2 レベルのすべての行グループに適用されると下限になります。</span><span class="sxs-lookup"><span data-stu-id="48bbc-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="48bbc-144"><xref:System.Windows.FrameworkElement.DataContext%2A>の<xref:System.Windows.Controls.GroupStyle>は、<xref:System.Windows.Data.CollectionViewGroup>グループを表すです。</span><span class="sxs-lookup"><span data-stu-id="48bbc-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>  
  
#### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="48bbc-145">行グループ ヘッダーの外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="48bbc-145">To change the appearance of row group headers</span></span>  
  
1.  <span data-ttu-id="48bbc-146">作成、<xref:System.Windows.Controls.GroupStyle>行グループの外観を定義します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>  
  
2.  <span data-ttu-id="48bbc-147">Put、<xref:System.Windows.Controls.GroupStyle>内、`<DataGrid.GroupStyle>`タグ。</span><span class="sxs-lookup"><span data-stu-id="48bbc-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="48bbc-148">DataGrid のアイテムの並べ替え</span><span class="sxs-lookup"><span data-stu-id="48bbc-148">Sorting items in a DataGrid</span></span>  
 <span data-ttu-id="48bbc-149">項目の並べ替え方法を指定する、<xref:System.Windows.Controls.DataGrid>を使用する、<xref:System.ComponentModel.SortDescription>型をソース ビュー内の項目を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>  
  
#### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="48bbc-150">DataGrid の項目を並べ替える</span><span class="sxs-lookup"><span data-stu-id="48bbc-150">To sort items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="48bbc-151">作成、<xref:System.ComponentModel.SortDescription>で並べ替えを行うプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="48bbc-152">XAML またはコードでは、プロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-152">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="48bbc-153">XAML では、設定、<xref:System.ComponentModel.SortDescription.PropertyName%2A>によって並べ替えするプロパティの名前にします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>  
  
    2.  <span data-ttu-id="48bbc-154">コードでは、並べ替えるプロパティの名前を渡すと、<xref:System.ComponentModel.ListSortDirection>コンス トラクターにします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>  
  
2.  <span data-ttu-id="48bbc-155">追加、<xref:System.ComponentModel.SortDescription>を<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>コレクション。</span><span class="sxs-lookup"><span data-stu-id="48bbc-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="48bbc-156">追加のインスタンスの追加<xref:System.ComponentModel.SortDescription>を<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A>コレクションに追加のプロパティを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="48bbc-157">DataGrid の項目をフィルター処理</span><span class="sxs-lookup"><span data-stu-id="48bbc-157">Filtering items in a DataGrid</span></span>  
 <span data-ttu-id="48bbc-158">項目をフィルター処理で、<xref:System.Windows.Controls.DataGrid>を使用して、<xref:System.Windows.Data.CollectionViewSource>のハンドラーでフィルター処理のロジックを提供する、<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="48bbc-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
#### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="48bbc-159">DataGrid の項目をフィルターするには</span><span class="sxs-lookup"><span data-stu-id="48bbc-159">To filter items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="48bbc-160">ハンドラーを追加、<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="48bbc-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
2.  <span data-ttu-id="48bbc-161"><xref:System.Windows.Data.CollectionViewSource.Filter>イベント ハンドラー、フィルター処理のロジックを定義します。</span><span class="sxs-lookup"><span data-stu-id="48bbc-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>  
  
     <span data-ttu-id="48bbc-162">ビューが更新されるたびに、フィルターが適用されます。</span><span class="sxs-lookup"><span data-stu-id="48bbc-162">The filter will be applied every time the view is refreshed.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 <span data-ttu-id="48bbc-163">または、内の項目をフィルター処理することができます、<xref:System.Windows.Controls.DataGrid>をフィルター処理のロジックと設定を提供するメソッドを作成することで、<xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType>フィルターを適用するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="48bbc-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="48bbc-164">このメソッドの例を参照してください[のビューのフィルター データ](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-164">To see an example of this method, see [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48bbc-165">例</span><span class="sxs-lookup"><span data-stu-id="48bbc-165">Example</span></span>  
 <span data-ttu-id="48bbc-166">次の例は、グループ化、並べ替え、およびフィルター処理を示しています。`Task`内のデータ、<xref:System.Windows.Data.CollectionViewSource>と表示、並べ替え、フィルターにグループ化、`Task`内のデータ、<xref:System.Windows.Controls.DataGrid>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="48bbc-167"><xref:System.Windows.Data.CollectionViewSource>として使用される、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.DataGrid>です。</span><span class="sxs-lookup"><span data-stu-id="48bbc-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="48bbc-168">グループ化、並べ替え、およびフィルター処理を実行、<xref:System.Windows.Data.CollectionViewSource>に表示されると、 <xref:System.Windows.Controls.DataGrid> UI。</span><span class="sxs-lookup"><span data-stu-id="48bbc-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="48bbc-169">この例をテストするには、プロジェクト名を一致させる DGGroupSortFilterExample 名前を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48bbc-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="48bbc-170">Visual Basic を使用している場合は、クラス名を変更する必要があります。<xref:System.Windows.Window>以下にします。</span><span class="sxs-lookup"><span data-stu-id="48bbc-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xaml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48bbc-171">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="48bbc-171">Compiling the Code</span></span>  
  
-  
  
## <a name="robust-programming"></a><span data-ttu-id="48bbc-172">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="48bbc-172">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="48bbc-173">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="48bbc-173">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48bbc-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="48bbc-174">See Also</span></span>  
 [<span data-ttu-id="48bbc-175">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="48bbc-175">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="48bbc-176">ObservableCollection を作成およびバインドする</span><span class="sxs-lookup"><span data-stu-id="48bbc-176">Create and Bind to an ObservableCollection</span></span>](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)  
 [<span data-ttu-id="48bbc-177">ビュー内のデータをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="48bbc-177">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="48bbc-178">ビュー内のデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="48bbc-178">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="48bbc-179">XAML でビューを使用してデータの並べ替えおよびグループ化を行う</span><span class="sxs-lookup"><span data-stu-id="48bbc-179">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
