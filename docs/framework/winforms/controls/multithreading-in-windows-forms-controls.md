---
title: "Windows フォーム コントロールのマルチスレッド処理 | Microsoft Docs"
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
  - "BackgroundWorker コンポーネント"
  - "BeginInvoke メソッド"
  - "スレッド処理 [Windows フォーム], コントロール"
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Windows フォーム コントロールのマルチスレッド処理
多くのアプリケーションでは、時間がかかる操作を別スレッドで実行することにより、ユーザー インターフェイス \(UI\) の反応を良くすることができます。  Windows フォーム コントロールでマルチスレッド処理を行うための手段はいくつか用意されています。たとえば、<xref:System.Threading> 名前空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=fullName> メソッド、および `BackgroundWorker` コンポーネントです。  
  
> [!NOTE]
>  `BackgroundWorker` コンポーネントは、<xref:System.Threading> 名前空間および <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=fullName> メソッドに代わるもので、また機能が追加されています。ただし、この名前空間とメソッドは、下位互換性を保つ目的、および必要に応じて将来使用する目的から、そのまま残されています。  詳細については、「[BackgroundWorker コンポーネントの概要](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)」を参照してください。  
  
## このセクションの内容  
 [方法 : Windows フォーム コントロールのスレッド セーフな呼び出しを行う](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Windows フォーム コントロールのスレッド セーフな呼び出しを行う方法を示します。  
  
 [方法 : バックグラウンド スレッドを使用してファイルを検索する](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <xref:System.Threading> 名前空間および <xref:System.Windows.Forms.Control.BeginInvoke%2A> メソッドを使用して、ファイルを非同期で検索する方法を示します。  
  
## 関連項目  
 <xref:System.ComponentModel.BackgroundWorker>  
 非同期の操作用のワーカー スレッドをカプセル化するコンポーネントについて説明されています。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 サウンドを非同期で読み込む方法について説明されています。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 イメージを非同期で読み込む方法について説明されています。  
  
## 関連項目  
 [方法 : バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 時間がかかる操作を <xref:System.ComponentModel.BackgroundWorker> コンポーネントで実行する方法を示します。  
  
 [BackgroundWorker コンポーネントの概要](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用して非同期の操作を実行する方法を説明するトピックを示します。