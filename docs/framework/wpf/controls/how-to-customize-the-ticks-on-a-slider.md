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
# <a name="how-to-customize-the-ticks-on-a-slider"></a>方法 : スライダーの目盛りをカスタマイズする
この例を作成する方法を示しています、<xref:System.Windows.Controls.Slider>目盛りを持つコントロール。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.Primitives.TickBar>を設定するときに表示、<xref:System.Windows.Controls.Slider.TickPlacement%2A>プロパティ以外の値を<xref:System.Windows.Controls.Primitives.TickPlacement.None>、これは、既定値です。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Slider>で、<xref:System.Windows.Controls.Primitives.TickBar>軸目盛りマークを表示します。 <xref:System.Windows.Controls.Slider.TickPlacement%2A>と<xref:System.Windows.Controls.Slider.TickFrequency%2A>プロパティは、目盛り、およびそれらの間の間隔の場所を定義します。 移動すると、 <xref:System.Windows.Controls.Primitives.Thumb>、ツール ヒントの値を表示する、<xref:System.Windows.Controls.Slider>です。 <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A>プロパティは、ツールヒントの実行く先を定義します。 <xref:System.Windows.Controls.Primitives.Thumb>の動きが目盛りの位置に対応しているため<xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A>に設定されている`true`です。  
  
 次の例を使用する方法を示しています、<xref:System.Windows.Controls.Slider.Ticks%2A>ティックに沿ってマークを作成するプロパティ、<xref:System.Windows.Controls.Slider>不定期にします。  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [スライダーの操作方法に関するトピック](http://msdn.microsoft.com/en-us/534be86c-afb2-425d-8186-631278a9925e)
