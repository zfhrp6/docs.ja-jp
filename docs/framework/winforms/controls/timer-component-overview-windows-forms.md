---
title: "Timer コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Timer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Timer コンポーネント [Windows フォーム], Timer コンポーネントの概要"
  - "タイマー, タイマーの概要"
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Timer コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.Timer> は、一定の間隔でイベントを発生させるコンポーネントです。  このコンポーネントは、Windows フォーム環境で使用します。  サーバー環境に適したタイマーが必要な場合は、「[Introduction to Server\-Based Timers](http://msdn.microsoft.com/ja-jp/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。  
  
## 主要なプロパティ、メソッド、およびイベント  
 間隔は <xref:System.Windows.Forms.Timer.Interval%2A> プロパティで定義し、値はミリ秒単位で指定します。  このコンポーネントを有効にすると、<xref:System.Windows.Forms.Timer.Tick> イベントが一定の間隔で発生します。  実行するコードは、ここに記述します。  詳細については、「[方法 : Windows フォームの Timer コンポーネントを使用して一定間隔でプロシージャを実行する](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)」を参照してください。  <xref:System.Windows.Forms.Timer> コンポーネントの主要なメソッドは、タイマーをオンおよびオフにする <xref:System.Windows.Forms.Timer.Start%2A> と <xref:System.Windows.Forms.Timer.Stop%2A> です。  タイマーをオフにすると、タイマーはリセットされます。<xref:System.Windows.Forms.Timer> コンポーネントを一時停止する方法はありません。  
  
## 参照  
 <xref:System.Windows.Forms.Timer>   
 [Timer コンポーネント](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)   
 [Windows フォームの Timer コンポーネントの Interval プロパティの制限](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)