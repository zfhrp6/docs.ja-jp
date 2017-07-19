---
title: "方法 : GridView を実装する ListView で行のスタイルを設定する | Microsoft Docs"
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
  - "行のスタイル設定、GridView コントロール"
  - "スタイル設定 (GridView を実装する ListView の行を)"
  - "ListView コントロール、Gridview を含む行のスタイル設定"
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : GridView を実装する ListView で行のスタイルを設定する
内の行のスタイルを設定する方法を示します、 <xref:System.Windows.Controls.ListView>を実装するコントロール、 <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>モードです。  
  
## <a name="example"></a>例  
 内の行のスタイルを設定することができます、 <xref:System.Windows.Controls.ListView>コントロールを設定して、 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上、 <xref:System.Windows.Controls.ListView>コントロールです。 として表される項目のスタイルを設定<xref:System.Windows.Controls.ListViewItem>のオブジェクト。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>参照、 <xref:System.Windows.Controls.ControlTemplate>オブジェクト、行の内容を表示するために使用します。  
  
 次の例の抽出元で、完全なサンプルに格納されている楽曲情報のコレクションを表示する、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データベースです。 データベースの各曲が格納された rating フィールドをこのフィールドの値が曲情報の行を表示する方法を指定します。  
  
 次の例は、定義する方法を示しています。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>の、 <xref:System.Windows.Controls.ListViewItem>曲のコレクション内の曲を表すオブジェクト。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>参照<xref:System.Windows.Controls.ControlTemplate>楽曲情報の行を表示する方法を指定するオブジェクト。  
  
 [!code-xml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 例を次に、 <xref:System.Windows.Controls.ControlTemplate>テキスト文字列を追加する`"Strongly Recommended"`行にします。 このテンプレートで参照される、 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>し、曲の格付けがある 5 (5) の値が表示されます。 <xref:System.Windows.Controls.ControlTemplate>を含む、 <xref:System.Windows.Controls.GridViewRowPresenter>オブジェクトで定義されている列の行の内容をレイアウトする、 <xref:System.Windows.Controls.GridView>表示モード。  
  
 [!code-xml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 次の例では定義<xref:System.Windows.Controls.GridView>します。  
  
 [!code-xml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [操作方法に関するトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)