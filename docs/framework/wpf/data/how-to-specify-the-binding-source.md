---
title: '方法 : バインディング ソースを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 333a85bc59ded3fd42bef6aff5845c9a6ddeb49b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556875"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="d3d8d-102">方法 : バインディング ソースを指定する</span><span class="sxs-lookup"><span data-stu-id="d3d8d-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="d3d8d-103">データ バインディングでは、バインド ソース オブジェクトとは、そこからデータを取得するオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="d3d8d-104">このトピックでは、バインド ソースを指定するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3d8d-105">例</span><span class="sxs-lookup"><span data-stu-id="d3d8d-105">Example</span></span>  
 <span data-ttu-id="d3d8d-106">複数のプロパティを共通ソースにバインドする場合は、`DataContext` を使用できます。これは、すべてのデータ バインド プロパティが共通ソースを継承するスコープを確立するための便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="d3d8d-107">次の例では、アプリケーションのルート要素にデータ コンテキストが確立されます。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="d3d8d-108">これにより、すべての子要素がそのデータ コンテキストを継承することができます。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="d3d8d-109">バインドするデータは、マッピングを通して直接参照され、リソース キー `incomeDataSource` が与えられるカスタム データ クラス `NetIncome` から取得されます。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="d3d8d-110">次の例は、`NetIncome` クラスの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  <span data-ttu-id="d3d8d-111">上記の例では、マークアップ内のオブジェクトをインスタンス化し、それをリソースとして使用しています。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="d3d8d-112">コードで既にインスタンス化されているオブジェクトにバインドする場合は、`DataContext` プロパティをプログラムで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="d3d8d-113">例については、「[方法: XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-113">For an example, see [Make Data Available for Binding in XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="d3d8d-114">個々のバインドでソースを明示的に指定する場合は、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="d3d8d-115">これらは、継承されたデータ コンテキストに優先します。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="d3d8d-116">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d3d8d-116">Property</span></span>|<span data-ttu-id="d3d8d-117">説明</span><span class="sxs-lookup"><span data-stu-id="d3d8d-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="d3d8d-118">オブジェクトのインスタンスにソースを設定するには、このプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="d3d8d-119">いくつかのプロパティは、同じデータ コンテキストを継承でスコープを確立するの機能を必要としない場合は、使用することができます、<xref:System.Windows.Data.Binding.Source%2A>プロパティの代わりに、`DataContext`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="d3d8d-120">詳細については、「<xref:System.Windows.Data.Binding.Source%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="d3d8d-121">これは、バインディング ターゲットの場所を基準としてソースを指定する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="d3d8d-122">このプロパティを使用できる一般的なシナリオとして、要素の 1 つのプロパティを同じ要素の別のプロパティにバインドする場合や、スタイルまたはテンプレート内のバインドを定義する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="d3d8d-123">詳細については、「<xref:System.Windows.Data.Binding.RelativeSource%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="d3d8d-124">バインド先の要素を表す文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="d3d8d-125">これは、アプリケーションの別の要素のプロパティにバインドする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="d3d8d-126">使用する場合など、 <xref:System.Windows.Controls.Slider> 、アプリケーションの他のコントロールの高さを制御する、またはバインドする場合、 <xref:System.Windows.Controls.ContentControl.Content%2A> 、コントロールを<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="d3d8d-127">詳細については、「<xref:System.Windows.Data.Binding.ElementName%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d8d-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3d8d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3d8d-128">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d3d8d-129">プロパティ値の継承</span><span class="sxs-lookup"><span data-stu-id="d3d8d-129">Property Value Inheritance</span></span>](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [<span data-ttu-id="d3d8d-130">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="d3d8d-130">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="d3d8d-131">バインディング宣言の概要</span><span class="sxs-lookup"><span data-stu-id="d3d8d-131">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="d3d8d-132">方法トピック</span><span class="sxs-lookup"><span data-stu-id="d3d8d-132">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
