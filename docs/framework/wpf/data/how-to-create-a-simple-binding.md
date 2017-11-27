---
title: "方法 : 簡単なバインディングを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a61844f917539f5d5e7c99299c8a33f4aa18450f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="21214-102">方法 : 簡単なバインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="21214-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="21214-103">この例は、単純なを作成する方法を示します<xref:System.Windows.Data.Binding>です。</span><span class="sxs-lookup"><span data-stu-id="21214-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21214-104">例</span><span class="sxs-lookup"><span data-stu-id="21214-104">Example</span></span>  
 <span data-ttu-id="21214-105">この例では必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。</span><span class="sxs-lookup"><span data-stu-id="21214-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="21214-106">`Person`オブジェクトがという名前空間で定義されている`SDKSample`です。</span><span class="sxs-lookup"><span data-stu-id="21214-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="21214-107">次の例のインスタンスを作成、`Person`オブジェクトを`PersonName`のプロパティの値`Joe`です。</span><span class="sxs-lookup"><span data-stu-id="21214-107">The following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="21214-108">これには、`Resources`セクションし、割り当てられている、`x:Key`です。</span><span class="sxs-lookup"><span data-stu-id="21214-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xaml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 <span data-ttu-id="21214-109">バインドする、`PersonName`プロパティは、次を実行するとします。</span><span class="sxs-lookup"><span data-stu-id="21214-109">To bind to the `PersonName` property you would do the following:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="21214-110">その結果、<xref:System.Windows.Controls.TextBlock>値"Joe"とともに表示されます。</span><span class="sxs-lookup"><span data-stu-id="21214-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21214-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="21214-111">See Also</span></span>  
 [<span data-ttu-id="21214-112">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="21214-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="21214-113">方法トピック</span><span class="sxs-lookup"><span data-stu-id="21214-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
