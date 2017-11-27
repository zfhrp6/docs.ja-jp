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
ms.openlocfilehash: de51aa83af71027ce86909a15f3ceee58fb47814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-data-in-a-view"></a>方法 : ビュー内のデータをフィルター処理する
この例では、ビュー内のデータをフィルター処理する方法を示します。  
  
## <a name="example"></a>例  
 フィルターを作成するには、フィルターのロジックを提供するメソッドを定義します。 メソッドがコールバックとして使用され、型のパラメーターを受け入れる`object`です。 次のメソッドでは、すべてを返します、`Order`オブジェクトと、`filled`プロパティを"No"、残りのオブジェクトをフィルター処理に設定します。  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 次の例で示すように、フィルターを適用できます。 この例では`myCollectionView`は、<xref:System.Windows.Data.ListCollectionView>オブジェクト。  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 フィルター処理を元に戻すに設定することができます、<xref:System.Windows.Data.CollectionView.Filter%2A>プロパティを`null`:  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 作成またはビューを取得する方法については、次を参照してください。[データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)です。 完了の例では、次を参照してください。[並べ替えおよび View サンプル内のアイテムのフィルタ リング](http://go.microsoft.com/fwlink/?LinkID=160040)です。  
  
 ビュー オブジェクトが元の場合、<xref:System.Windows.Data.CollectionViewSource>オブジェクト、イベント ハンドラーを設定してフィルター処理ロジックを適用する、<xref:System.Windows.Data.CollectionViewSource.Filter>イベント。 次の例では、`listingDataView`のインスタンスは、<xref:System.Windows.Data.CollectionViewSource>です。  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 この例の実装を次に示します`ShowOnlyBargainsFilter`フィルター イベント ハンドラー。 このイベント ハンドラーを使用して、<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>プロパティをフィルターで除外`AuctionItem`を持つオブジェクト、 `CurrentPrice` $25 以上です。  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [ビュー内のデータの並べ替え](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
