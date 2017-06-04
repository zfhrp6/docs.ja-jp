---
title: "方法 : XDocument、XElement、または LINQ for XML クエリの結果にバインドする | Microsoft Docs"
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
  - "データ バインディング [WPF], バインド (XDocument に)"
  - "データ バインディング [WPF], バインド (XElement に)"
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 方法 : XDocument、XElement、または LINQ for XML クエリの結果にバインドする
この例は、<xref:System.Xml.Linq.XDocument> を使用して XML データを <xref:System.Windows.Controls.ItemsControl> にバインドする方法を示しています。  
  
## 使用例  
 次の XAML コードは、<xref:System.Windows.Controls.ItemsControl> を定義し、`Planet` 型のデータ用のデータ テンプレートを `http://planetsNS` XML 名前空間に含めます。  名前空間を占有する XML データ型では、名前空間をかっこで囲んで含める必要があります。また、その XML データ型が XAML マークアップ拡張機能が出現する可能性がある場所に出現する場合は、名前空間の前に、かっこのエスケープ シーケンスを使用して指定する必要があります。  このコードは、<xref:System.Xml.Linq.XElement> クラスの <xref:System.Xml.Linq.XContainer.Element%2A> メソッドと <xref:System.Xml.Linq.XElement.Attribute%2A> メソッドに対応する動的プロパティにバインドします。  動的プロパティによって、XAML がこれらのメソッドの名前を共有する動的プロパティにバインドできます。  詳細については、「[LINQ to XML の動的プロパティ](../Topic/LINQ%20to%20XML%20Dynamic%20Properties.md)」を参照してください。  XML 用の既定の名前空間宣言が属性名には適用されないことに注意してください。  
  
 [!code-xml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 次の C\# コードは、<xref:System.Xml.Linq.XDocument.Load%2A> を呼び出し、スタック パネルのデータ コンテキストを `http://planetsNS` XML 名前空間内の `SolarSystemPlanets` という名前の要素のすべてのサブ要素に設定します。  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 XML データは、<xref:System.Windows.Data.ObjectDataProvider> を使用して XAML リソースとして格納することができます。  コード例全体については、「[L2DBForm.xaml ソース コード](../Topic/L2DBForm.xaml%20Source%20Code.md)」を参照してください。  次の例は、コードでデータ コンテキストをオブジェクト リソースに設定する方法を示しています。  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> および <xref:System.Xml.Linq.XElement.Attribute%2A> にマップされる動的プロパティによって、XAML 内での柔軟性が提供されます。  コードを LINQ for XML クエリの結果にバインドすることもできます。  この例では、要素の値によって並べられたクエリ結果にバインドします。  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## 参照  
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [LINQ to XML による WPF のデータ バインドの概要](../Topic/WPF%20Data%20Binding%20with%20LINQ%20to%20XML%20Overview.md)   
 [LINQ to XML を使用した WPF のデータ バインドの例](../Topic/WPF%20Data%20Binding%20Using%20LINQ%20to%20XML%20Example.md)   
 [LINQ to XML の動的プロパティ](../Topic/LINQ%20to%20XML%20Dynamic%20Properties.md)