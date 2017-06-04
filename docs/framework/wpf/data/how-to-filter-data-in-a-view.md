---
title: "方法 : ビュー内のデータをフィルター処理する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ バインディング, フィルター処理 (ビュー内のデータを)"
  - "フィルター処理 (ビュー内のデータを)"
  - "ビュー, フィルター処理 (データを)"
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ビュー内のデータをフィルター処理する
この例では、ビュー内のデータをフィルター処理する方法を示します。  
  
## 使用例  
 フィルターを作成するには、フィルター処理ロジックを提供するメソッドを定義します。  このメソッドは、コールバックとして使用され、`object` 型のパラメーターを受け取ります。  次のメソッドは、残りのオブジェクトをフィルターで除外し、`filled` プロパティが "No" に設定されたすべての `Order` オブジェクトを返します。  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 次の例に示すように、フィルターを適用できます。  この例では、`myCollectionView` は、<xref:System.Windows.Data.ListCollectionView> オブジェクトです。  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 フィルターを解除するには、<xref:System.Windows.Data.CollectionView.Filter%2A> プロパティを `null` に設定できます。  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 ビューを作成または取得する方法については、「[データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)」を参照してください。  サンプル全体については、[ビューでの項目の並べ替えおよびフィルター処理のサンプル](http://go.microsoft.com/fwlink/?LinkID=160040)を参照してください。  
  
 ビュー オブジェクトが <xref:System.Windows.Data.CollectionViewSource> オブジェクトから生成された場合は、<xref:System.Windows.Data.CollectionViewSource.Filter> イベントのイベント ハンドラーを設定することによりフィルター処理ロジックを適用します。  次の例では、`listingDataView` は <xref:System.Windows.Data.CollectionViewSource> のインスタンスです。  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 `ShowOnlyBargainsFilter` フィルター イベント ハンドラーの実装例を次に示します。  このイベント ハンドラーは、<xref:System.Windows.Data.FilterEventArgs.Accepted%2A> プロパティを使用して、`CurrentPrice` が 25 ドル以上の `AuctionItem` オブジェクトをフィルターで除外します。  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## 参照  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>   
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [ビュー内のデータの並べ替え](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)