---
title: "方法 : XAML でデータをバインディング可能にする"
ms.custom: 
ms.date: 01/29/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f4e8e785b246e191ae8052f676331ea116b8c0d
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>方法 : XAML でデータをバインディング可能にする
このトピックで使用できるようにデータのバインドでさまざまな方法について説明します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]アプリケーションのニーズに応じて、します。  
  
## <a name="example"></a>例  
 ある場合、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクトにバインドするには[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、使用できるように、オブジェクトのバインディングでは、リソースとして定義し、1 つの方法、`x:Key`です。 次の例で必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。 `Person`強調表示されたを含む行で示されているオブジェクト、`<src>`と呼ばれる、名前空間に要素が定義されている`SDKSample`です。  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 バインドできます、<xref:System.Windows.Controls.TextBlock>コントロール内のオブジェクトを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で強調表示された行が含まれています、`<TextBlock>`要素に示します。 
  
 また、使用することができます、<xref:System.Windows.Data.ObjectDataProvider>次の例のように、クラス。  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 バインディングを定義する、強調表示された行を含むと同じよう、`<TextBlock>`要素に示します。  
  
 結果では、この例では、同じ: がある、<xref:System.Windows.Controls.TextBlock>テキスト コンテンツ付き`Joe`します。 ただし、<xref:System.Windows.Data.ObjectDataProvider>クラス、メソッドの結果にバインドする機能などの機能を提供します。 使用することができます、<xref:System.Windows.Data.ObjectDataProvider>クラスの場合は、機能を提供する必要があります。  
  
 ただし、既に作成されているオブジェクトにバインドする場合は、設定する必要が、`DataContext`コードでは、次の例のようにします。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.XmlDataProvider>クラスを参照してください[XMLDataProvider および XPath クエリを使用して XML データにバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)です。 アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.ObjectDataProvider>クラスを参照してください[XDocument、XElement、または LINQ に XML クエリの結果のバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)です。  
  
 バインドするデータを指定するさまざまな方法について、次を参照してください。[バインディング ソースを指定](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)です。 どのような種類のデータにバインドすることができます、または独自に実装する方法について[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、バインディングのオブジェクトを参照してください[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)です。  
  
## <a name="see-also"></a>参照  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
