---
title: "方法 : ビュー内のデータをフィルター処理する"
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
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17b7fc68319552a7b31d5eaf7826146de5c41aa5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="09b6b-102">方法 : ビュー内のデータをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="09b6b-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="09b6b-103">この例では、ビュー内のデータをフィルター処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09b6b-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09b6b-104">例</span><span class="sxs-lookup"><span data-stu-id="09b6b-104">Example</span></span>  
 <span data-ttu-id="09b6b-105">フィルターを作成するには、フィルターのロジックを提供するメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="09b6b-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="09b6b-106">メソッドがコールバックとして使用され、型のパラメーターを受け入れる`object`です。</span><span class="sxs-lookup"><span data-stu-id="09b6b-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="09b6b-107">次のメソッドでは、すべてを返します、`Order`オブジェクトと、`filled`プロパティを"No"、残りのオブジェクトをフィルター処理に設定します。</span><span class="sxs-lookup"><span data-stu-id="09b6b-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="09b6b-108">次の例で示すように、フィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="09b6b-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="09b6b-109">この例では`myCollectionView`は、<xref:System.Windows.Data.ListCollectionView>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="09b6b-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="09b6b-110">フィルター処理を元に戻すに設定することができます、<xref:System.Windows.Data.CollectionView.Filter%2A>プロパティを`null`:</span><span class="sxs-lookup"><span data-stu-id="09b6b-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="09b6b-111">作成またはビューを取得する方法については、次を参照してください。[データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)です。</span><span class="sxs-lookup"><span data-stu-id="09b6b-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="09b6b-112">完了の例では、次を参照してください。[並べ替えおよび View サンプル内のアイテムのフィルタ リング](http://go.microsoft.com/fwlink/?LinkID=160040)です。</span><span class="sxs-lookup"><span data-stu-id="09b6b-112">For the complete example, see [Sorting and Filtering Items in a View Sample](http://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="09b6b-113">ビュー オブジェクトが元の場合、<xref:System.Windows.Data.CollectionViewSource>オブジェクト、イベント ハンドラーを設定してフィルター処理ロジックを適用する、<xref:System.Windows.Data.CollectionViewSource.Filter>イベント。</span><span class="sxs-lookup"><span data-stu-id="09b6b-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="09b6b-114">次の例では、`listingDataView`のインスタンスは、<xref:System.Windows.Data.CollectionViewSource>です。</span><span class="sxs-lookup"><span data-stu-id="09b6b-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="09b6b-115">この例の実装を次に示します`ShowOnlyBargainsFilter`フィルター イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="09b6b-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="09b6b-116">このイベント ハンドラーを使用して、<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>プロパティをフィルターで除外`AuctionItem`を持つオブジェクト、 `CurrentPrice` $25 以上です。</span><span class="sxs-lookup"><span data-stu-id="09b6b-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="09b6b-117">参照</span><span class="sxs-lookup"><span data-stu-id="09b6b-117">See Also</span></span>  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [<span data-ttu-id="09b6b-118">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="09b6b-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="09b6b-119">ビュー内のデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="09b6b-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="09b6b-120">方法トピック</span><span class="sxs-lookup"><span data-stu-id="09b6b-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
