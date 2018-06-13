---
title: '方法 : バインドされたデータを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556641"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="18a18-102">方法 : バインドされたデータを変換する</span><span class="sxs-lookup"><span data-stu-id="18a18-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="18a18-103">この例では、バインディングで使用されているデータへの変換を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="18a18-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="18a18-104">バインド中にデータを変換するを実装するクラスを作成する必要があります、<xref:System.Windows.Data.IValueConverter>インターフェイスが含まれています、<xref:System.Windows.Data.IValueConverter.Convert%2A>と<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="18a18-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a18-105">例</span><span class="sxs-lookup"><span data-stu-id="18a18-105">Example</span></span>  
 <span data-ttu-id="18a18-106">次の例では、年、月、および日のみが表示されるように渡された日付値に変換する日付コンバーターの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="18a18-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="18a18-107">実装する場合、<xref:System.Windows.Data.IValueConverter>装飾を使用して実装することをお勧めは、インターフェイス、<xref:System.Windows.Data.ValueConversionAttribute>開発に示すために属性が次の例のように、変換に含まれるデータ型をツールします。</span><span class="sxs-lookup"><span data-stu-id="18a18-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="18a18-108">コンバーターを作成した後でリソースとして追加できる、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。</span><span class="sxs-lookup"><span data-stu-id="18a18-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="18a18-109">次の例では、 *src*先の名前空間にマップ*DateConverter*が定義されています。</span><span class="sxs-lookup"><span data-stu-id="18a18-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="18a18-110">最後に、次の構文を使用して、バインディングでコンバーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="18a18-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="18a18-111">次の例では、テキストのコンテンツ、<xref:System.Windows.Controls.TextBlock>にバインドされた*StartDate*、外部データ ソースのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="18a18-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="18a18-112">上記の例で参照されているスタイル リソースは、このトピックで示していないリソース セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="18a18-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a18-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="18a18-113">See Also</span></span>  
 [<span data-ttu-id="18a18-114">バインディングの検証の実装</span><span class="sxs-lookup"><span data-stu-id="18a18-114">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="18a18-115">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="18a18-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="18a18-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="18a18-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
