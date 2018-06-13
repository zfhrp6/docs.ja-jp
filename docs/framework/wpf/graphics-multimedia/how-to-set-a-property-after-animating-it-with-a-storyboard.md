---
title: '方法 : ストーリーボードを使用してアニメーション化した後にプロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: b8e9c08075b13f8d6f701d5ac6ae4f8ea8949184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562266"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>方法 : ストーリーボードを使用してアニメーション化した後にプロパティを設定する
場合によっては、アニメーション化された後、プロパティの値を変更することはできません、ことがあります。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Windows.Media.Animation.Storyboard>の色をアニメーション化するために使用する<xref:System.Windows.Media.SolidColorBrush>です。 ストーリー ボードは、ボタンがクリックされたときにトリガーされます。 <xref:System.Windows.Media.Animation.Timeline.Completed>プログラムが通知されるように、イベントが処理されるときに、<xref:System.Windows.Media.Animation.ColorAnimation>が完了します。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>例  
 後に、<xref:System.Windows.Media.Animation.ColorAnimation>が完了したら、ブラシの色を青に変更を試行するプログラムです。  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 何も操作する前のコードが表示されない: によって提供される、ブラシは黄、これは、値、<xref:System.Windows.Media.Animation.ColorAnimation>ブラシをアニメーション化します。 基になるプロパティの値 (基本値) は実際に青に変更されています。 ただし、有効なつまり現在の値は黄色ため、<xref:System.Windows.Media.Animation.ColorAnimation>底の値を上書きしています。 ベース値に有効な値をもう一度になる場合は、プロパティへの影響からアニメーションを停止する必要があります。 これにはストーリー ボードのアニメーションで行うには次の 3 つの方法があります。  
  
-   アニメーションの<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティ <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   ストーリー ボード全体を削除します。  
  
-   アニメーションを個々 のプロパティから削除します。  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Stop に設定されて、アニメーションの FillBehavior プロパティ  
 設定して<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>に<xref:System.Windows.Media.Animation.FillBehavior.Stop>、停止、アクティブな期間の末尾に達した後、ターゲット プロパティに影響を与えずに、アニメーションがわかります。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>ストーリー ボード全体を削除します。  
 使用して、<xref:System.Windows.Media.Animation.RemoveStoryboard>トリガーまたは<xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>メソッド、そのターゲット プロパティの影響を与えることを停止するストーリー ボードのアニメーションがわかります。 このアプローチと設定の違い、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、ストーリー ボードを削除することでいつでも、while、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティにのみ影響アニメーションがアクティブな期間の最後に達するとします。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>アニメーションを個々 のプロパティから削除します。  
 プロパティに影響を与えないアニメーションを停止するもう 1 つの方法は、使用する、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>アニメーション化されているオブジェクトのメソッドです。 最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 この手法は、非ストーリー ボードのアニメーションのでも動作します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
