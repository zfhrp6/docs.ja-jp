---
title: "方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bfa1941e6352372712debb5a5243bdd24810aac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="dae3a-102">方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う</span><span class="sxs-lookup"><span data-stu-id="dae3a-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="dae3a-103">この例は、内のデータ コレクションのビューを作成する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dae3a-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="dae3a-104">ビューを使用するグループ化、並べ替え、フィルター、の機能および現在のアイテムの概念です。</span><span class="sxs-lookup"><span data-stu-id="dae3a-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dae3a-105">例</span><span class="sxs-lookup"><span data-stu-id="dae3a-105">Example</span></span>  
 <span data-ttu-id="dae3a-106">次の例では、静的リソース名前*配置*のコレクションとして定義されて*場所*各内のオブジェクト*場所*オブジェクトは、市区町村名で構成されていましたし、状態です。</span><span class="sxs-lookup"><span data-stu-id="dae3a-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="dae3a-107">プレフィックス*src*名前空間にマップされているデータ ソース*場所*が定義されています。</span><span class="sxs-lookup"><span data-stu-id="dae3a-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="dae3a-108">プレフィックス*scm*にマップ`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`と*dat*にマップ`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`です。</span><span class="sxs-lookup"><span data-stu-id="dae3a-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="dae3a-109">次の例では、市区町村名によって並べ替えられ、状態別にグループ化するデータ コレクションのビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="dae3a-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="dae3a-110">ビューは、次の例のように、バインディング ソースに指定できます。</span><span class="sxs-lookup"><span data-stu-id="dae3a-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="dae3a-111">定義されている XML データへのバインドを<xref:System.Windows.Data.XmlDataProvider>リソースで XML 名の前に、@ 記号。</span><span class="sxs-lookup"><span data-stu-id="dae3a-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="dae3a-112">参照</span><span class="sxs-lookup"><span data-stu-id="dae3a-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="dae3a-113">データ コレクションの既定のビューを取得する</span><span class="sxs-lookup"><span data-stu-id="dae3a-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="dae3a-114">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="dae3a-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="dae3a-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="dae3a-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
