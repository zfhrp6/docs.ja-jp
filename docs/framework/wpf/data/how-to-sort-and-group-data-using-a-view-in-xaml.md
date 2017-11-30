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
ms.openlocfilehash: c219def87e258a2c9fc1bf4f4867287e6156c59a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="0534b-102">方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う</span><span class="sxs-lookup"><span data-stu-id="0534b-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="0534b-103">この例は、内のデータ コレクションのビューを作成する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0534b-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="0534b-104">ビューを使用するグループ化、並べ替え、フィルター、の機能および現在のアイテムの概念です。</span><span class="sxs-lookup"><span data-stu-id="0534b-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0534b-105">例</span><span class="sxs-lookup"><span data-stu-id="0534b-105">Example</span></span>  
 <span data-ttu-id="0534b-106">次の例では、静的リソース名前*配置*のコレクションとして定義されて*場所*各内のオブジェクト*場所*オブジェクトは、市区町村名で構成されていましたし、状態です。</span><span class="sxs-lookup"><span data-stu-id="0534b-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="0534b-107">プレフィックス*src*名前空間にマップされているデータ ソース*場所*が定義されています。</span><span class="sxs-lookup"><span data-stu-id="0534b-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="0534b-108">プレフィックス*scm*にマップ`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`と*dat*にマップ`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`です。</span><span class="sxs-lookup"><span data-stu-id="0534b-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="0534b-109">次の例では、市区町村名によって並べ替えられ、状態別にグループ化するデータ コレクションのビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="0534b-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="0534b-110">ビューは、次の例のように、バインディング ソースに指定できます。</span><span class="sxs-lookup"><span data-stu-id="0534b-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="0534b-111">定義されている XML データへのバインドを<xref:System.Windows.Data.XmlDataProvider>リソースで XML 名の前に、@ 記号。</span><span class="sxs-lookup"><span data-stu-id="0534b-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="0534b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0534b-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="0534b-113">データ コレクションの既定のビューを取得する</span><span class="sxs-lookup"><span data-stu-id="0534b-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="0534b-114">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="0534b-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0534b-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="0534b-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
