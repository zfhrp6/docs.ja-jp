---
title: "方法 : XAML でデータをバインディング可能にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c342f0d635a9220a88a2af79c76e2c1580dee2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>方法 : XAML でデータをバインディング可能にする
このトピックで使用できるようにデータのバインドでさまざまな方法について説明します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]アプリケーションのニーズに応じて、します。  
  
## <a name="example"></a>例  
 ある場合、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクトにバインドするには[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、使用できるように、オブジェクトのバインディングでは、リソースとして定義し、1 つの方法、`x:Key`です。 次の例で必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。 `Person`オブジェクトがという名前空間で定義されている`SDKSample`です。  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 内のオブジェクトにバインドすることができますし、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の次の例に示すようにします。  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 また、使用することができます、<xref:System.Windows.Data.ObjectDataProvider>クラスは、次の例のようにします。  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 バインディングを定義すると同じ方法。  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 結果では、この例では、同じ: がある、<xref:System.Windows.Controls.TextBlock>テキスト コンテンツ付き`Joe`します。 ただし、<xref:System.Windows.Data.ObjectDataProvider>クラス、メソッドの結果にバインドする機能などの機能を提供します。 使用することができます、<xref:System.Windows.Data.ObjectDataProvider>クラスの場合は、機能を提供する必要があります。  
  
 ただし、既に作成されているオブジェクトにバインドする場合は、設定する必要が、`DataContext`コードでは、次の例のようにします。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.XmlDataProvider>クラスを参照してください[XMLDataProvider および XPath クエリを使用して XML データにバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)です。 アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.ObjectDataProvider>クラスを参照してください[XDocument、XElement、または LINQ に XML クエリの結果のバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)です。  
  
 バインドするデータを指定するさまざまな方法について、次を参照してください。[バインディング ソースを指定](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)です。 どのような種類のデータにバインドすることができます、または独自に実装する方法について[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、バインディングのオブジェクトを参照してください[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)です。  
  
## <a name="see-also"></a>参照  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
