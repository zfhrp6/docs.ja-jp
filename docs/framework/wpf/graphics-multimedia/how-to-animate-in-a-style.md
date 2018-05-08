---
title: '方法 : スタイル内でアニメーション化を行う'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: e0741a869ab81875aaa25340de851ef939e11a6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-in-a-style"></a>方法 : スタイル内でアニメーション化を行う
この例では、スタイル内でプロパティをアニメーション化する方法を示します。 スタイル内でアニメーション化するときに、スタイルが定義されているフレームワーク要素のみが直接対象となることができます。 Freezable オブジェクトを対象にする必要があります「ドット ダウン」スタイルを指定した要素のプロパティからです。  
  
 次の例では、複数のアニメーションのスタイル内で定義されているし、に適用される、<xref:System.Windows.Controls.Button>です。 部分的に半透明とバックエンドを不透明なから消えてしまう場合、ユーザーがマウス ボタンの上、もう一度、繰り返しです。 ユーザーがボタンをマウスを動かしたときに完全に不透明になります。 ボタンがクリックされたときに、背景色は白して戻すオレンジ色から変更します。 <xref:System.Windows.Media.SolidColorBrush>を描画するため、ボタンを直接対象ことはできません、下のボタンの dotting 使用してアクセスされた<xref:System.Windows.Controls.Control.Background%2A>プロパティです。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 スタイル内でアニメーション化するときに、存在しないオブジェクトはターゲットに考えられることに注意してください。 たとえば、自分のスタイルを使用して、<xref:System.Windows.Media.SolidColorBrush>ボタンの背景のプロパティを設定するが、ある時点で、スタイルをオーバーライドされ、ボタンの背景に設定されている、<xref:System.Windows.Media.LinearGradientBrush>です。  アニメーション化しようとして、<xref:System.Windows.Media.SolidColorBrush>例外をスローしません、アニメーションはサイレント モードで失敗します。  
  
 構文を対象とするストーリー ボードの詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。 アニメーションの詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。 スタイルの詳細については、次を参照してください。、[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。
