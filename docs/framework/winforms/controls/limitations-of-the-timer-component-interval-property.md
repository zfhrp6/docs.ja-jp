---
title: "Windows フォームの Timer コンポーネントの Interval プロパティの制限 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Interval プロパティ, 制限事項"
  - "Timer コンポーネント [Windows フォーム], 制限事項 (Interval プロパティの)"
  - "タイマー, イベントの間隔"
  - "タイマー, Windows ベースの"
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows フォームの Timer コンポーネントの Interval プロパティの制限
Windows フォームの <xref:System.Windows.Forms.Timer> コンポーネントの <xref:System.Windows.Forms.Timer.Interval%2A> プロパティは、1 つのタイマー イベントから次のタイマー イベントまでの時間間隔をミリ秒単位で指定します。  コンポーネントが無効にされない限り、タイマーはほぼ一定の間隔で <xref:System.Windows.Forms.Timer.Tick> イベントを受信し続けます。  
  
 このコンポーネントは、Windows フォーム環境で使用します。  サーバー環境に適したタイマーが必要な場合は、「[Introduction to Server\-Based Timers](http://msdn.microsoft.com/ja-jp/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。  
  
## Interval プロパティ  
 <xref:System.Windows.Forms.Timer.Interval%2A> プロパティには、<xref:System.Windows.Forms.Timer> コンポーネントのプログラミング時に考慮する必要のあるいくつかの制限があります。  
  
-   実行しているアプリケーションまたは他のアプリケーションがシステムに対して重い負荷をかけている場合 \(長いループ、複雑な計算、ドライブ、ネットワーク、ポートへのアクセスなど\) は、アプリケーションがタイマー イベントを受け取る間隔が <xref:System.Windows.Forms.Timer.Interval%2A> プロパティで指定されたよりも長くなることがあります。  
  
-   間隔が厳密に時間どおりに経過することは保証されていません。  正確さを保つには、内部で蓄積された時間を追跡する代わりに、必要に応じてシステム時計をチェックします。  
  
-   <xref:System.Windows.Forms.Timer.Interval%2A> プロパティの精度はミリ秒単位です。  コンピューターによっては、ミリ秒以上の高分解能カウンターが用意されているものがあります。  このようなカウンターが使用可能かどうかは、コンピューターのプロセッサ ハードウェアによります。  詳細については、マイクロソフト サポート技術情報 \(http:\/\/support.microsoft.com\) の文書 172338「QueryPerformanceCounter を使用してコードの時間を計測する方法」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Timer>   
 [Timer コンポーネント](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)   
 [Timer コンポーネントの概要](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)