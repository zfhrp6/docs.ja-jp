---
title: "方法 : データ コレクションの既定のビューを取得する | Microsoft Docs"
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
  - "作成, データ コレクションのビュー"
  - "データ バインディング, 作成 (データ コレクションのビューを)"
  - "データ コレクション, 作成 (ビューを)"
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : データ コレクションの既定のビューを取得する
ビューを使用すると、並べ替え、フィルター処理、またはグループ化の基準に応じて、同じデータ コレクションをさまざまな方法で表示できます。  すべてのコレクションに、1 つの共有の既定ビューがあります。この既定のビューは、バインディングがそのソースとしてコレクションを指定したときに、実際のバインディング ソースとして使用されます。  この例は、コレクションの既定のビューを取得する方法を示しています。  
  
## 使用例  
 ビューを作成するには、コレクションへのオブジェクト参照が必要です。  このデータ オブジェクトは、独自の分離コード オブジェクトを参照することによって、データ コンテキストを取得することによって、データ ソースのプロパティを取得することによって、またはバインディングのプロパティを取得することによって得ることができます。  この例は、データ オブジェクトの <xref:System.Windows.FrameworkElement.DataContext%2A> を取得して、このコレクションの既定のコレクション ビューを直接取得するために使用する方法を示しています。  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 この例では、ルート要素は <xref:System.Windows.Controls.StackPanel> です。  <xref:System.Windows.FrameworkElement.DataContext%2A> は、データ プロバイダーを参照する *myDataSource* に設定されます。データ プロバイダーは、*Order* オブジェクトの <xref:System.Collections.ObjectModel.ObservableCollection%601> です。  
  
 [!code-xml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 また、<xref:System.Windows.Data.CollectionViewSource> クラスを使用して、独自のコレクション ビューをインスタンス化してそれにバインドすることもできます。  このコレクション ビューは、それに直接バインドするコントロールだけが共有します。  例については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」の「ビューの作成方法」を参照してください。  
  
 コレクション ビューによって提供される機能の例については、「[ビュー内のデータの並べ替え](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)」、「[ビュー内のデータをフィルター処理する](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)」および「[データ CollectionView のオブジェクト間を移動する](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)」を参照してください。  
  
## 参照  
 [XAML でビューを使用してデータの並べ替えおよびグループ化を行う](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)