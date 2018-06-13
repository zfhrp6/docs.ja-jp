---
title: '方法 : ストーリーボードを使ってプロパティをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: 7e67fb07a05d474999515a678fd72ac6b96953c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561073"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>方法 : ストーリーボードを使ってプロパティをアニメーション化する
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>プロパティをアニメーション化します。 使用してプロパティをアニメーション化する、 <xref:System.Windows.Media.Animation.Storyboard>、アニメーション化しも作成する各プロパティのアニメーションを作成、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを格納します。  
  
 プロパティの種類によって、使用するアニメーションの種類が決まります。 例についてを受け取るプロパティをアニメーション化する<xref:System.Double>、値を使用して、<xref:System.Windows.Media.Animation.DoubleAnimation>です。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>添付プロパティ オブジェクトと、アニメーションが適用されたプロパティを指定します。  
  
 ストーリー ボードを起動する[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を使用して、<xref:System.Windows.Media.Animation.BeginStoryboard>アクションと<xref:System.Windows.EventTrigger>です。 <xref:System.Windows.EventTrigger>開始、<xref:System.Windows.Media.Animation.BeginStoryboard>イベントである場合の動作によって指定されたその<xref:System.Windows.EventTrigger.RoutedEvent%2A>プロパティが発生します。 <xref:System.Windows.Media.Animation.BeginStoryboard>アクションが開始される、<xref:System.Windows.Media.Animation.Storyboard>です。  
  
 次の例で<xref:System.Windows.Media.Animation.Storyboard>2 つのアニメーション化するオブジェクト<xref:System.Windows.Controls.Button>コントロール。 最初のボタンのサイズ変更をその<xref:System.Windows.FrameworkElement.Width%2A>がアニメーション化します。 2 番目のボタンの色を変更する、<xref:System.Windows.Media.SolidColorBrush.Color%2A>のプロパティ、<xref:System.Windows.Media.SolidColorBrush>設定に使用される、<xref:System.Windows.Controls.Control.Background%2A>アニメーションを実行するボタンのです。  
  
## <a name="example"></a>例  
 [!code-xaml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  アニメーション両方を対象にできますが、<xref:System.Windows.FrameworkElement>などのオブジェクト、<xref:System.Windows.Controls.Control>または<xref:System.Windows.Controls.Panel>、および<xref:System.Windows.Freezable>などのオブジェクト、<xref:System.Windows.Media.Brush>または<xref:System.Windows.Media.Transform>、framework 要素だけが、<xref:System.Windows.FrameworkElement.Name%2A>プロパティです。 名前をフリーズ可能オブジェクトに割り当てて、アニメーションの対象にできるようにするには、前の例で示したように [x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)を使用します。  
  
 作成する必要があるコードを使用する場合、<xref:System.Windows.NameScope>の<xref:System.Windows.FrameworkElement>をアニメーション化するオブジェクトの名前を登録および<xref:System.Windows.FrameworkElement>です。 コードでは、アニメーションを開始するには、使用、<xref:System.Windows.Media.Animation.BeginStoryboard>アクションが、<xref:System.Windows.EventTrigger>です。 必要に応じて、イベント ハンドラーを使用することができます、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドの<xref:System.Windows.Media.Animation.Storyboard>します。 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用する方法の例を次に示します。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 アニメーションとストーリー ボードの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 使用に限定されていませんコードを使用する場合<xref:System.Windows.Media.Animation.Storyboard>オブジェクトのプロパティをアニメーション化するためにします。 使用例を含む詳細については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」と「[AnimationClock を使用してプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)」を参照してください。
