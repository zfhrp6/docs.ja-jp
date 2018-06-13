---
title: '方法 : XMLDataProvider と XPath クエリを使用して XML データにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: bb8eb727fb6614440721c4d34a7d1828182d2f14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557447"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>方法 : XMLDataProvider と XPath クエリを使用して XML データにバインドする
この例をバインドする方法を示しています。[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]データを使用して、<xref:System.Windows.Data.XmlDataProvider>です。  
  
 <xref:System.Windows.Data.XmlDataProvider>では、アプリケーションでのデータ バインドを介してアクセスできるデータを基になることができますが、ツリーの[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ノード。 言い換えると、<xref:System.Windows.Data.XmlDataProvider>の任意のツリーを使用する便利な手段を提供[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]バインディング ソースとしてのノードです。  
  
## <a name="example"></a>例  
 次の例では、データとして直接埋め込まれて、 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *データ アイランド*内で、<xref:System.Windows.FrameworkElement.Resources%2A>セクションです。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ アイランドは、`<x:XData>` タグ内にラップされていることと、常にルート ノードを 1 つだけ (この例では *Inventory*) 持つことが必要です。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データのルート ノードには、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間を空の文字列に設定する **xmlns** 属性があります。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページ内にインラインで配置されるデータ アイランドに XPath クエリを適用する場合に必須です。 インラインここでは、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、継承データ アイランド、<xref:System.Windows>名前空間。 このため、名前空間で修飾されているから XPath クエリを保持する場合は空白に設定する必要があります、<xref:System.Windows>名前空間は、クエリの送信先を誤るとします。  
  
 [!code-xaml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 この例に示すように、同じバインディング宣言を属性構文で作成するには、特殊文字を適切にエスケープする必要があります。 詳しくは、「[XML Character Entities and XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)」(XML 文字エンティティと XAML) をご覧ください。  
  
 <xref:System.Windows.Controls.ListBox>この例を実行すると、次の項目が表示されます。 これらは、*Books* の下のすべての要素のうち、*Stock* の値が "*out*" か、*Number* の値が 3 に等しいか 8 以上のものの *Title* です。 注意してない*CD*ために、項目が返されます、<xref:System.Windows.Data.XmlDataProvider.XPath%2A>セットの値を<xref:System.Windows.Data.XmlDataProvider>だけであることを示します、*ブック*(本質的にフィルターを設定する) の要素を公開する必要があります。  
  
 ![XPath の例](../../../../docs/framework/wpf/data/media/xpathexample.PNG "XPathExample")  
  
 この例では、書籍のタイトルが表示されて、<xref:System.Windows.Data.Binding.XPath%2A>の<xref:System.Windows.Controls.TextBlock>でのバインディング、<xref:System.Windows.DataTemplate>に設定されている"*タイトル*"です。 など、属性の値を表示するかどうか、 *ISBN*を設定する<xref:System.Windows.Data.Binding.XPath%2A>値を"`@ISBN`"です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内の **XPath** プロパティは、XmlNode.SelectNodes メソッドによって処理されます。 別の結果を得るために、**XPath** クエリを変更できます。 ここでは、いくつかの例を<xref:System.Windows.Data.Binding.XPath%2A>にバインドされているクエリを<xref:System.Windows.Controls.ListBox>前の例。  
  
-   `XPath="Book[1]"` は、最初の書籍要素 ("XML in Action") を返します。 **XPath** のインデックスが 0 ではなく 1 から開始することにご注意ください。  
  
-   `XPath="Book[@*]"` は、任意の属性を持つすべての書籍要素を返します。  
  
-   `XPath="Book[last()-1]"` は、最後から 2 番目の書籍要素 ("Introducing Microsoft .NET") を返します。  
  
-   `XPath="*[position()>3]"` は、最初の 3 つを除くすべての書籍要素を返します。  
  
 実行すると、 **XPath**クエリで返されます、<xref:System.Xml.XmlNode>または XmlNodes の一覧です。 <xref:System.Xml.XmlNode> [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]使用できるオブジェクト、<xref:System.Windows.Data.Binding.Path%2A>にバインドするプロパティ、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]プロパティです。 前の例をもう一度考えてみます。 場合の例では、残りの部分は、同じまま変更して、<xref:System.Windows.Controls.TextBlock>には、次のバインドで返される XmlNodes の名前が表示されます、<xref:System.Windows.Controls.ListBox>です。 この場合、返されたノードの名前はすべて "*Book*" です。  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページのソースに [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] をデータ アイランドとして埋め込む方法では、コンパイル時に正確なデータ コンテンツが必要となるので、アプリケーションによっては不都合が生じます。 したがって、次の例のように、外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ファイルからのデータの取得もサポートされています。  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 場合、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]リモート データが存在する[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイルがアクセスを定義するデータに適切なを割り当てることによって[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]を<xref:System.Windows.Data.XmlDataProvider.Source%2A>次のように属性します。  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.ObjectDataProvider>  
 [XDocument、XElement、または LINQ for XML クエリの結果にバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)  
 [階層 XML データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
