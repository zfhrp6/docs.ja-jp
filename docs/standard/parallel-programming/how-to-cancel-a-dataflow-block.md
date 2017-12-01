---
title: "方法: データフロー ブロックをキャンセルする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d6fbde31cd4b4b5d0c6404b8baf23230f2bda77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a>方法: データフロー ブロックをキャンセルする
このドキュメントでは、アプリケーションでキャンセルを有効にする方法を示します。 この例では、Windows フォームを使用して、データフロー パイプラインで作業項目がアクティブである場所と、キャンセルの影響を示します。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
### <a name="to-create-the-windows-forms-application"></a>Windows フォーム アプリケーションを作成するには  
  
1.  C# または Visual Basic の **Windows フォーム アプリケーション** プロジェクトを作成します。 以降の手順では、プロジェクトの名前は `CancellationWinForms` とします。  
  
2.  メイン フォーム Form1.cs のフォーム デザイナーで (の Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])、追加、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
3.  追加、<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。 設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>と<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**作業項目の追加**です。  
  
4.  1 秒あたりの追加<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。 設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>、<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**キャンセル**、および<xref:System.Windows.Forms.ToolStripItem.Enabled%2A>プロパティを`False`です。  
  
5.  次の 4 つの追加<xref:System.Windows.Forms.ToolStripProgressBar>オブジェクトを<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
## <a name="creating-the-dataflow-pipeline"></a>データフロー パイプラインの作成  
 このセクションでは、作業項目を処理して進行状況バーを更新するデータフロー パイプラインを作成する方法を示します。  
  
#### <a name="to-create-the-dataflow-pipeline"></a>データフロー パイプラインを作成するには  
  
1.  プロジェクトで、System.Threading.Tasks.Dataflow.dll への参照を追加します。  
  
2.  Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) が次の `using` ステートメント ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `Imports`) を含むことを確認します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  `Form1` クラスの内部の型として `WorkItem` クラスを追加します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  `Form1` クラスに次のデータ メンバーを追加します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  次の `CreatePipeline` メソッドを `Form1` クラスに追加します。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 `incrementProgress` と `decrementProgress` のデータフロー ブロックはユーザー インターフェイスで機能するので、これらの操作をユーザー インターフェイス スレッドで実行することが重要です。 これを実現する、構築時にこれらのオブジェクトが各提供、<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>を持つオブジェクトを<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>プロパティに設定<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>です。 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。 `Form1` コンストラクターはユーザー インターフェイス スレッドから呼び出されるので、`incrementProgress` および `decrementProgress` データフロー ブロックに対するアクションも、ユーザー インターフェイス スレッドで実行されます。  
  
 この例では設定、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティ、パイプラインのメンバーを作成するときにします。 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティが完全にデータ フロー ブロックの実行をキャンセル、ユーザーが操作をキャンセルし、次がパイプラインに多くの作業項目を追加した後、全体のパイプラインを再作成する必要があります。 操作をキャンセルした後も他の作業を実行できるようにデータフロー ブロックをキャンセルする方法もあります。例については、「[チュートリアル: Windows フォーム アプリケーションでのデータフローの使用](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>ユーザー インターフェイスへのデータフロー パイプラインの接続  
 このセクションでは、ユーザー インターフェイスにデータフロー パイプラインを接続する方法を説明します。 パイプラインの作成とパイプラインへの作業項目の追加は、どちらも **[作業項目の追加]** ボタンのインベント ハンドラーによって制御されます。 キャンセルは **[キャンセル]** ボタンによって開始されます。 ユーザーがこのいずれかのボタンをクリックすると、適切な操作が非同期的に開始されます。  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>ユーザー インターフェイスにデータフロー パイプラインを接続するには  
  
1.  メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**作業項目の追加**ボタンをクリックします。  
  
2.  実装、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**作業項目の追加**ボタンをクリックします。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント ハンドラー、**キャンセル**ボタンをクリックします。  
  
4.  実装、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント ハンドラー、**キャンセル**ボタンをクリックします。  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>例  
 次の例は、Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) のコード全体を示しています。  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 次の図は、実行中のアプリケーションを示しています。  
  
 ![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
