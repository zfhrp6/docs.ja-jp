---
title: "方法 : カスタム パネル要素を作成する"
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
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eacc5435e259c20c25b64d6e82c33d07338602a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="af69b-102">方法 : カスタム パネル要素を作成する</span><span class="sxs-lookup"><span data-stu-id="af69b-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="af69b-103">例</span><span class="sxs-lookup"><span data-stu-id="af69b-103">Example</span></span>  
 <span data-ttu-id="af69b-104">この例の既定のレイアウト動作をオーバーライドする方法を示しています、<xref:System.Windows.Controls.Panel>要素から派生したカスタム レイアウト要素を作成および<xref:System.Windows.Controls.Panel>です。</span><span class="sxs-lookup"><span data-stu-id="af69b-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="af69b-105">例では、定義の単純なカスタム<xref:System.Windows.Controls.Panel>と呼ばれる要素`PlotPanel`、子要素に従って 2 つハード コーディングされた x 座標と y 座標を配置します。</span><span class="sxs-lookup"><span data-stu-id="af69b-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="af69b-106">この例では`x`と`y`に設定されて`50`。 したがって、すべての子要素は、x と y でその場所に配置軸です。</span><span class="sxs-lookup"><span data-stu-id="af69b-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="af69b-107">ユーザー設定を実装する<xref:System.Windows.Controls.Panel>動作、この例では、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="af69b-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="af69b-108">各メソッドを返します、<xref:System.Windows.Size>配置し、子要素をレンダリングするために必要なデータです。</span><span class="sxs-lookup"><span data-stu-id="af69b-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="af69b-109">参照</span><span class="sxs-lookup"><span data-stu-id="af69b-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="af69b-110">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="af69b-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="af69b-111">カスタム コンテンツの折り返しパネル サンプルを作成します。</span><span class="sxs-lookup"><span data-stu-id="af69b-111">Create a Custom Content-Wrapping Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159979)
