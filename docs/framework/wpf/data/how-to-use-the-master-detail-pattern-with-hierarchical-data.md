---
title: "方法 : 階層データでマスター詳細パターンを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="21146-102">方法 : 階層データでマスター詳細パターンを使用する</span><span class="sxs-lookup"><span data-stu-id="21146-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="21146-103">この例では、マスター/詳細シナリオを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="21146-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21146-104">例</span><span class="sxs-lookup"><span data-stu-id="21146-104">Example</span></span>  
 <span data-ttu-id="21146-105">この例では`LeagueList`のコレクションは、`Leagues`です。</span><span class="sxs-lookup"><span data-stu-id="21146-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="21146-106">各`League`が、`Name`およびのコレクションの`Divisions`、および各`Division`名は、一連の`Teams`します。</span><span class="sxs-lookup"><span data-stu-id="21146-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="21146-107">各`Team`team 名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="21146-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="21146-108">次に示すのは、この例のスクリーンショットです。</span><span class="sxs-lookup"><span data-stu-id="21146-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="21146-109">`Divisions` <xref:System.Windows.Controls.ListBox>の選択項目が自動的に追跡、 `Leagues` <xref:System.Windows.Controls.ListBox>し、対応するデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="21146-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="21146-110">`Teams` <xref:System.Windows.Controls.ListBox>他の 2 つの選択項目を追跡<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="21146-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="21146-111">![マスター &#45; detail の例](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="21146-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="21146-112">この例では注意する 2 つの点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="21146-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="21146-113">3 つ<xref:System.Windows.Controls.ListBox>コントロールを同じソースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="21146-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="21146-114">設定する、<xref:System.Windows.Data.Binding.Path%2A>するデータのレベルを指定するバインドのプロパティ、<xref:System.Windows.Controls.ListBox>を表示します。</span><span class="sxs-lookup"><span data-stu-id="21146-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="21146-115">設定する必要があります、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティを`true`上、<xref:System.Windows.Controls.ListBox>コントロールを追跡して、選択します。</span><span class="sxs-lookup"><span data-stu-id="21146-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="21146-116">このプロパティを設定すると、選択した項目として常に設定されている、<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>です。</span><span class="sxs-lookup"><span data-stu-id="21146-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="21146-117">また場合、<xref:System.Windows.Controls.ListBox>からデータを取得、 <xref:System.Windows.Data.CollectionViewSource>、選択範囲と通貨を自動的に同期します。</span><span class="sxs-lookup"><span data-stu-id="21146-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="21146-118">使用しているときに、手法は若干異なります[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ。</span><span class="sxs-lookup"><span data-stu-id="21146-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="21146-119">例については、次を参照してください。[階層の XML データを、マスター/詳細形式のパターンを使用して](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="21146-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21146-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="21146-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="21146-121">コレクションにバインドして選択に基づく情報を表示する</span><span class="sxs-lookup"><span data-stu-id="21146-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="21146-122">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="21146-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="21146-123">データ テンプレートの概要</span><span class="sxs-lookup"><span data-stu-id="21146-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="21146-124">方法トピック</span><span class="sxs-lookup"><span data-stu-id="21146-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
