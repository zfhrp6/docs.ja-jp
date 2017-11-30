---
title: "方法 : スタイル内でアニメーション化を行う"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10cd243c633e7a7e458d2026fc5e3d91d2996427
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-in-a-style"></a>方法 : スタイル内でアニメーション化を行う
この例では、スタイル内でプロパティをアニメーション化する方法を示します。 スタイル内でアニメーション化するときに、スタイルが定義されているフレームワーク要素のみが直接対象となることができます。 Freezable オブジェクトを対象にする必要があります「ドット ダウン」スタイルを指定した要素のプロパティからです。  
  
 次の例では、複数のアニメーションのスタイル内で定義されているし、に適用される、<xref:System.Windows.Controls.Button>です。 部分的に半透明とバックエンドを不透明なから消えてしまう場合、ユーザーがマウス ボタンの上、もう一度、繰り返しです。 ユーザーがボタンをマウスを動かしたときに完全に不透明になります。 ボタンがクリックされたときに、背景色は白して戻すオレンジ色から変更します。 <xref:System.Windows.Media.SolidColorBrush>を描画するため、ボタンを直接対象ことはできません、下のボタンの dotting 使用してアクセスされた<xref:System.Windows.Controls.Control.Background%2A>プロパティです。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 スタイル内でアニメーション化するときに、存在しないオブジェクトはターゲットに考えられることに注意してください。 たとえば、自分のスタイルを使用して、<xref:System.Windows.Media.SolidColorBrush>ボタンの背景のプロパティを設定するが、ある時点で、スタイルをオーバーライドされ、ボタンの背景に設定されている、<xref:System.Windows.Media.LinearGradientBrush>です。  アニメーション化しようとして、<xref:System.Windows.Media.SolidColorBrush>例外をスローしません、アニメーションはサイレント モードで失敗します。  
  
 構文を対象とするストーリー ボードの詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。 アニメーションの詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。 スタイルの詳細については、次を参照してください。、[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。
