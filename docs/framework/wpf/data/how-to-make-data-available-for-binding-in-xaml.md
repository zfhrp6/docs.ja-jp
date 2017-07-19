---
title: "方法 : XAML でデータをバインディング可能にする | Microsoft Docs"
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
  - "バインド (データを), データを利用可能にする"
  - "データ バインディング, データをバインディング可能にする"
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : XAML でデータをバインディング可能にする
ここでは、アプリケーションでの必要に応じて、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でデータをバインディング可能にするさまざまな方法について説明します。  
  
## 使用例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] から[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトにバインドする場合、そのオブジェクトをバインディング可能にする方法の 1 つは、それをリソースとして定義し、`x:Key` を指定することです。  次の例では、`PersonName` という名前の文字列プロパティを持つ `Person` オブジェクトがあります。  この `Person` オブジェクトは、`SDKSample` という名前空間で定義されます。  
  
 [!code-xml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 その後、次の例に示すように、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でそのオブジェクトにバインドします。  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 または、次の例に示すように、<xref:System.Windows.Data.ObjectDataProvider> クラスを使用することもできます。  
  
 [!code-xml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 同じようにバインディングを定義します。  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 ここに示す例では、結果は同じになります。`Joe` というテキスト コンテンツを持つ <xref:System.Windows.Controls.TextBlock> が得られます。  これに対し、<xref:System.Windows.Data.ObjectDataProvider> クラスは、メソッドの結果にバインドするなどの機能を提供します。  <xref:System.Windows.Data.ObjectDataProvider> クラスが提供する機能が必要な場合は、そちらを使用してください。  
  
 ただし、既に作成されているオブジェクトにバインドする場合は、次の例に示すように、コード内で `DataContext` を設定する必要があります。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <xref:System.Windows.Data.XmlDataProvider> クラスを使用して、バインディングで使用する [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにアクセスするには、「[XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。  <xref:System.Windows.Data.ObjectDataProvider> クラスを使用して、バインディングで使用する [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにアクセスするには、「[XDocument、XElement、または LINQ for XML クエリの結果にバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)」を参照してください。  
  
 バインド先とするデータを指定するさまざまな方法については、「[バインディング ソースを指定する](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)」を参照してください。  バインド先として指定できるデータの型、またはバインディング用に独自の[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトを実装する方法については、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」を参照してください。  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)