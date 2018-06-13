---
title: '方法 : XAML でデータをバインディング可能にする'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: dd66fb2f96f8c42fea36afaeda0aaf35a2adbace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557330"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="c0efe-102">方法 : XAML でデータをバインディング可能にする</span><span class="sxs-lookup"><span data-stu-id="c0efe-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="c0efe-103">このトピックで使用できるようにデータのバインドでさまざまな方法について説明します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]アプリケーションのニーズに応じて、します。</span><span class="sxs-lookup"><span data-stu-id="c0efe-103">This topic discusses the different ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0efe-104">例</span><span class="sxs-lookup"><span data-stu-id="c0efe-104">Example</span></span>  
 <span data-ttu-id="c0efe-105">ある場合、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクトにバインドするには[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、使用できるように、オブジェクトのバインディングでは、リソースとして定義し、1 つの方法、`x:Key`です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="c0efe-106">次の例で必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="c0efe-107">`Person`強調表示されたを含む行で示されているオブジェクト、`<src>`と呼ばれる、名前空間に要素が定義されている`SDKSample`です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-107">The `Person` object, which is shown by the highlighted line that contains the `<src>` element, is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="c0efe-108">バインドできます、<xref:System.Windows.Controls.TextBlock>コントロール内のオブジェクトを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で強調表示された行が含まれています、`<TextBlock>`要素に示します。</span><span class="sxs-lookup"><span data-stu-id="c0efe-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="c0efe-109">また、使用することができます、<xref:System.Windows.Data.ObjectDataProvider>次の例のように、クラス。</span><span class="sxs-lookup"><span data-stu-id="c0efe-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="c0efe-110">バインディングを定義する、強調表示された行を含むと同じよう、`<TextBlock>`要素に示します。</span><span class="sxs-lookup"><span data-stu-id="c0efe-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="c0efe-111">結果では、この例では、同じ: がある、<xref:System.Windows.Controls.TextBlock>テキスト コンテンツ付き`Joe`します。</span><span class="sxs-lookup"><span data-stu-id="c0efe-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="c0efe-112">ただし、<xref:System.Windows.Data.ObjectDataProvider>クラス、メソッドの結果にバインドする機能などの機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="c0efe-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="c0efe-113">使用することができます、<xref:System.Windows.Data.ObjectDataProvider>クラスの場合は、機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0efe-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="c0efe-114">ただし、既に作成されているオブジェクトにバインドする場合は、設定する必要が、`DataContext`コードでは、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="c0efe-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="c0efe-115">アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.XmlDataProvider>クラスを参照してください[XMLDataProvider および XPath クエリを使用して XML データにバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="c0efe-116">アクセスする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データを使用してバインディングを<xref:System.Windows.Data.ObjectDataProvider>クラスを参照してください[XDocument、XElement、または LINQ に XML クエリの結果のバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="c0efe-117">バインドするデータを指定するさまざまな方法について、次を参照してください。[バインディング ソースを指定](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-117">For information about the different ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="c0efe-118">どのような種類のデータにバインドすることができます、または独自に実装する方法について[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、バインディングのオブジェクトを参照してください[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0efe-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0efe-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0efe-119">See Also</span></span>  
 [<span data-ttu-id="c0efe-120">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="c0efe-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c0efe-121">方法トピック</span><span class="sxs-lookup"><span data-stu-id="c0efe-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
