---
title: "方法 : Canvas の添付プロパティを使用して子要素を配置する"
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
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5314f39c3012826f25fa6c64baf7eb8e42329f58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="04dac-102">方法 : Canvas の添付プロパティを使用して子要素を配置する</span><span class="sxs-lookup"><span data-stu-id="04dac-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="04dac-103">この例は、の添付プロパティを使用する方法を示しています。<xref:System.Windows.Controls.Canvas>子要素を配置します。</span><span class="sxs-lookup"><span data-stu-id="04dac-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04dac-104">例</span><span class="sxs-lookup"><span data-stu-id="04dac-104">Example</span></span>  
 <span data-ttu-id="04dac-105">次の例 4<xref:System.Windows.Controls.Button>要素を親の子要素として<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="04dac-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="04dac-106">各子要素の個別の添付プロパティを表す<xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>、 <xref:System.Windows.Controls.Canvas.Left%2A>、 <xref:System.Windows.Controls.Canvas.Right%2A>、および<xref:System.Windows.Controls.Canvas.Top%2A>です。</span><span class="sxs-lookup"><span data-stu-id="04dac-106">Each child element represents a distinct attached property of <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span> <span data-ttu-id="04dac-107">各<xref:System.Windows.Controls.Button>が親を基準に配置されている<xref:System.Windows.Controls.Canvas>とその割り当てられたプロパティの値に従って、します。</span><span class="sxs-lookup"><span data-stu-id="04dac-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="04dac-108">参照</span><span class="sxs-lookup"><span data-stu-id="04dac-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="04dac-109">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="04dac-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="04dac-110">方法トピック</span><span class="sxs-lookup"><span data-stu-id="04dac-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="04dac-111">添付プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="04dac-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
