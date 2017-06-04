---
title: "方法 : 階層データでマスター詳細パターンを使用する | Microsoft Docs"
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
  - "データ バインディング, マスター/詳細データ パラダイム"
  - "マスター/詳細データ パラダイム"
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 階層データでマスター詳細パターンを使用する
この例では、マスター詳細シナリオを実装する方法を示します。  
  
## 使用例  
 この例では、`LeagueList` は `Leagues` のコレクションです。  `League` にはそれぞれ `Divisions` のコレクションと `Name` があり、`Division` にはそれぞれ `Teams` のコレクションと名前があります。  `Team` にはそれぞれチーム名があります。  
  
 [!code-xml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 この例のスクリーンショットを次に示します。  `Divisions` <xref:System.Windows.Controls.ListBox> は、`Leagues` <xref:System.Windows.Controls.ListBox> での選択を自動的に追跡し、対応するデータを表示します。  `Teams` <xref:System.Windows.Controls.ListBox> は、他の 2 つの <xref:System.Windows.Controls.ListBox> コントロールでの選択を追跡します。  
  
 ![マスター詳細のサンプル](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 この例では、次の 2 つの点に注意する必要があります。  
  
1.  3 つの <xref:System.Windows.Controls.ListBox> コントロールは、同じソースにバインドしています。  <xref:System.Windows.Controls.ListBox> に表示するデータのレベルを指定するには、バインディングの <xref:System.Windows.Data.Binding.Path%2A> プロパティを設定します。  
  
2.  選択を追跡する <xref:System.Windows.Controls.ListBox> コントロールでは、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> プロパティを `true` に設定する必要があります。  このプロパティを設定すると、選択されている項目は常に <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> として設定されます。  または、<xref:System.Windows.Controls.ListBox> が <xref:System.Windows.Data.CollectionViewSource> からデータを取得する場合は、選択と現在の項目が自動的に同期されます。  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データを使用する場合は、方法が若干異なります。  例については、「[階層 XML データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.HierarchicalDataTemplate>   
 [コレクションにバインドして選択に基づく情報を表示する](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)