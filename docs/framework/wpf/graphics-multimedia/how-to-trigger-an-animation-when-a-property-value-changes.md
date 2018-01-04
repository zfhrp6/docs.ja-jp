---
title: "方法 : プロパティ値が変化したときにアニメーションをトリガーする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0eb4542d8baf86f01417eb1925028a00471b40b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>方法 : プロパティ値が変化したときにアニメーションをトリガーする
この例を使用する方法を示しています、<xref:System.Windows.Trigger>を開始する、<xref:System.Windows.Media.Animation.Storyboard>プロパティの値が変更されたとき。 使用することができます、<xref:System.Windows.Trigger>内、 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、または<xref:System.Windows.DataTemplate>です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Trigger>アニメーション化する、<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Button>ときにその<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティになります`true`です。  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 プロパティによって適用されたアニメーション<xref:System.Windows.Trigger>オブジェクトよりも複雑な方法で動作しますが<xref:System.Windows.EventTrigger>アニメーションまたはアニメーションを使用して開始<xref:System.Windows.Media.Animation.Storyboard>メソッドです。  「ハンドオフ」アニメーションを使用して他の定義、<xref:System.Windows.Trigger>使用して、オブジェクトが作成<xref:System.Windows.EventTrigger>およびアニメーションのメソッドによってトリガーされます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Trigger>  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
