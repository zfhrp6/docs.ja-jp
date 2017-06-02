---
title: "方法 : CompositeCollection を実装する | Microsoft Docs"
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
  - "クラス, CompositeCollection"
  - "データ バインディング, CompositeCollection クラス"
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : CompositeCollection を実装する
## 使用例  
 <xref:System.Windows.Data.CompositeCollection> クラスを使用して、複数のコレクションと項目を 1 つのリストとして表示する方法を次の例に示します。  この例では、`GreekGods` は `GreekGod` カスタム オブジェクトの <xref:System.Collections.ObjectModel.ObservableCollection%601> です。  データ テンプレートは、`GreekGod` オブジェクトと `GreekHero` オブジェクトがそれぞれ金とシアンの前景色で表示されるように定義されています。  
  
 [!code-xml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## 参照  
 <xref:System.Windows.Data.CollectionContainer>   
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>   
 <xref:System.Windows.Data.XmlDataProvider>   
 <xref:System.Windows.DataTemplate>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)