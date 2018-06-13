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
ms.locfileid: "33557174"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>方法 : データ コレクションの既定のビューを取得する
ビューでは、並べ替え、フィルター処理、または条件をグループ化に応じて、さまざまな方法で表示する同じデータ収集を許可します。 すべてのコレクションには、バインディング ソースとしてコレクションを指定するときに、実際のバインド ソースとして使用される 1 つの共有の既定ビューがあります。 この例では、コレクションの既定のビューを取得する方法を示します。  
  
## <a name="example"></a>例  
 ビューを作成するには、コレクションにオブジェクト参照が必要です。 このデータ オブジェクトは、データ ソースのプロパティを取得するか、バインディングのプロパティを取得することによって、データ コンテキストを取得することにより、独自のコード ビハインド オブジェクトを参照することによって取得できます。 この例は、取得する方法を示します、<xref:System.Windows.FrameworkElement.DataContext%2A>データ オブジェクトと使用のこのコレクションの表示を既定のコレクションを直接取得することです。  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 ルート要素は、この例では、<xref:System.Windows.Controls.StackPanel>です。 <xref:System.Windows.FrameworkElement.DataContext%2A>に設定されている*myDataSource*、あるデータ プロバイダーを参照する、<xref:System.Collections.ObjectModel.ObservableCollection%601>の*順序*オブジェクト。  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 また、インスタンス化し、独自のビューを使用してコレクションにバインド、<xref:System.Windows.Data.CollectionViewSource>クラスです。 このコレクション ビューは、直接バインドするコントロールでのみ共有されます。 例については、ビューのセクションで作成する方法を参照してください、[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。  
  
 コレクション ビューによって提供される機能の例については、次を参照してください[ビューのデータを並べ替える](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)、[のビューのフィルター データ](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)、および[移動を通じて、内のオブジェクト データ CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>関連項目  
 [XAML でビューを使用してデータの並べ替えおよびグループ化を行う](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
