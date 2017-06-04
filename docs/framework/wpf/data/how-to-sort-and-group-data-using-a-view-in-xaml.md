---
title: "方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う | Microsoft Docs"
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
  - "データ バインディング, グループ化 (XAML でビューのデータを)"
  - "データ バインディング, 並べ替え (XAML でビューのデータを)"
  - "グループ化 (XAML でビューのデータを)"
  - "並べ替え (XAML でビューのデータを)"
  - "ビュー, グループ化 (データを)"
  - "ビュー, 並べ替え (データの)"
  - "XAML, グループ化 (ビューのデータを)"
  - "XAML, 並べ替え (ビューのデータを)"
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でデータ コレクションのビューを作成する方法を次の例に示します。  ビューには、グループ化、並べ替え、およびフィルター処理の機能があり、現在の項目も使用できます。  
  
## 使用例  
 次の例では、*places* という名前の静的リソースが、*Place* オブジェクトのコレクションとして定義されます。それぞれの *Place* オブジェクトは、都市の名前と州で構成されます。  プレフィックス *src* は、データ ソース *Places* が定義されている名前空間にマップされます。  プレフィックス *scm* は `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` にマップされ、*dat* は `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` にマップされます。  
  
 次の例では、CityName で並べ替えられ、State でグループ化されたデータ コレクションのビューを作成します。  
  
 [!code-xml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 その後、次の例のように、このビューをバインディング ソースに指定できます。  
  
 [!code-xml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <xref:System.Windows.Data.XmlDataProvider> リソースで定義された XML データへのバインディングの場合は、XML 名の前に @ 記号を付けます。  
  
 [!code-xml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## 参照  
 <xref:System.Windows.Data.CollectionViewSource>   
 [データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)