---
title: "方法 : 装飾を実装する"
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
helpviewer_keywords: adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3f69fee64ea65e8d49cce523c85669993cc6bce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="2a2f5-102">方法 : 装飾を実装する</span><span class="sxs-lookup"><span data-stu-id="2a2f5-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="2a2f5-103">この例では、最小限の装飾の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="2a2f5-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="2a2f5-104">実装についてのメモ</span><span class="sxs-lookup"><span data-stu-id="2a2f5-104">Notes for Implementers</span></span>  
 <span data-ttu-id="2a2f5-105">装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="2a2f5-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="2a2f5-106">レンダリング動作を実装する一般的な方法は、上書きする、<xref:System.Windows.UIElement.OnRender%2A>メソッドと 1 つ以上を使用して<xref:System.Windows.Media.DrawingContext>に応じて (この例で示した部分) の装飾のビジュアルを表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2a2f5-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a2f5-107">例</span><span class="sxs-lookup"><span data-stu-id="2a2f5-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2a2f5-108">説明</span><span class="sxs-lookup"><span data-stu-id="2a2f5-108">Description</span></span>  
 <span data-ttu-id="2a2f5-109">カスタムの装飾が抽象から継承するクラスを実装することによって作成された<xref:System.Windows.Documents.Adorner>クラスです。</span><span class="sxs-lookup"><span data-stu-id="2a2f5-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="2a2f5-110">例の装飾は、の<xref:System.Windows.UIElement>をオーバーライドすることで、円、<xref:System.Windows.UIElement.OnRender%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2a2f5-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2a2f5-111">コード</span><span class="sxs-lookup"><span data-stu-id="2a2f5-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="2a2f5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a2f5-112">See Also</span></span>  
 [<span data-ttu-id="2a2f5-113">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="2a2f5-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
