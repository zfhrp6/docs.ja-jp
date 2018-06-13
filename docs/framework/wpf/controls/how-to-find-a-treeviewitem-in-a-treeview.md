---
title: '方法: TreeView で TreeViewItem を検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: cff931312e6bc6db5ae5f26c0db80ad2f43825f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554756"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="72bd0-102">方法: TreeView で TreeViewItem を検索する</span><span class="sxs-lookup"><span data-stu-id="72bd0-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="72bd0-103"><xref:System.Windows.Controls.TreeView>コントロールには、階層データを表示する便利な手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="72bd0-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="72bd0-104">場合、<xref:System.Windows.Controls.TreeView>は、データ ソースにバインドされて、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティは、選択したデータ オブジェクトを迅速に取得するための便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="72bd0-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="72bd0-105">通常、基になるデータ オブジェクトを使用する最適な場合がありますがする必要しますが、ありますプログラムで操作を含むデータの<xref:System.Windows.Controls.TreeViewItem>します。</span><span class="sxs-lookup"><span data-stu-id="72bd0-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="72bd0-106">たとえば、プログラムを展開する必要があります、 <xref:System.Windows.Controls.TreeViewItem>、またはで別の項目を選択、<xref:System.Windows.Controls.TreeView>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="72bd0-107">検索する、<xref:System.Windows.Controls.TreeViewItem>特定のデータ オブジェクトを格納しているの各レベルを走査する必要があります、<xref:System.Windows.Controls.TreeView>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="72bd0-108">内の項目、<xref:System.Windows.Controls.TreeView>パフォーマンスを向上させるためにも仮想化されたことができます。</span><span class="sxs-lookup"><span data-stu-id="72bd0-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="72bd0-109">項目が仮想化の場合、する必要がありますまた、<xref:System.Windows.Controls.TreeViewItem>データ オブジェクトが含まれるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="72bd0-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72bd0-110">例</span><span class="sxs-lookup"><span data-stu-id="72bd0-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="72bd0-111">説明</span><span class="sxs-lookup"><span data-stu-id="72bd0-111">Description</span></span>  
 <span data-ttu-id="72bd0-112">次の検索の例、<xref:System.Windows.Controls.TreeView>特定のオブジェクトとを含むオブジェクトを返します<xref:System.Windows.Controls.TreeViewItem>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="72bd0-113">例では、によって、各<xref:System.Windows.Controls.TreeViewItem>がインスタンス化されるは、その子項目を検索できるようにします。</span><span class="sxs-lookup"><span data-stu-id="72bd0-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="72bd0-114">この例は、場合にも動作、<xref:System.Windows.Controls.TreeView>仮想化された項目を使用しません。</span><span class="sxs-lookup"><span data-stu-id="72bd0-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72bd0-115">次の例は、いずれかの動作<xref:System.Windows.Controls.TreeView>、基になるデータ モデル、および検索に関係なくすべて<xref:System.Windows.Controls.TreeViewItem>オブジェクトが見つかるまでです。</span><span class="sxs-lookup"><span data-stu-id="72bd0-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="72bd0-116">パフォーマンスが向上するもう 1 つの方法は、指定したオブジェクトのデータ モデルでのデータ階層内での位置を追跡しを検索する、対応する<xref:System.Windows.Controls.TreeViewItem>で、<xref:System.Windows.Controls.TreeView>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="72bd0-117">パフォーマンスが向上する手法がデータ モデルの知識が必要し、特定の一般化することはできませんただし、<xref:System.Windows.Controls.TreeView>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="72bd0-118">コード</span><span class="sxs-lookup"><span data-stu-id="72bd0-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="72bd0-119">上記のコードが依存するカスタム<xref:System.Windows.Controls.VirtualizingStackPanel>という名前のメソッドを公開する`BringIntoView`です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="72bd0-120">次のコード定義のカスタム<xref:System.Windows.Controls.VirtualizingStackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="72bd0-121">次の XAML を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>ユーザー設定を使用する<xref:System.Windows.Controls.VirtualizingStackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="72bd0-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="72bd0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="72bd0-122">See Also</span></span>  
 [<span data-ttu-id="72bd0-123">TreeView のパフォーマンスを改善する</span><span class="sxs-lookup"><span data-stu-id="72bd0-123">Improve the Performance of a TreeView</span></span>](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
