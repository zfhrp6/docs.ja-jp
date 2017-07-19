---
title: "Walkthrough: Using Dataflow in a Windows Forms Application | Microsoft Docs"
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
  - "TPL dataflow library, in Windows Forms"
  - "Task Parallel Library, dataflows"
  - "Windows Forms, and TPL"
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Walkthrough: Using Dataflow in a Windows Forms Application
ここでは、Windows フォーム アプリケーションでイメージ処理を実行するデータ フローのブロックのネットワークを作成する方法を示します。  
  
 この例では、指定されたフォルダーから、イメージ ファイルを読み込み、複合イメージを生成し、結果を表示します。  例はネットワークでイメージをルーティングするためにデータ フロー モデルを使用します。  データ フロー モデルでは、プログラムの独立したコンポーネントどうしがメッセージを送信することによって通信します。  メッセージを受信したコンポーネントは、アクションを実行し、別のコンポーネントが結果を渡します。  このモデルと制御フロー モデルを比較してください。制御フロー モデルでは、アプリケーションは制御構造 \(条件付きステートメントやループなど\) を使用してプログラムでの操作順序を制御します。  
  
## 必須コンポーネント  
 このチュートリアルを開始する前に [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) を読み込みます。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## セクション  
 このチュートリアルは、次のセクションで構成されています。  
  
-   [Windows フォーム アプリケーションの作成](#winforms)  
  
-   [データ フロー ネットワークの作成](#network)  
  
-   [ユーザー インターフェイスからデータ フロー ネットワークをアタッチできます。](#ui)  
  
-   [完全な例](#complete)  
  
<a name="winforms"></a>   
## Windows フォーム アプリケーションの作成  
 ここでは、基本の Windows フォーム アプリケーションを作成し、メイン フォームにコントロールを追加する方法について説明します。  
  
#### Windows フォーム アプリケーションを作成するには  
  
1.  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]で、Visual Basic または [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]**\[Windows フォーム アプリケーション\]** のプロジェクトを作成します。  このドキュメントでは、プロジェクトは `CompositeImages`という名前です。  
  
2.  メイン フォームのフォーム デザイナーで、Form1.cs \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の Form1.vb\) は、<xref:System.Windows.Forms.ToolStrip> のコントロールを追加します。  
  
3.  <xref:System.Windows.Forms.ToolStrip> のコントロールに <xref:System.Windows.Forms.ToolStripButton> のコントロールを追加します。  フォルダーを選択するに <xref:System.Windows.Forms.ToolStripItemDisplayStyle> に <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> のプロパティと <xref:System.Windows.Forms.ToolStripItem.Text%2A> のプロパティを設定します。  
  
4.  <xref:System.Windows.Forms.ToolStrip> のコントロールに秒の <xref:System.Windows.Forms.ToolStripButton> のコントロールを追加します。  キャンセルに <xref:System.Windows.Forms.ToolStripItemDisplayStyle>に <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> のプロパティ、<xref:System.Windows.Forms.ToolStripItem.Text%2A> のプロパティ、および `False`に <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> のプロパティを設定します。  
  
5.  メイン フォームに <xref:System.Windows.Forms.PictureBox> オブジェクトを追加します。  <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
<a name="network"></a>   
## データ フロー ネットワークの作成  
 このセクションでは、イメージ処理を実行するデータ フロー ネットワークを作成する方法について説明します。  
  
#### データ フロー ネットワークを作成するには  
  
1.  プロジェクトに System.Threading.Tasks.Dataflow.dll への参照を追加します。  
  
2.  Form1.cs \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の Form1.vb\) が `using` Next \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`Using`\) ステートメントが含まれていることを確認する:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  `Form1` クラスに次のデータ メンバーを追加する:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  `Form1` クラスに次のメソッド、`CreateImageProcessingNetwork`を追加します。  このメソッドは、イメージ処理ネットワークを作成します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  `LoadBitmaps` メソッドを実装します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  `CreateCompositeBitmap` メソッドを実装します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  `CreateCompositeBitmap` のメソッドの C\# バージョンは <xref:System.Drawing.Bitmap?displayProperty=fullName> オブジェクトを効率的に処理を有効にするには、ポインターを使用します。  したがって、[アンセーフ](../Topic/unsafe%20\(C%23%20Reference\).md) キーワードの使用をプロジェクトの **\[アンセーフ コードの許可\]** オプションを有効にする必要があります。  この方法の詳細については [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] のプロジェクトのアンセーフ コードを有効にする [\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)を参照します。  
  
 ネットワークのメンバーを次の表に示します。  
  
