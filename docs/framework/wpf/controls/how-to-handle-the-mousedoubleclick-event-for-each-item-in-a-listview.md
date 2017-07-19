---
title: "方法 : ListView の各項目の MouseDoubleClick イベントを処理する | Microsoft Docs"
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
  - "ListView コントロール, MouseDoubleClick イベント"
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ListView の各項目の MouseDoubleClick イベントを処理する
<xref:System.Windows.Controls.ListView> の項目のイベントを処理するには、各 <xref:System.Windows.Controls.ListViewItem> にイベント ハンドラーを追加する必要があります。  <xref:System.Windows.Controls.ListView> がデータ ソースにバインドされている場合、<xref:System.Windows.Controls.ListViewItem> を明示的には作成しませんが、<xref:System.Windows.Controls.ListViewItem> のスタイルに <xref:System.Windows.EventSetter> を追加することで、各項目のイベントを処理できます。  
  
## 使用例  
 データ バインド <xref:System.Windows.Controls.ListView> を作成し、各 <xref:System.Windows.Controls.ListViewItem> にイベント ハンドラーを追加する <xref:System.Windows.Style> を作成する例を次に示します。  
  
 [!code-xml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <xref:System.Windows.Controls.Control.MouseDoubleClick> イベントを処理する例を次に示します。  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ListView> をデータ ソースにバインドすることはきわめて一般的ですが、非データ バインド <xref:System.Windows.Controls.ListView> で、<xref:System.Windows.Controls.ListViewItem> を明示的に作成するかどうかに関係なく、スタイルを使用して各 <xref:System.Windows.Controls.ListViewItem> にイベント ハンドラーを追加することができます。  明示的および暗黙的に作成された <xref:System.Windows.Controls.ListViewItem> コントロールの詳細については、「<xref:System.Windows.Controls.ItemsControl>」を参照してください。  
  
## 参照  
 <xref:System.Xml.XmlElement>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)