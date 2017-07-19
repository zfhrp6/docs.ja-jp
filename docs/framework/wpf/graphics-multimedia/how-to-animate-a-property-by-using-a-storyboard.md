---
title: "方法 : ストーリーボードを使ってプロパティをアニメーション化する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アニメーション, ストーリーボード"
  - "ストーリーボード, アニメーション"
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ストーリーボードを使ってプロパティをアニメーション化する
この例では、<xref:System.Windows.Media.Animation.Storyboard> を使用してプロパティをアニメーション化する方法を示します。  <xref:System.Windows.Media.Animation.Storyboard> を使用してプロパティをアニメーション化するには、アニメーション化する各プロパティのアニメーションを作成し、アニメーションを格納する <xref:System.Windows.Media.Animation.Storyboard> も作成します。  
  
 プロパティの型によって、使用するアニメーションの型が決まります。  たとえば、<xref:System.Double> 値を受け取るプロパティをアニメーション化するには、<xref:System.Windows.Media.Animation.DoubleAnimation> を使用します。  <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> および <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> [添付プロパティ](GTMT)は、アニメーションを適用するオブジェクトとプロパティを指定します。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でストーリーボードを開始するには、<xref:System.Windows.Media.Animation.BeginStoryboard> アクションと <xref:System.Windows.EventTrigger> を使用します。  <xref:System.Windows.EventTrigger.RoutedEvent%2A> プロパティで指定されているイベントが発生すると、<xref:System.Windows.EventTrigger> は <xref:System.Windows.Media.Animation.BeginStoryboard> アクションを開始します。  <xref:System.Windows.Media.Animation.BeginStoryboard> アクションは <xref:System.Windows.Media.Animation.Storyboard> を開始します。  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用して、2 つの <xref:System.Windows.Controls.Button> コントロールをアニメーション化します。  最初のボタンのサイズを変更するため、<xref:System.Windows.FrameworkElement.Width%2A> をアニメーション化します。  2 番目のボタンの色を変更するため、<xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> プロパティを使用して、アニメーション化するボタンの <xref:System.Windows.Controls.Control.Background%2A> を設定します。  
  
## 使用例  
 [!code-xml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  アニメーションは、<xref:System.Windows.Controls.Control> や <xref:System.Windows.Controls.Panel> などの <xref:System.Windows.FrameworkElement> オブジェクトと、<xref:System.Windows.Media.Brush> や <xref:System.Windows.Media.Transform> などの <xref:System.Windows.Freezable> オブジェクトの両方を対象にできますが、<xref:System.Windows.FrameworkElement.Name%2A> プロパティを持っているのはフレームワーク要素だけです。  名前をフリーズ可能オブジェクトに割り当てて、アニメーションの対象にできるようにするには、前の例で示したように [x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)を使用します。  
  
 コードを使用する場合は、<xref:System.Windows.FrameworkElement> に <xref:System.Windows.NameScope> を作成し、アニメーション化するオブジェクトの名前をその <xref:System.Windows.FrameworkElement> に登録します。  コードでアニメーションを開始するには、<xref:System.Windows.EventTrigger> で <xref:System.Windows.Media.Animation.BeginStoryboard> アクションを使用します。  必要に応じて、イベント ハンドラーと <xref:System.Windows.Media.Animation.Storyboard> の <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用できます。  <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用する方法の例を次に示します。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 アニメーションとストーリーボードの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 コードを使用する場合、プロパティをアニメーション化する方法は <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用するものだけではありません。  使用例を含む詳細については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」および「[AnimationClock を使用してプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)」を参照してください。