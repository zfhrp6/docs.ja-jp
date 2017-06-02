---
title: "方法 : ストーリーボードを開始後に制御する | Microsoft Docs"
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
  - "ストーリーボード, 制御 (起動後に)"
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ストーリーボードを開始後に制御する
この例では、<xref:System.Windows.Media.Animation.Storyboard> が開始した後で、コードを使用してそのストーリーボードを制御する方法を示します。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でストーリーボードを制御するには、たとえば、<xref:System.Windows.Trigger> オブジェクトと <xref:System.Windows.TriggerAction> オブジェクトを使用します。「[開始後のストーリーボードをイベント トリガーを使用して制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)」を参照してください。  
  
 ストーリーボードを開始するには、ストーリーボードの <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用します。このメソッドは、ストーリーボードのアニメーションをアニメーション化の対象プロパティに分配し、ストーリーボードを開始します。  
  
 ストーリーボードを制御可能にするには、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用し、2 番目のパラメーターに **true** を指定します。  その後は、ストーリーボードの対話型メソッドを使用して、ストーリーボードを一時停止、再開、シーク、停止、加速、または減速したり、保留期間まで進めたりすることができます。  以下は、ストーリーボードの対話型メソッドの一覧です。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: ストーリーボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: 一時停止されたストーリーボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A> : ストーリーボードの対話速度を設定します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> : ストーリーボードの指定した位置をシークします。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> : ストーリーボードを指定した位置までシークします。  <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> メソッドとは異なり、この操作は次の目盛りに進む前に処理されます。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A> : ストーリーボードを保留期間に進めます \(保留期間がある場合\)。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: ストーリーボードを停止します。  
  
 次の例では、さまざまなストーリーボード メソッドを使用して、ストーリーボードを対話形式で制御しています。  
  
 **メモ :**  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でトリガーを使用してストーリーボードを制御する例については、「[開始後のストーリーボードをイベント トリガーを使用して制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## 参照  
 [開始後のストーリーボードをイベント トリガーを使用して制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)