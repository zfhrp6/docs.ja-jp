---
title: "方法 : 装飾を実装する"
ms.custom: 
ms.date: 03/30/2017
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
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76bceae5b69fad4c217127617309484edcf18108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="bd418-102">方法 : 装飾を実装する</span><span class="sxs-lookup"><span data-stu-id="bd418-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="bd418-103">この例では、最小限の装飾の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="bd418-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="bd418-104">実装についてのメモ</span><span class="sxs-lookup"><span data-stu-id="bd418-104">Notes for Implementers</span></span>  
 <span data-ttu-id="bd418-105">装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="bd418-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="bd418-106">レンダリング動作を実装する一般的な方法は、上書きする、<xref:System.Windows.UIElement.OnRender%2A>メソッドと 1 つ以上を使用して<xref:System.Windows.Media.DrawingContext>に応じて (この例で示した部分) の装飾のビジュアルを表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bd418-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd418-107">例</span><span class="sxs-lookup"><span data-stu-id="bd418-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="bd418-108">説明</span><span class="sxs-lookup"><span data-stu-id="bd418-108">Description</span></span>  
 <span data-ttu-id="bd418-109">カスタムの装飾が抽象から継承するクラスを実装することによって作成された<xref:System.Windows.Documents.Adorner>クラスです。</span><span class="sxs-lookup"><span data-stu-id="bd418-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="bd418-110">例の装飾は、の<xref:System.Windows.UIElement>をオーバーライドすることで、円、<xref:System.Windows.UIElement.OnRender%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bd418-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bd418-111">コード</span><span class="sxs-lookup"><span data-stu-id="bd418-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="bd418-112">参照</span><span class="sxs-lookup"><span data-stu-id="bd418-112">See Also</span></span>  
 [<span data-ttu-id="bd418-113">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="bd418-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
