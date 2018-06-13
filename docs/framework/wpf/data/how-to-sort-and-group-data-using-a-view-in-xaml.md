---
title: '方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う'
ms.date: 03/30/2017
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
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555831"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="76d38-102">方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う</span><span class="sxs-lookup"><span data-stu-id="76d38-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="76d38-103">この例は、内のデータ コレクションのビューを作成する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="76d38-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="76d38-104">ビューを使用するグループ化、並べ替え、フィルター、の機能および現在のアイテムの概念です。</span><span class="sxs-lookup"><span data-stu-id="76d38-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76d38-105">例</span><span class="sxs-lookup"><span data-stu-id="76d38-105">Example</span></span>  
 <span data-ttu-id="76d38-106">次の例では、静的リソース名前*配置*のコレクションとして定義されて*場所*各内のオブジェクト*場所*オブジェクトは、市区町村名で構成されていましたし、状態です。</span><span class="sxs-lookup"><span data-stu-id="76d38-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="76d38-107">プレフィックス*src*名前空間にマップされているデータ ソース*場所*が定義されています。</span><span class="sxs-lookup"><span data-stu-id="76d38-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="76d38-108">プレフィックス*scm*にマップ`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`と*dat*にマップ`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`です。</span><span class="sxs-lookup"><span data-stu-id="76d38-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="76d38-109">次の例では、市区町村名によって並べ替えられ、状態別にグループ化するデータ コレクションのビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="76d38-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="76d38-110">ビューは、次の例のように、バインディング ソースに指定できます。</span><span class="sxs-lookup"><span data-stu-id="76d38-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="76d38-111">定義されている XML データへのバインドを<xref:System.Windows.Data.XmlDataProvider>リソースで XML 名の前に、@ 記号。</span><span class="sxs-lookup"><span data-stu-id="76d38-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="76d38-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="76d38-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="76d38-113">データ コレクションの既定のビューを取得する</span><span class="sxs-lookup"><span data-stu-id="76d38-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="76d38-114">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="76d38-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="76d38-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="76d38-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
