---
title: "方法 : 階層 XML データでマスター詳細パターンを使用する | Microsoft Docs"
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
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 階層 XML データでマスター詳細パターンを使用する
この例では、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データでマスター詳細シナリオを実装する方法を示します。  
  
## 使用例  
 この例は、「[階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」で説明した例の [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ バージョンです。  この例では、データは `League.xml` ファイルから取得します。  3 番目の <xref:System.Windows.Controls.ListBox> コントロールが、2 番目の <xref:System.Windows.Controls.ListBox> の <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> プロパティにバインドすることにより、その選択項目の変更を追跡していることに注意してください。  
  
 [!code-xml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## 参照  
 <xref:System.Windows.HierarchicalDataTemplate>   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)