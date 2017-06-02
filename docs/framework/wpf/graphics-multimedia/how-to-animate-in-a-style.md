---
title: "方法 : スタイル内でアニメーション化を行う | Microsoft Docs"
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
  - "アニメーション, プロパティ, スタイル内"
  - "スタイル, アニメーション化 (プロパティを)"
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : スタイル内でアニメーション化を行う
この例では、スタイル内でプロパティをアニメーション化する方法を示します。  スタイル内でのアニメーション化では、スタイルが定義されているフレームワーク要素だけを直接ターゲットにできます。  フリーズ可能オブジェクトをターゲットにするには、スタイルが設定されている要素のプロパティから "ドット ダウン" する必要があります。  
  
 次の例では、複数のアニメーションをスタイル内で定義し、<xref:System.Windows.Controls.Button> に適用します。  ユーザーがマウスをボタン上に移動すると、そのボタンは、不透明から部分的に透明へフェードし、また元に戻るという動作を繰り返します。  ユーザーがマウスをボタンから離すと、すべて不透明になります。  ボタンをクリックすると、その背景色がオレンジから白に変わり、また元に戻ります。  ボタンの描画に使用する <xref:System.Windows.Media.SolidColorBrush> は直接ターゲットにできないため、ボタンの <xref:System.Windows.Controls.Control.Background%2A> プロパティからのドット ダウンによってアクセスします。  
  
## 使用例  
 [!code-xml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 スタイル内でアニメーション化を行う場合、存在しないオブジェクトはターゲットにできないことに注意してください。  たとえば、スタイルが <xref:System.Windows.Media.SolidColorBrush> を使用してボタンの Background プロパティを設定すると、ある時点で、そのスタイルはオーバーライドされ、ボタンの背景は <xref:System.Windows.Media.LinearGradientBrush> で設定されます。  <xref:System.Windows.Media.SolidColorBrush> をアニメーション化しようとしても例外をスローすることはなく、アニメーション化は、単に通知なしに失敗します。  
  
 ストーリーボードの対象化に関する構文の詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  アニメーションの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  スタイルの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。