---
title: "方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント トリガー, 制御 (ストーリーボードを)"
  - "ストーリーボード, 制御 (起動後に)"
  - "トリガー, 制御 (ストーリーボードを)"
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する
この例では、<xref:System.Windows.Media.Animation.Storyboard> が開始した後でそれを制御する方法を示します。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して <xref:System.Windows.Media.Animation.Storyboard> を開始するには、<xref:System.Windows.Media.Animation.BeginStoryboard> を使用します。これにより、アニメーション化されるオブジェクトとプロパティにアニメーションが配布され、ストーリーボードが開始されます。  <xref:System.Windows.Media.Animation.BeginStoryboard> は、<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> プロパティを指定することによって名前を設定すると、制御可能なストーリーボードになります。  ストーリーボードは、開始されると対話的に制御できます。  
  
 ストーリーボードを制御するには、以下のストーリーボード アクションを <xref:System.Windows.EventTrigger> オブジェクトと共に使用します。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: ストーリーボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: 一時停止されたストーリーボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: ストーリーボードの速度を変更します。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: ストーリーボードがある場合は、それを区間の最後に進めます。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: ストーリーボードを停止します。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: ストーリーボードを削除して、リソースを解放します。  
  
## 使用例  
 次の例では、制御可能なストーリーボード アクションを使用して、ストーリーボードを対話的に制御しています。  
  
 **メモ :** コードを使用してストーリーボードを制御する例については、「[対話型メソッドを使用してストーリーボードを開始後に制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)」を参照してください。  
  
 [!code-xml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 その他の例については、[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>   
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>   
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>   
 <xref:System.Windows.Media.Animation.PauseStoryboard>   
 <xref:System.Windows.Media.Animation.StopStoryboard>   
 <xref:System.Windows.Media.Animation.SeekStoryboard>   
 [対話型メソッドを使用してストーリーボードを開始後に制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)