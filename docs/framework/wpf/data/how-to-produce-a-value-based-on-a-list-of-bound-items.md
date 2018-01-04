---
title: "方法 : バインドされた項目の一覧に基づいて値を生成する"
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
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3987690a1acb180ee22fa02e399accd9c5d481d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="b7e56-102">方法 : バインドされた項目の一覧に基づいて値を生成する</span><span class="sxs-lookup"><span data-stu-id="b7e56-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="b7e56-103"><xref:System.Windows.Data.MultiBinding>使用すると、ソースのプロパティの一覧にバインディング ターゲット プロパティをバインドし、指定された入力の値を生成するロジックを適用できます。</span><span class="sxs-lookup"><span data-stu-id="b7e56-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="b7e56-104">この例は、使用する方法を示します<xref:System.Windows.Data.MultiBinding>です。</span><span class="sxs-lookup"><span data-stu-id="b7e56-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7e56-105">例</span><span class="sxs-lookup"><span data-stu-id="b7e56-105">Example</span></span>  
 <span data-ttu-id="b7e56-106">次の例では、`NameListData` は、`PersonName` オブジェクトのコレクションを参照します。このオブジェクトは、`firstName` と `lastName` の 2 つのプロパティを含みます。</span><span class="sxs-lookup"><span data-stu-id="b7e56-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="b7e56-107">次のコード生成、<xref:System.Windows.Controls.TextBlock>最後の名前を持つ人物の姓と名の先頭を示すです。</span><span class="sxs-lookup"><span data-stu-id="b7e56-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="b7e56-108">姓が先の形式を生成する方法を理解するには、次に示す `NameConverter` の実装をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b7e56-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="b7e56-109">`NameConverter` は、<xref:System.Windows.Data.IMultiValueConverter> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b7e56-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="b7e56-110">`NameConverter` は、個々のバインディングから値を受け取り、それらを値のオブジェクト配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="b7e56-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="b7e56-111">順序、<xref:System.Windows.Data.Binding>下にある要素が表示されます、<xref:System.Windows.Data.MultiBinding>要素は、それらの値が配列に格納されている順序。</span><span class="sxs-lookup"><span data-stu-id="b7e56-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="b7e56-112">値、<xref:System.Windows.Data.MultiBinding.ConverterParameter%2A>属性がのパラメーターの引数によって参照される、<xref:System.Windows.Data.MultiBinding.Converter%2A>メソッドで、名前を書式設定する方法を決定するパラメーターの切り替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="b7e56-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e56-113">参照</span><span class="sxs-lookup"><span data-stu-id="b7e56-113">See Also</span></span>  
 [<span data-ttu-id="b7e56-114">バインドされたデータを変換する</span><span class="sxs-lookup"><span data-stu-id="b7e56-114">Convert Bound Data</span></span>](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [<span data-ttu-id="b7e56-115">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="b7e56-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="b7e56-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="b7e56-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
