---
title: "方法 : スライダーの目盛りをカスタマイズする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 610fa829b4d2c49d0c3ae760f5601610bd2a0c46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="6c7cd-102">方法 : スライダーの目盛りをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="6c7cd-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="6c7cd-103">この例を作成する方法を示しています、<xref:System.Windows.Controls.Slider>目盛りを持つコントロール。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c7cd-104">例</span><span class="sxs-lookup"><span data-stu-id="6c7cd-104">Example</span></span>  
 <span data-ttu-id="6c7cd-105"><xref:System.Windows.Controls.Primitives.TickBar>を設定するときに表示、<xref:System.Windows.Controls.Slider.TickPlacement%2A>プロパティ以外の値を<xref:System.Windows.Controls.Primitives.TickPlacement.None>、これは、既定値です。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="6c7cd-106">次の例を作成する方法を示しています、<xref:System.Windows.Controls.Slider>で、<xref:System.Windows.Controls.Primitives.TickBar>軸目盛りマークを表示します。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="6c7cd-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A>と<xref:System.Windows.Controls.Slider.TickFrequency%2A>プロパティは、目盛り、およびそれらの間の間隔の場所を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="6c7cd-108">移動すると、 <xref:System.Windows.Controls.Primitives.Thumb>、ツール ヒントの値を表示する、<xref:System.Windows.Controls.Slider>です。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="6c7cd-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>プロパティは、ツールヒントの実行く先を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="6c7cd-110"><xref:System.Windows.Controls.Primitives.Thumb>の動きが目盛りの位置に対応しているため<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>に設定されている`true`です。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="6c7cd-111">次の例を使用する方法を示しています、<xref:System.Windows.Controls.Slider.Ticks%2A>ティックに沿ってマークを作成するプロパティ、<xref:System.Windows.Controls.Slider>不定期にします。</span><span class="sxs-lookup"><span data-stu-id="6c7cd-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6c7cd-112">参照</span><span class="sxs-lookup"><span data-stu-id="6c7cd-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="6c7cd-113">スライダーの操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="6c7cd-113">Slider How-to Topics</span></span>](http://msdn.microsoft.com/en-us/534be86c-afb2-425d-8186-631278a9925e)
