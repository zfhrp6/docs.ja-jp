---
title: "BackgroundWorker コンポーネント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "非同期パターン"
  - "バックグラウンド操作"
  - "バックグラウンド タスク"
  - "BackgroundWorker コンポーネント"
  - "コンポーネント [Windows フォーム], 非同期"
  - "フォーム, バックグラウンド操作"
  - "フォーム, マルチスレッド"
  - "スレッド処理 [Windows フォーム], バックグラウンド操作"
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# BackgroundWorker コンポーネント
`BackgroundWorker` コンポーネントを使用すると、フォームまたはコントロールで非同期の操作を実行できます。  
  
## このセクションの内容  
 [BackgroundWorker コンポーネントの概要](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 `BackgroundWorker` コンポーネントについて説明します。このコンポーネントを使用すると、時間のかかる操作を、アプリケーションのメイン UI スレッドとは別のスレッドで非同期的に \("バックグラウンドで"\) 実行できます。  
  
 [チュートリアル : 操作をバックグラウンドで実行する](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 デザイナーで `BackgroundWorker` コンポーネントを使用して、時間のかかる操作を別スレッドで実行する方法を説明します。  
  
 [方法 : バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 `BackgroundWorker` コンポーネントを使用して、時間のかかる操作を別スレッドで実行する方法を説明します。  
  
 [チュートリアル : バックグラウンド操作を使用するフォームの実装](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 デザイナーを使用して、数値演算処理を非同期で実行するアプリケーションを作成します。  
  
 [方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 数値演算処理を非同期で実行するアプリケーションを作成します。  
  
 [方法 : バックグラウンドでファイルをダウンロードする](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 `BackgroundWorker` コンポーネントを使用して、別スレッドでファイルをダウンロードする方法を説明します。  
  
## 関連項目  
 <xref:System.ComponentModel.BackgroundWorker>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントのデータを保持する型について説明します。  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのデータを保持する型について説明します。  
  
## 関連項目  
 [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 非同期パターンを使用することで、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用する方法について説明します。