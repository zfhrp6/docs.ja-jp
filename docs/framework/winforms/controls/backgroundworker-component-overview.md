---
title: "BackgroundWorker コンポーネントの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BackgroundWorker"
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
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# BackgroundWorker コンポーネントの概要
一般的な操作には、実行時間が長くかかるものが数多くあります。  次に例を示します。  
  
-   イメージのダウンロード  
  
-   Web サービスの起動  
  
-   ファイルのダウンロードとアップロード \(ピアツーピア アプリケーションの場合を含む\)  
  
-   ローカルでの複雑な計算  
  
-   データベース トランザクション  
  
-   ローカル ディスク アクセス \(前提としてメモリ アクセスに比べて低速です\)  
  
 以上のような操作の実行時には、ユーザー インターフェイスがハングアップすることがあります。  応答性に優れた UI を必要としながらも、このような操作との関連で長時間の遅延に直面する場合は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントが便利なソリューションになります。  
  
 <xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用すると、時間のかかる操作を、アプリケーションのメイン UI スレッドとは別のスレッドで非同期的に \("バックグラウンドで"\) 実行できます。  <xref:System.ComponentModel.BackgroundWorker> を使用するには、バックグラウンドで実行する、時間のかかるワーカー メソッドをこのコンポーネントに通知して、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> メソッドを呼び出すだけです。  呼び出し元スレッドが正常に動作し続けると共に、ワーカー メソッドも非同期的に動作します。  このメソッドが終了すると、<xref:System.ComponentModel.BackgroundWorker> は、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントを起動して、呼び出し元スレッドに警告します。このイベントには、オプションで操作の結果を含めることもできます。  
  
 <xref:System.ComponentModel.BackgroundWorker> コンポーネントは、**\[コンポーネント\]** タブの **\[ツールボックス\]** で選択できます。  <xref:System.ComponentModel.BackgroundWorker> をフォームに追加するには、<xref:System.ComponentModel.BackgroundWorker> コンポーネントをフォームにドラッグします。  このコンポーネントはコンポーネント トレイに表示され、プロパティが **\[プロパティ\]** ウィンドウに表示されます。  
  
 非同期操作を開始するには、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> メソッドを使用します。  <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> は、オプションの `object` パラメーターを受け取り、このパラメーターを使用してワーカー メソッドに引数を渡すことができます。  <xref:System.ComponentModel.BackgroundWorker> クラスは、<xref:System.ComponentModel.BackgroundWorker.DoWork> イベントを公開します。このイベントには、<xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラー経由でワーカー スレッドをアタッチします。  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーは、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> プロパティを持つ <xref:System.ComponentModel.DoWorkEventArgs> パラメーターを受け取ります。  このプロパティは、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> からパラメーターを受け取り、<xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーで呼び出されるワーカー メソッドに渡されます。  次の例は、`ComputeFibonacci` というワーカー メソッドの結果を代入する方法を示しています。  これは、「[方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)」に記載されている例の一部です。  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 イベント ハンドラーの使い方の詳細については、「[イベント](../../../../docs/standard/events/index.md)」を参照してください。  
  
> [!CAUTION]
>  どのような種類のマルチスレッドを使用している場合でも、非常に深刻で複雑なバグを引き起こしてしまう可能性があります。  マルチスレッドを使用するソリューションを実装する前に、「[Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)」を参照してください。  
  
 <xref:System.ComponentModel.BackgroundWorker> クラスの使い方の詳細については、「[方法 : バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)」を参照してください。  
  
## 参照  
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/ja-jp/c731a50c-09c1-4468-9646-54c86b75d269)   
 [方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)