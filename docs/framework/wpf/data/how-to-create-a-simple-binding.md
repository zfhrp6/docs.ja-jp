---
title: '方法 : 簡単なバインディングを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555020"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="4ffb3-102">方法 : 簡単なバインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="4ffb3-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="4ffb3-103">この例は、単純なを作成する方法を示します<xref:System.Windows.Data.Binding>です。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ffb3-104">例</span><span class="sxs-lookup"><span data-stu-id="4ffb3-104">Example</span></span>  
 <span data-ttu-id="4ffb3-105">この例では必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="4ffb3-106">`Person`オブジェクトがという名前空間で定義されている`SDKSample`です。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="4ffb3-107">強調表示された行を含む、`<src>`次の例で要素をインスタンス化、`Person`オブジェクトを`PersonName`のプロパティの値`Joe`です。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="4ffb3-108">これには、`Resources`セクションし、割り当てられている、`x:Key`です。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="4ffb3-109">強調表示された行を含む、`<TextBlock>`要素にバインドし、<xref:System.Windows.Controls.TextBlock>コントロールを`PersonName`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="4ffb3-110">その結果、<xref:System.Windows.Controls.TextBlock>値"Joe"とともに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ffb3-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffb3-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ffb3-111">See Also</span></span>  
 [<span data-ttu-id="4ffb3-112">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="4ffb3-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="4ffb3-113">方法トピック</span><span class="sxs-lookup"><span data-stu-id="4ffb3-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
