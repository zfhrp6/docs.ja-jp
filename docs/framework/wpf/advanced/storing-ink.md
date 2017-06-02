---
title: "インクの格納 | Microsoft Docs"
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
  - "Ink Serialized Format (ISF)"
  - "インク, 格納"
  - "ISF (Ink Serialized Format)"
  - "取得 (インクを)"
  - "格納 (インクを)"
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# インクの格納
<xref:System.Windows.Ink.StrokeCollection.Save%2A> メソッドは、インクを ISF \(Ink Serialized Format\) として格納するためのサポートを提供します。  <xref:System.Windows.Ink.StrokeCollection> クラスのコンストラクターは、インク データを読み取るためのサポートを提供します。  
  
## インクの格納と取得  
 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プラットフォームでインクを格納および取得する方法について説明します。  
  
 ボタン クリックのイベント ハンドラーを実装する例を次に示します。ここでは、\[名前を付けて保存\] ダイアログ ボックスをユーザーに示し、<xref:System.Windows.Controls.InkCanvas> からのインクをファイルに保存します。  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 ボタン クリックのイベント ハンドラーを実装する例を次に示します。ここでは、\[File Open\] ダイアログ ボックスをユーザーに示し、ファイルから <xref:System.Windows.Controls.InkCanvas> 要素へインクを読み込みます。  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## 参照  
 <xref:System.Windows.Controls.InkCanvas>   
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)