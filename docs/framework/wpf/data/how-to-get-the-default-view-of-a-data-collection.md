---
title: '方法 : データ コレクションの既定のビューを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e8e6928391a98a132f1dbb39edfda0d73d2eebdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="8d4d8-102">方法 : データ コレクションの既定のビューを取得する</span><span class="sxs-lookup"><span data-stu-id="8d4d8-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="8d4d8-103">ビューでは、並べ替え、フィルター処理、または条件をグループ化に応じて、さまざまな方法で表示する同じデータ収集を許可します。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="8d4d8-104">すべてのコレクションには、バインディング ソースとしてコレクションを指定するときに、実際のバインド ソースとして使用される 1 つの共有の既定ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="8d4d8-105">この例では、コレクションの既定のビューを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d4d8-106">例</span><span class="sxs-lookup"><span data-stu-id="8d4d8-106">Example</span></span>  
 <span data-ttu-id="8d4d8-107">ビューを作成するには、コレクションにオブジェクト参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="8d4d8-108">このデータ オブジェクトは、データ ソースのプロパティを取得するか、バインディングのプロパティを取得することによって、データ コンテキストを取得することにより、独自のコード ビハインド オブジェクトを参照することによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="8d4d8-109">この例は、取得する方法を示します、<xref:System.Windows.FrameworkElement.DataContext%2A>データ オブジェクトと使用のこのコレクションの表示を既定のコレクションを直接取得することです。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="8d4d8-110">ルート要素は、この例では、<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="8d4d8-111"><xref:System.Windows.FrameworkElement.DataContext%2A>に設定されている*myDataSource*、あるデータ プロバイダーを参照する、<xref:System.Collections.ObjectModel.ObservableCollection%601>の*順序*オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="8d4d8-112">また、インスタンス化し、独自のビューを使用してコレクションにバインド、<xref:System.Windows.Data.CollectionViewSource>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="8d4d8-113">このコレクション ビューは、直接バインドするコントロールでのみ共有されます。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="8d4d8-114">例については、ビューのセクションで作成する方法を参照してください、[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="8d4d8-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="8d4d8-115">コレクション ビューによって提供される機能の例については、次を参照してください[ビューのデータを並べ替える](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)、[のビューのフィルター データ](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)、および[移動を通じて、内のオブジェクト データ CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="8d4d8-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4d8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d4d8-116">See Also</span></span>  
 [<span data-ttu-id="8d4d8-117">XAML でビューを使用してデータの並べ替えおよびグループ化を行う</span><span class="sxs-lookup"><span data-stu-id="8d4d8-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="8d4d8-118">方法トピック</span><span class="sxs-lookup"><span data-stu-id="8d4d8-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