|メンバー|型|説明|  
|----------|-------|--------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|フォルダーのパスを入力として受け取り、出力として <xref:System.Drawing.Bitmap> オブジェクトのコレクションを生成します。|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<xref:System.Drawing.Bitmap> オブジェクトのコレクションを入力として受け取り、出力として複合のビットマップを作成します。|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|フォームの構成のビットマップを表示します。|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|イメージを表示するためにキャンセル操作が表示され、ユーザーが別のフォルダーを選択することができます。|  
  
 ネットワークを形成するデータ フローのブロックを接続するには、この例では <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> のメソッドを使用します。  <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> のメソッドはターゲット ブロックがメッセージを受け入れるか拒否するかどうかを確認 <xref:System.Predicate%601> オブジェクトを受け取るオーバーロードされたバージョンが含まれています。  このフィルター処理機能によって、専用の特定の値にメッセージ ブロックを有効にします。  この例では、ネットワークの 2 とおりの方法は 1 とおりに分岐することができます。  メイン分岐はディスクからイメージを読み込みましたり、複合イメージおよび表示するイメージのフォームを作成します。  代替の分岐には、現在の操作をキャンセルします。  <xref:System.Predicate%601> オブジェクトがメイン分岐に沿ってデータ フローのブロックが特定のメッセージの拒否によって代替分岐をに切り替えることができます。  たとえば、ユーザーが操作をキャンセルした場合は、データ フローのブロック `createCompositeBitmap` が出力として `null` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`Nothing`\) を生成します。  データ フローのブロック `displayCompositeBitmap` は `null` の入力値を拒否ので、メッセージが `operationCancelled`に用意されています。  データ フローのブロック `operationCancelled` はすべてのメッセージを受け入れるため、イメージを操作がキャンセルされたことを示すために表示されます。  
  
 次の図は、イメージ処理ネットワークを示しています。  
  
 ![画像処理ネットワーク](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 `displayCompositeBitmap` と `operationCancelled` のデータ フローのブロックがユーザー インターフェイスで機能するため、これらの操作がユーザー インターフェイス スレッドで発生することが重要です。  、構築中に行うには、これをこれらのオブジェクトにはそれぞれ <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName>に <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> のプロパティ セットを持つ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを提供します。  <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=fullName> のメソッドは、現在の同期コンテキストの作業を実行 <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。  `CreateImageProcessingNetwork` のメソッドがユーザー インターフェイス スレッドで実行されるフォルダー選択ボタンのハンドラーから呼び出されるため、`displayCompositeBitmap` と `operationCancelled` のデータ フローのブロックの操作では、ユーザー インターフェイス スレッドで実行されます。  
  
 この例では <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> のプロパティを設定する代わりに <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> のプロパティが完全にデータ フローのブロックの実行を取り消すため、共有キャンセル トークンを使用します。  キャンセル トークンが、ユーザーは一つ以上の操作を取り消す場合でも、この例が同じデータ フロー ネットワークを複数回再利用できるようになります。  完全にデータ フローのブロックの実行を取り消すために <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> の使用例については [How to: Cancel a Dataflow Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)を参照してください。  
  
<a name="ui"></a>   
## ユーザー インターフェイスからデータ フロー ネットワークをアタッチできます。  
 ここでは、ユーザー インターフェイスにデータ フロー ネットワークに接続する方法について説明します。  複合イメージの作成および操作のキャンセルが、選択したフォルダーおよび Cancel ボタンから開始されます。  ユーザーがこれらのボタンのいずれかを選択すると、適切なアクションを非同期的に開始されます。  
  
#### データ フロー ネットワークをユーザー インターフェイスに接続するには  
  
1.  メイン フォームのフォーム デザイナーで、選択したフォルダー ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成します。  
  
2.  選択したフォルダー ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントを実装してください。  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  メイン フォームのフォーム デザイナーで、キャンセル ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成します。  
  
4.  キャンセル ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントを実装してください。  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## 完全な例  
 次の例では、このチュートリアルの完全なコードを示しています。  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 次の図は\\Sample の Pictures\\ の共通フォルダーの一般的な出力が表示されます。  
  
 ![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow\_CompositeImages")  
  
## 次の手順  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)