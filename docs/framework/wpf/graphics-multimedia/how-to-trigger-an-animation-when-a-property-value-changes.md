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
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="54db3-102">方法 : プロパティ値が変化したときにアニメーションをトリガーする</span><span class="sxs-lookup"><span data-stu-id="54db3-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="54db3-103">この例を使用する方法を示しています、<xref:System.Windows.Trigger>を開始する、<xref:System.Windows.Media.Animation.Storyboard>プロパティの値が変更されたとき。</span><span class="sxs-lookup"><span data-stu-id="54db3-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="54db3-104">使用することができます、<xref:System.Windows.Trigger>内、 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、または<xref:System.Windows.DataTemplate>です。</span><span class="sxs-lookup"><span data-stu-id="54db3-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54db3-105">例</span><span class="sxs-lookup"><span data-stu-id="54db3-105">Example</span></span>  
 <span data-ttu-id="54db3-106">次の例では、<xref:System.Windows.Trigger>アニメーション化する、<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Button>ときにその<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティになります`true`です。</span><span class="sxs-lookup"><span data-stu-id="54db3-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="54db3-107">プロパティによって適用されたアニメーション<xref:System.Windows.Trigger>オブジェクトよりも複雑な方法で動作しますが<xref:System.Windows.EventTrigger>アニメーションまたはアニメーションを使用して開始<xref:System.Windows.Media.Animation.Storyboard>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="54db3-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="54db3-108">「ハンドオフ」アニメーションを使用して他の定義、<xref:System.Windows.Trigger>使用して、オブジェクトが作成<xref:System.Windows.EventTrigger>およびアニメーションのメソッドによってトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="54db3-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54db3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="54db3-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="54db3-110">プロパティ アニメーションの手法の概要</span><span class="sxs-lookup"><span data-stu-id="54db3-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="54db3-111">ストーリーボードの概要</span><span class="sxs-lookup"><span data-stu-id="54db3-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
