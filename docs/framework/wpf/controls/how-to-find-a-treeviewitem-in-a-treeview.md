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
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>方法: TreeView で TreeViewItem を検索する
<xref:System.Windows.Controls.TreeView>コントロールには、階層データを表示する便利な手段が用意されています。 場合、<xref:System.Windows.Controls.TreeView>は、データ ソースにバインドされて、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティは、選択したデータ オブジェクトを迅速に取得するための便利な方法を提供します。 通常、基になるデータ オブジェクトを使用する最適な場合がありますがする必要しますが、ありますプログラムで操作を含むデータの<xref:System.Windows.Controls.TreeViewItem>します。 たとえば、プログラムを展開する必要があります、 <xref:System.Windows.Controls.TreeViewItem>、またはで別の項目を選択、<xref:System.Windows.Controls.TreeView>です。  
  
 検索する、<xref:System.Windows.Controls.TreeViewItem>特定のデータ オブジェクトを格納しているの各レベルを走査する必要があります、<xref:System.Windows.Controls.TreeView>です。 内の項目、<xref:System.Windows.Controls.TreeView>パフォーマンスを向上させるためにも仮想化されたことができます。 項目が仮想化の場合、する必要がありますまた、<xref:System.Windows.Controls.TreeViewItem>データ オブジェクトが含まれるかどうかを確認します。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
 次の検索の例、<xref:System.Windows.Controls.TreeView>特定のオブジェクトとを含むオブジェクトを返します<xref:System.Windows.Controls.TreeViewItem>です。 例では、によって、各<xref:System.Windows.Controls.TreeViewItem>がインスタンス化されるは、その子項目を検索できるようにします。 この例は、場合にも動作、<xref:System.Windows.Controls.TreeView>仮想化された項目を使用しません。  
  
> [!NOTE]
>  次の例は、いずれかの動作<xref:System.Windows.Controls.TreeView>、基になるデータ モデル、および検索に関係なくすべて<xref:System.Windows.Controls.TreeViewItem>オブジェクトが見つかるまでです。 パフォーマンスが向上するもう 1 つの方法は、指定したオブジェクトのデータ モデルでのデータ階層内での位置を追跡しを検索する、対応する<xref:System.Windows.Controls.TreeViewItem>で、<xref:System.Windows.Controls.TreeView>です。 パフォーマンスが向上する手法がデータ モデルの知識が必要し、特定の一般化することはできませんただし、<xref:System.Windows.Controls.TreeView>です。  
  
## <a name="code"></a>コード  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 上記のコードが依存するカスタム<xref:System.Windows.Controls.VirtualizingStackPanel>という名前のメソッドを公開する`BringIntoView`です。 次のコード定義のカスタム<xref:System.Windows.Controls.VirtualizingStackPanel>です。  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 次の XAML を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>ユーザー設定を使用する<xref:System.Windows.Controls.VirtualizingStackPanel>です。  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>関連項目  
 [TreeView のパフォーマンスを改善する](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
