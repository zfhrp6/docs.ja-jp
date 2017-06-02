---
title: "方法 : XMLDataProvider と XPath クエリを使用して XML データにバインドする | Microsoft Docs"
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
  - "バインド, XML データに (XmlDataProvider クエリを使用)"
  - "データ バインディング, バインド (XmlDataProvider クエリを使用して XML データに)"
  - "XmlDataProvider, バインド (XML データに)"
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 方法 : XMLDataProvider と XPath クエリを使用して XML データにバインドする
この例では、<xref:System.Windows.Data.XmlDataProvider> を使用して [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] データにバインドする方法を示します。  
  
 <xref:System.Windows.Data.XmlDataProvider> を使用して、アプリケーションでデータ バインディングを介してアクセスできる基になるデータは、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ノードの任意のツリーです。  つまり、<xref:System.Windows.Data.XmlDataProvider> とは、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ノードの任意のツリーを[バインディング ソース](GTMT)として使用するための便利な手段です。  
  
## 使用例  
 次の例では、データは [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ アイランドとして直接 <xref:System.Windows.FrameworkElement.Resources%2A> セクションに埋め込まれています。  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ アイランドは、`<x:XData>` タグ内にラップされていることと、常にルート ノードを 1 つだけ \(この例では *Inventory*\) 持つことが必要です。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データのルート ノードには **xmlns** 属性があり、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間が空の文字列に設定されています。  これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページ内にインラインで配置されるデータ アイランドに XPath クエリを適用する場合の必須事項です。  このインラインの場合は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] と、必然的にデータ アイランドも <xref:System.Windows> 名前空間を継承します。  このため、XPath クエリが <xref:System.Windows> 名前空間によって修飾されることを防ぐために、名前空間を空白に設定する必要があります。このようにしなければ、クエリの検索範囲が本来のものとは異なってしまいます。  
  
 [!code-xml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 この例に示すように、同じバインディング宣言を属性構文で作成するには、特殊文字を適切にエスケープする必要があります。  詳細については、「[XML 文字エンティティと XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)」を参照してください。  
  
 この例を実行すると、次の項目が <xref:System.Windows.Controls.ListBox> に表示されます。  これらは、*Books* の下のすべての要素のうち、*Stock* の値が "*out*" か、*Number* の値が 3 に等しいか 8 以上のものの *Title* です。  *CD* の項目が 1 つも返されないのは、<xref:System.Windows.Data.XmlDataProvider> の <xref:System.Windows.Data.XmlDataProvider.XPath%2A> の設定値が、*Books* 要素のみを公開するように指定されている \(フィルターを設定することと同じ\) からです。  
  
 ![XPath の例](../../../../docs/framework/wpf/data/media/xpathexample.png "XPathExample")  
  
 この例で書籍のタイトルが表示されるのは、<xref:System.Windows.DataTemplate> 内の <xref:System.Windows.Controls.TextBlock> バインディングの <xref:System.Windows.Data.Binding.XPath%2A> が "*Title*" に設定されているためです。  属性、たとえば *ISBN* の値を表示するには、<xref:System.Windows.Data.Binding.XPath%2A> の値を "`@ISBN`" に設定します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内の **XPath** プロパティは、XmlNode.SelectNodes メソッドによって処理されます。  別の結果を得るために、**XPath** クエリを変更することもできます。  前の例での、バインドされた <xref:System.Windows.Controls.ListBox> に対する <xref:System.Windows.Data.Binding.XPath%2A> クエリの例を次に示します。  
  
-   `XPath="Book[1]"` は、最初の書籍要素 \("XML in Action"\) を返します。  **XPath** のインデックスが 0 ではなく 1 から開始することに注意してください。  
  
-   `XPath="Book[@*]"` は、任意の属性を持つすべての書籍要素を返します。  
  
-   `XPath="Book[last()-1]"` は、最後から 2 番目の書籍要素 \("Introducing Microsoft .NET"\) を返します。  
  
-   `XPath="*[position()>3]"` は、最初の 3 つを除くすべての書籍要素を返します。  
  
 **XPath** クエリを実行すると、1 つの <xref:System.Xml.XmlNode> または XmlNode のリストが返されます。  <xref:System.Xml.XmlNode> は[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトです。つまり、<xref:System.Windows.Data.Binding.Path%2A> プロパティを使用して[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] のプロパティにバインドできます。  前の例をもう一度考えてみます。  例の残りの部分はそのままで <xref:System.Windows.Controls.TextBlock> バインディングを次のように変更すると、返された XmlNode の名前が <xref:System.Windows.Controls.ListBox> に表示されます。  この場合、返されたノードの名前はすべて "*Book*" です。  
  
 [!code-xml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページのソースに [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] をデータ アイランドとして埋め込む方法では、コンパイルの時点で正確なデータ コンテンツが必要となるので、アプリケーションによっては不都合が生じます。  したがって、次の例のように、外部ファイル [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] からデータを取得する機能もサポートされています。  
  
 [!code-xml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データがリモートの [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ファイル内に存在する場合は、次のように、適切な [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] を <xref:System.Windows.Data.XmlDataProvider.Source%2A> 属性に割り当てることによってデータへのアクセスを定義します。  
  
```  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## 参照  
 <xref:System.Windows.Data.ObjectDataProvider>   
 [XDocument、XElement、または LINQ for XML クエリの結果にバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)   
 [階層 XML データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)   
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)