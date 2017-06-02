---
title: "How to: Cancel a Dataflow Block | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Task Parallel Library, dataflows"
  - "dataflow blocks, canceling in TPL"
  - "TPL dataflow library,canceling dataflow blocks"
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Cancel a Dataflow Block
ここでは、アプリケーションのキャンセルを可能にする方法を示しています。  この例では、作業項目がキャンセルのデータフロー パイプラインと、結果がアクティブである場所を示すために、Windows のフォームを使用します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
### Windows フォーム アプリケーションを作成するには  
  
1.  C\# または Visual Basic **\[Windows フォーム アプリケーション\]** のプロジェクトを作成します。  次の手順では、プロジェクトは `CancellationWinForms`という名前です。  
  
2.  メイン フォームのフォーム デザイナーで、Form1.cs \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の Form1.vb\) は、<xref:System.Windows.Forms.ToolStrip> のコントロールを追加します。  
  
3.  <xref:System.Windows.Forms.ToolStrip> のコントロールに <xref:System.Windows.Forms.ToolStripButton> のコントロールを追加します。  作業項目を追加するに <xref:System.Windows.Forms.ToolStripItemDisplayStyle> に <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> のプロパティと <xref:System.Windows.Forms.ToolStripItem.Text%2A> のプロパティを設定します。  
  
4.  <xref:System.Windows.Forms.ToolStrip> のコントロールに秒の <xref:System.Windows.Forms.ToolStripButton> のコントロールを追加します。  キャンセルに <xref:System.Windows.Forms.ToolStripItemDisplayStyle>に <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> のプロパティ、<xref:System.Windows.Forms.ToolStripItem.Text%2A> のプロパティ、および `False`に <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> のプロパティを設定します。  
  
5.  <xref:System.Windows.Forms.ToolStrip> のコントロールへの <xref:> System.Windows.Forms.ToolStripProgressBar?qualifyHint=False&autoUpgrade=True の 4 種類のオブジェクトを追加します。  
  
## データフロー パイプラインの作成  
 ここでは、データ フローのパイプラインを作成する方法と、作業の処理方法を説明し、プログレス バーを更新します。  
  
#### データフロー パイプラインを作成します。  
  
1.  プロジェクトで、System.Threading.Tasks.Dataflow.dll への参照を追加します。  
  
2.  Form1.cs \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の Form1.vb\) が `using` の次のステートメント \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`Imports`\) が含まれていることを確認します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  `Form1` クラスの内部の型として `WorkItem` クラスを追加します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  `Form1` クラスに次のデータ メンバーを追加します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  `Form1` クラスに次のメソッド、`CreatePipeline`を追加します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 `incrementProgress` と `decrementProgress` のデータ フローのブロックがユーザー インターフェイスで機能するため、これらの操作がユーザー インターフェイス スレッドで発生することが重要です。  構築中にこれを実行するには、これらのオブジェクトは、<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName>に <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> のプロパティ セットを持つ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを提供します。  <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName> のメソッドは、現在の同期コンテキストの作業を実行 <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。  `Form1` のコンストラクターがユーザー インターフェイス スレッドから呼び出されるため、`incrementProgress` と `decrementProgress` のデータ フローのブロックの操作では、ユーザー インターフェイス スレッドで実行されます。  
  
 この例では、パイプラインのメンバーを構築するときに <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> のプロパティを設定します。  <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> のプロパティが完全にデータ フローの実行をブロックするため、すべてのパイプラインはユーザー取り消しの完了後にアクション作り直されなければなり、パイプラインによりも多くの作業項目を追加する必要があります。  操作がキャンセルされた後に他の作業を実行できるように、データ フローのブロックを取り消す方法を示す例については、[Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)を参照してください。  
  
## ユーザー インターフェイスにデータフロー パイプラインをアタッチできます。  
 ここでは、ユーザー インターフェイスにデータフロー パイプラインを追加する方法について説明します。  パイプラインを作成し、パイプラインに作業項目を追加すると、追加作業項目ボタンのイベント ハンドラーによって制御されます。  取り消し処理はキャンセル ボタンで開始します。  ユーザーがこれらのボタンのいずれかをクリックすると、適切なアクションを非同期的に開始されます。  
  
#### データフロー パイプラインをユーザー インターフェイスに接続するには  
  
1.  メイン フォームのフォーム デザイナーで、作業項目の追加ボタン <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成します。  
  
2.  追加の作業項目ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントを実装してください。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  メイン フォームのフォーム デザイナーで、キャンセル ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> のイベント ハンドラーのイベント ハンドラーを作成します。  
  
4.  キャンセル ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> のイベント ハンドラーを実装してください。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## 使用例  
 次の例は、Form1.cs \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の Form1.vb\) の完全なコードを示しています。  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 次の図では、実行中のアプリケーションを示します。  
  
 ![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow\_Cancellation")  
  
## 信頼性の高いプログラミング  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)