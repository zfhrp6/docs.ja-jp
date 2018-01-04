---
title: "方法 : インクを回転させる"
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
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45a65a8d6c7d506cf74d98667527b8b5548af038
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-ink"></a><span data-ttu-id="9038b-102">方法 : インクを回転させる</span><span class="sxs-lookup"><span data-stu-id="9038b-102">How to: Rotate Ink</span></span>
## <a name="example"></a><span data-ttu-id="9038b-103">例</span><span class="sxs-lookup"><span data-stu-id="9038b-103">Example</span></span>  
 <span data-ttu-id="9038b-104">次の例からのインクをコピーする、<xref:System.Windows.Controls.InkCanvas>を<xref:System.Windows.Controls.Canvas>を格納している、<xref:System.Windows.Controls.InkPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="9038b-104">The following example copies the ink from an <xref:System.Windows.Controls.InkCanvas> to a <xref:System.Windows.Controls.Canvas> that contains an <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="9038b-105">アプリケーションでは、インクをコピーするときにも回転インク時計回りに 90 ° します。</span><span class="sxs-lookup"><span data-stu-id="9038b-105">When the application copies the ink, it also rotates the ink 90 degrees clockwise.</span></span>  
  
 [!code-xaml[HowToRotateInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="9038b-106">例</span><span class="sxs-lookup"><span data-stu-id="9038b-106">Example</span></span>  
 <span data-ttu-id="9038b-107">次の例は、カスタム<xref:System.Windows.Documents.Adorner>にストロークを回転する、<xref:System.Windows.Controls.InkPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="9038b-107">The following example is a custom <xref:System.Windows.Documents.Adorner> that rotates the strokes on an <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[AdornerForStrokes#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 <span data-ttu-id="9038b-108">次の例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義するファイル、<xref:System.Windows.Controls.InkPresenter>インクに設定します。</span><span class="sxs-lookup"><span data-stu-id="9038b-108">The following example is a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that defines an <xref:System.Windows.Controls.InkPresenter> and populates it with ink.</span></span> <span data-ttu-id="9038b-109">`Window_Loaded`イベント ハンドラーを追加するカスタムの装飾、<xref:System.Windows.Controls.InkPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="9038b-109">The `Window_Loaded` event handler adds the custom adorner to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-xaml[AdornerForStrokes#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
