---
title: '方法 : プロパティ値が変化したときにアニメーションをトリガーする'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: f127f00445a587ee097faa6bed28e124690de10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561318"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>方法 : プロパティ値が変化したときにアニメーションをトリガーする
この例を使用する方法を示しています、<xref:System.Windows.Trigger>を開始する、<xref:System.Windows.Media.Animation.Storyboard>プロパティの値が変更されたとき。 使用することができます、<xref:System.Windows.Trigger>内、 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、または<xref:System.Windows.DataTemplate>です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Trigger>アニメーション化する、<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Button>ときにその<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティになります`true`です。  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 プロパティによって適用されたアニメーション<xref:System.Windows.Trigger>オブジェクトよりも複雑な方法で動作しますが<xref:System.Windows.EventTrigger>アニメーションまたはアニメーションを使用して開始<xref:System.Windows.Media.Animation.Storyboard>メソッドです。  「ハンドオフ」アニメーションを使用して他の定義、<xref:System.Windows.Trigger>使用して、オブジェクトが作成<xref:System.Windows.EventTrigger>およびアニメーションのメソッドによってトリガーされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Trigger>  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
