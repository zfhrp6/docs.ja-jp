---
title: "方法 : 簡単なバインディングを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="e9d18-102">方法 : 簡単なバインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="e9d18-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="e9d18-103">この例は、単純なを作成する方法を示します<xref:System.Windows.Data.Binding>です。</span><span class="sxs-lookup"><span data-stu-id="e9d18-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9d18-104">例</span><span class="sxs-lookup"><span data-stu-id="e9d18-104">Example</span></span>  
 <span data-ttu-id="e9d18-105">この例では必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。</span><span class="sxs-lookup"><span data-stu-id="e9d18-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="e9d18-106">`Person`オブジェクトがという名前空間で定義されている`SDKSample`です。</span><span class="sxs-lookup"><span data-stu-id="e9d18-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="e9d18-107">強調表示された行を含む、`<src>`次の例で要素をインスタンス化、`Person`オブジェクトを`PersonName`のプロパティの値`Joe`です。</span><span class="sxs-lookup"><span data-stu-id="e9d18-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="e9d18-108">これには、`Resources`セクションし、割り当てられている、`x:Key`です。</span><span class="sxs-lookup"><span data-stu-id="e9d18-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="e9d18-109">強調表示された行を含む、`<TextBlock>`要素にバインドし、<xref:System.Windows.Controls.TextBlock>コントロールを`PersonName`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e9d18-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="e9d18-110">その結果、<xref:System.Windows.Controls.TextBlock>値"Joe"とともに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9d18-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d18-111">参照</span><span class="sxs-lookup"><span data-stu-id="e9d18-111">See Also</span></span>  
 [<span data-ttu-id="e9d18-112">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="e9d18-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e9d18-113">方法トピック</span><span class="sxs-lookup"><span data-stu-id="e9d18-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
