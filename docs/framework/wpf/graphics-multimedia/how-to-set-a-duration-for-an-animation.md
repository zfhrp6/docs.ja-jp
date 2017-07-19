---
title: "方法 : アニメーションの継続時間を設定する | Microsoft Docs"
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
  - "アニメーション, 継続時間"
  - "継続期間 (アニメーションの)"
  - "タイムライン, description"
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : アニメーションの継続時間を設定する
<xref:System.Windows.Media.Animation.Timeline> は時間のセグメントを表し、そのセグメントの長さはタイムラインの <xref:System.Windows.Duration> によって決まります。  <xref:System.Windows.Media.Animation.Timeline> は、期間の最後に到達すると、再生を停止します。  <xref:System.Windows.Media.Animation.Timeline> に子タイムラインがある場合は、子も再生を停止します。  アニメーションの場合は、<xref:System.Windows.Duration> は、アニメーションが開始値から終了値まで移行するのに要する時間を指定します。  
  
 <xref:System.Windows.Duration> には、特定の有限の時間、または特殊な値 <xref:System.Windows.Duration.Automatic%2A> または <xref:System.Windows.Duration.Forever%2A> を指定できます。  アニメーションには、常に有限の長さを定義する必要があるため、アニメーションの継続時間は必ず時間値にする必要があります。それ以外の場合、アニメーションは、ターゲット値の間で遷移する方法を認識できません。  <xref:System.Windows.Media.Animation.Storyboard> や <xref:System.Windows.Media.Animation.ParallelTimeline> などのコンテナー タイムライン \(<xref:System.Windows.Media.Animation.TimelineGroup> オブジェクト\) の既定の期間は <xref:System.Windows.Duration.Automatic%2A> であり、最後の子が再生を停止した時点で自動的に終了することを意味します。  
  
 次の例では、<xref:System.Windows.Shapes.Rectangle> の幅、高さ、および塗りつぶしの色をアニメーション化しています。  期間はアニメーションとコンテナーのタイムラインに設定されており、アニメーションの認識された速度の制御と、コンテナー タイムラインの期間での子タイムラインの期間のオーバーライドを含むアニメーション効果になっています。  
  
## 使用例  
 [!code-xml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.Duration>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)