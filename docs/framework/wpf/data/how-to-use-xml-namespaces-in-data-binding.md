---
title: "方法 : データ バインドで XML 名前空間を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f98d174fd0bd8ea28c7b72cec25b5b16f2b76c51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="cff94-102">方法 : データ バインドで XML 名前空間を使用する</span><span class="sxs-lookup"><span data-stu-id="cff94-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="cff94-103">例</span><span class="sxs-lookup"><span data-stu-id="cff94-103">Example</span></span>  
 <span data-ttu-id="cff94-104">この例では、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] のバインディング ソースに指定された名前空間の処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cff94-104">This example shows how to handle namespaces specified in your [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] binding source.</span></span>  
  
 <span data-ttu-id="cff94-105">[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データに次の [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間定義がある場合:</span><span class="sxs-lookup"><span data-stu-id="cff94-105">If your [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data has the following [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace definition:</span></span>  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 <span data-ttu-id="cff94-106">使用することができます、<xref:System.Windows.Data.XmlNamespaceMapping>する名前空間にマップする要素、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>次の例のように、します。</span><span class="sxs-lookup"><span data-stu-id="cff94-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="cff94-107">使用してできます、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>を参照する、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間。</span><span class="sxs-lookup"><span data-stu-id="cff94-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace.</span></span> <span data-ttu-id="cff94-108"><xref:System.Windows.Controls.ListBox>この例で表示、*タイトル*と*dc:date*各*項目*です。</span><span class="sxs-lookup"><span data-stu-id="cff94-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 <span data-ttu-id="cff94-109">なお、<xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>で使用されるものと一致する必要はありませんを指定する、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ソース; で、プレフィックスが変更された場合、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ソース マッピングが正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="cff94-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source; if the prefix changes in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source your mapping still works.</span></span>  
  
 <span data-ttu-id="cff94-110">この例では、 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] web サービスでは、基になるが、<xref:System.Windows.Data.XmlNamespaceMapping>要素はインラインでも動作[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]または[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]埋め込みファイル内のデータ。</span><span class="sxs-lookup"><span data-stu-id="cff94-110">In this particular example, the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] or [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data in an embedded file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff94-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="cff94-111">See Also</span></span>  
 [<span data-ttu-id="cff94-112">XMLDataProvider と XPath クエリを使用して XML データにバインドする</span><span class="sxs-lookup"><span data-stu-id="cff94-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="cff94-113">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="cff94-113">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="cff94-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="cff94-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
