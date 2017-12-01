---
title: "チュートリアル: Windows フォーム アプリケーションでのデータフローの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>チュートリアル: Windows フォーム アプリケーションでのデータフローの使用
このドキュメントでは、Windows フォーム アプリケーションでイメージ処理を実行する、データフロー ブロックのネットワークを作成する方法を説明します。  
  
 この例では、指定したフォルダーからイメージ ファイルを読み込み、複合イメージを作成して、結果を表示します。 例では、ネットワーク経由でイメージをルーティングするために、データフロー モデルを使用します。 このデータフロー モデルでは、プログラム内の独立したコンポーネント同士が、メッセージを送信することによって相互に通信します。 1 つのコンポーネントがメッセージを受信すると、何らかのアクションを実行した後に、結果を別のコンポーネントに渡します。 このモデルと制御フロー モデルを比較してください。制御フロー モデルでは、アプリケーションは制御構造 (条件付きステートメントやループなど) を使用してプログラムでの操作順序を制御します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを開始する前に、「[Dataflow (データフロー)](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)」をお読みください。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
 
  
## <a name="sections"></a>セクション  
 このチュートリアルは、次のセクションで構成されています。  
  
-   [Windows フォーム アプリケーションの作成](#winforms)  
  
-   [データフロー ネットワークの作成](#network)  
  
-   [ユーザー インターフェイスへのデータフロー ネットワークの接続](#ui)  
  
-   [コード例全体](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Windows フォーム アプリケーションの作成  
 このセクションでは、基本的な Windows フォーム アプリケーションを作成し、メイン フォームにコントロールを追加する方法を説明します。  
  
#### <a name="to-create-the-windows-forms-application"></a>Windows フォーム アプリケーションを作成するには  
  
1.  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)] または Visual Basic **Windows フォーム アプリケーション** プロジェクトを作成します。 このドキュメントでは、プロジェクトの名前を `CompositeImages` とします。  
  
2.  メイン フォーム Form1.cs のフォーム デザイナーで (の Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])、追加、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
3.  追加、<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。 設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>と<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**フォルダーを選択**です。  
  
4.  1 秒あたりの追加<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。 設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>、<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**キャンセル**、および<xref:System.Windows.Forms.ToolStripItem.Enabled%2A>プロパティを`False`です。  
  
5.  追加、<xref:System.Windows.Forms.PictureBox>メイン フォームにオブジェクト。 <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>データフロー ネットワークの作成  
 このセクションでは、イメージ処理を実行するデータフロー ネットワークを作成する方法を説明します。  
  
#### <a name="to-create-the-dataflow-network"></a>データフロー ネットワークを作成するには  
  
1.  System.Threading.Tasks.Dataflow.dll への参照をプロジェクトに追加します。  
  
2.  Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では Form1.vb) に次の `using` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `Using`) ステートメントが含まれることを確認します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  `Form1` クラスに次のデータ メンバーを追加します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  次の `CreateImageProcessingNetwork` メソッドを `Form1` クラスに追加します。 このメソッドによって、イメージ処理ネットワークが作成されます。  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  `LoadBitmaps` メソッドを実装します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  `CreateCompositeBitmap` メソッドを実装します。  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# バージョンの`CreateCompositeBitmap`メソッドでは、ポインターを使用して効率的に処理を有効にする、<xref:System.Drawing.Bitmap?displayProperty=nameWithType>オブジェクト。 したがって、[unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) キーワードを使用するために、プロジェクト内の **[アンセーフ コードの許可]** オプションを有効にしてください。 アンセーフ コードを有効にする方法について、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]プロジェクトで、[ビルド ページ、プロジェクト デザイナー (c#)] を参照してください https://msdn.microsoft.com/library/kb4wyys2)。  
  
 ネットワークのメンバーを次の表に示します。  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|フォルダー パスを入力として受け取りのコレクションを生成<xref:System.Drawing.Bitmap>オブジェクトとして出力します。|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|コレクションを受け取って<xref:System.Drawing.Bitmap>オブジェクトを入力としてし、出力として複合ビットマップを生成します。|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|フォーム上に複合ビットマップを表示します。|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|操作が取り消されたことを示すためにイメージを表示し、ユーザーが別のフォルダーを選択できるようにします。|  
  
 この例では、ネットワークを形成するデータフロー ブロックを接続するには<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>メソッドです。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>メソッドには受け取るオーバー ロードされたバージョンが含まれています、<xref:System.Predicate%601>ターゲット ブロックが受け入れるか、メッセージを拒否するかどうかを決定するオブジェクト。 このフィルターのしくみによって、メッセージ ブロックは特定の値のみを受信できます。 この例では、ネットワークが、2 つに分岐します。 メイン分岐は、ディスクからイメージを読み込み、複合イメージを作成し、フォームにそのイメージを表示します。 もう 1 つの分岐では、現在の操作がキャンセルされます。 <xref:System.Predicate%601>オブジェクトが特定のメッセージを拒否することによって、別の分岐を切り替えるには、メイン分岐に沿ったデータ フロー ブロックを有効にします。 たとえば、ユーザーが操作をキャンセルした場合、データフロー ブロック `createCompositeBitmap` で、`null`([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `Nothing`) が出力として生成されます。 データフロー ブロック `displayCompositeBitmap` では、`null` 入力値が拒否されるため、メッセージが `operationCancelled` に提供されます。 データフロー ブロック `operationCancelled` はすべてのメッセージを受け入れるため、操作が取り消されたことを示すためにイメージを表示します。  
  
 次の図は、イメージ処理ネットワークを示しています。  
  
 ![イメージ処理ネットワーク](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 `displayCompositeBitmap` と `operationCancelled` のデータフロー ブロックはユーザー インターフェイスで機能するので、これらの操作をユーザー インターフェイス スレッドで実行することが重要です。 これを実現する、構築時に、これらのオブジェクトは各の提供、<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>を持つオブジェクト、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>プロパティに設定<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>です。 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。 ユーザー インターフェイス スレッドで実行される`CreateImageProcessingNetwork` メソッドは、**[フォルダーの選択]** ボタンのハンドラーから呼び出されるため、`displayCompositeBitmap` と`operationCancelled` のデータフロー ブロックのアクションも、ユーザー インターフェイス スレッドで実行されます。  
  
 この例の設定ではなく、共有のキャンセル トークンを使用して、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティのため、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティが完全にデータ フロー ブロックの実行をキャンセルします。 キャンセル トークンによって、この例では、ユーザーが 1 つまたは複数の操作をキャンセルしたときにも、同じデータフロー ネットワークを複数回再利用できます。 使用する例については<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>取り消すには完全にデータ フロー ブロックの実行、次を参照してください。[する方法: データフロー ブロックをキャンセル](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)です。  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>ユーザー インターフェイスへのデータフロー ネットワークの接続  
 このセクションでは、ユーザー インターフェイスにデータフロー ネットワークを接続する方法を説明します。 複合イメージの作成と、操作のキャンセルは、**[フォルダーの選択]** と **[キャンセル]** の各ボタンから開始されます。 ユーザーがこのいずれかのボタンを選択すると、適切な操作が非同期的に開始されます。  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>ユーザー インターフェイスにデータフロー ネットワークを接続するには  
  
1.  メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**フォルダーを選択**ボタンをクリックします。  
  
2.  実装、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**フォルダーを選択**ボタンをクリックします。  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**キャンセル**ボタンをクリックします。  
  
4.  実装、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**キャンセル**ボタンをクリックします。  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>完全な例  
 次の例は、このチュートリアルのコード全体を示しています。  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 次の図は、一般的な \Sample Pictures\ フォルダーの典型的な出力を示しています。  
  
 ![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
