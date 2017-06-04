---
title: "方法 : タイムラインを自動的に反転するかどうかを指定する | Microsoft Docs"
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
  - "AutoReverse プロパティ (タイムラインの)"
  - "タイムライン, AutoReverse プロパティ"
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : タイムラインを自動的に反転するかどうかを指定する
タイムラインの <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> プロパティは、順方向の反復の完了後にタイムラインを逆方向に再生するかどうかを決定します。  期間とターゲット値は同じで <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> の設定が異なるさまざまなアニメーションの例を次に示します。  異なる <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> の設定に対する <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> プロパティの動作を示すため、一部のアニメーションは繰り返すように設定されています。  最後のアニメーションでは、入れ子になったタイムラインでの <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> プロパティの動作が示されています。  
  
## 使用例  
 [!code-xml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]