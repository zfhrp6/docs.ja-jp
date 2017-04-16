---
title: "方法 : データ バインドで XML 名前空間を使用する | Microsoft Docs"
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
  - "データ バインディング, XML 名前空間"
  - "名前空間, XML"
  - "XML, 名前空間"
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : データ バインドで XML 名前空間を使用する
## 使用例  
 この例は、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] [バインディング ソース](GTMT)で指定された名前空間を処理する方法を示します。  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データに次の [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間定義があるとします。  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 この場合は、次の例のように、<xref:System.Windows.Data.XmlNamespaceMapping> 要素を使用して名前空間を <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> にマッピングします。  これで、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> を使用して [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間を参照できます。  この例の <xref:System.Windows.Controls.ListBox> では、各 *item* の *title* および *dc:date* が表示されます。  
  
 [!code-xml[XmlnsBind#XmlNamespaceMapping](../../../../samples/snippets/xaml/VS_Snippets_Wpf/XmlnsBind/XAML/Window1.xaml#xmlnamespacemapping)]
 [!code-xml[XmlnsBind#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBind/CS/Window1.xaml#xmlnamespacemapping)]  
  
 指定した <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> は、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ソースで使用されているものと一致する必要はありません。[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ソースでプレフィックスが変更されても、マッピングは機能します。  
  
 この例では、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データのソースが Web サービスになっていますが、<xref:System.Windows.Data.XmlNamespaceMapping> 要素は、埋め込まれたファイルのインライン [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] または [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データでも機能します。  
  
## 参照  
 [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)