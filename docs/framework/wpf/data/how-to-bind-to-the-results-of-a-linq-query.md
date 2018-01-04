---
title: "方法 : LINQ クエリの結果にバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad4969d80f7bd801ec738fa40e8b2d4ab9deefad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="ec6b4-102">方法 : LINQ クエリの結果にバインドする</span><span class="sxs-lookup"><span data-stu-id="ec6b4-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="ec6b4-103">この例では、LINQ クエリを実行し、結果にバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec6b4-104">例</span><span class="sxs-lookup"><span data-stu-id="ec6b4-104">Example</span></span>  
 <span data-ttu-id="ec6b4-105">次の例では、次の 2 つのリスト ボックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-105">The following example creates two list boxes.</span></span> <span data-ttu-id="ec6b4-106">最初のリスト ボックスには、次の 3 つのリスト項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="ec6b4-107">最初のリスト ボックスから項目を選択すると、次のイベント ハンドラーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="ec6b4-108">この例では`Tasks`のコレクションは、`Task`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="ec6b4-109">`Task`クラスという名前のプロパティには`Priority`します。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="ec6b4-110">このイベント ハンドラーのコレクションを返す LINQ クエリを実行する`Task`オブジェクトを選択した優先度値を持ち、として設定し、 <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="ec6b4-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="ec6b4-111">に、2 番目のリスト ボックスがそのコレクションにバインドその<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>に値が設定されている`{Binding}`です。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="ec6b4-112">その結果、返されるコレクションが表示されます (に基づいて、 `myTaskTemplate` <xref:System.Windows.DataTemplate>)。</span><span class="sxs-lookup"><span data-stu-id="ec6b4-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6b4-113">参照</span><span class="sxs-lookup"><span data-stu-id="ec6b4-113">See Also</span></span>  
 [<span data-ttu-id="ec6b4-114">XAML でデータをバインディング可能にする</span><span class="sxs-lookup"><span data-stu-id="ec6b4-114">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [<span data-ttu-id="ec6b4-115">コレクションにバインドして選択に基づく情報を表示する</span><span class="sxs-lookup"><span data-stu-id="ec6b4-115">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="ec6b4-116">WPF Version 4.5 の新機能</span><span class="sxs-lookup"><span data-stu-id="ec6b4-116">What's New in WPF Version 4.5</span></span>](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [<span data-ttu-id="ec6b4-117">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="ec6b4-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="ec6b4-118">方法トピック</span><span class="sxs-lookup"><span data-stu-id="ec6b4-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
