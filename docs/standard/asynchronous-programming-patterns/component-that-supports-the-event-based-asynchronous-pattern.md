---
title: "チュートリアル : イベントベースの非同期パターンをサポートするコンポーネントの実装"
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
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150e4b27cc149774895574ddd196de5f9bc2acd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>チュートリアル : イベントベースの非同期パターンをサポートするコンポーネントの実装
著しい遅延が発生する可能性がありますをいくつかの操作のクラスを作成している場合は、実装することによって、非同期機能を付けることを検討して、[イベント ベースの非同期パターン概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)です。  
  
 このチュートリアルでは、イベント ベースの非同期パターンを実装するコンポーネントを作成する方法について説明します。 ヘルパー クラスを使用して実装されている、<xref:System.ComponentModel?displayProperty=nameWithType>コンポーネントが正しく動作する任意のアプリケーション モデルで実行できるようにするには、名前空間を含む[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、コンソール アプリケーションと Windows フォーム アプリケーションです。 また、このコンポーネントは、<xref:System.Windows.Forms.PropertyGrid>コントロールや、独自のカスタム デザイナーです。  
  
 ときに非同期的に含まれる素数を計算するアプリケーションがあります。 アプリケーションは、主要なユーザー インターフェイス (UI) スレッドと各素数計算のためのスレッドがあります。 多数あるかどうかをテスト素数かなりの時間がかかることができます、この遅延によって、メイン UI スレッドは中断されませんやフォームが応答性の高い計算中にします。 多数の計算は自由に同時に、選択的に取り消しと保留中の計算を実行することができます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   コンポーネントの作成  
  
-   パブリックの非同期イベントおよびデリゲートを定義します。  
  
-   プライベート デリゲートの定義  
  
-   パブリック イベントを実装します。  
  
-   完了メソッドの実装  
  
-   ワーカー メソッドの実装  
  
-   開始とキャンセル メソッドの実装  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: イベント ベースの非同期パターンをサポートするコンポーネントを実装する](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)です。  
  
## <a name="creating-the-component"></a>コンポーネントの作成  
 最初の手順では、イベント ベースの非同期パターンを実装するコンポーネントを作成します。  
  
#### <a name="to-create-the-component"></a>コンポーネントを作成するには  
  
-   呼ばれるクラスを作成する`PrimeNumberCalculator`から継承する<xref:System.ComponentModel.Component>です。  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>パブリックの非同期イベントおよびデリゲートを定義します。  
 コンポーネントは、イベントを使用するクライアントと通信します。 *MethodName* `Completed` 、非同期タスクの完了をクライアントに警告イベント、および*MethodName* `ProgressChanged`イベントは、非同期タスクの進行状況のクライアントに通知します。  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>コンポーネントのクライアントの非同期イベントを定義します。  
  
1.  インポート、<xref:System.Threading?displayProperty=nameWithType>と<xref:System.Collections.Specialized?displayProperty=nameWithType>ファイルの上部にある名前空間。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  前に、`PrimeNumberCalculator`クラス定義、進行状況と完了イベントのデリゲートを宣言します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  `PrimeNumberCalculator`クラス定義、レポートの進行状況および完了をクライアントのイベントを宣言します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  後に、`PrimeNumberCalculator`クラス定義、派生、`CalculatePrimeCompletedEventArgs`のクライアントのイベント ハンドラーをそれぞれの計算の結果を報告のクラス、 `CalculatePrimeCompleted`.event です。 加え、`AsyncCompletedEventArgs`プロパティ、このクラスにより、クライアントは、どの番号がテストされているの主要なであるか、および最初の除数は素がないかどうかを決定します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点では、コンポーネントをビルドすることができます。  
  
#### <a name="to-test-your-component"></a>コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
     2 つのコンパイラ警告が表示されます。  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     次のセクションでは、これらの警告が消去されます。  
  
## <a name="defining-private-delegates"></a>プライベート デリゲートの定義  
 非同期の側面、`PrimeNumberCalculator`と呼ばれる特別なデリゲートを使用してコンポーネントを内部的に実装されます、<xref:System.Threading.SendOrPostCallback>です。 A<xref:System.Threading.SendOrPostCallback>で実行されるコールバック メソッドを表す、<xref:System.Threading.ThreadPool>スレッドです。 コールバック メソッドには、型の 1 つのパラメーターを受け取る署名が必要<xref:System.Object>、することができるはラッパー クラスでデリゲートの間で状態を渡す必要があります。 詳細については、「<xref:System.Threading.SendOrPostCallback>」を参照してください。  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>コンポーネントの内部の非同期動作を実装するには。  
  
1.  宣言し、作成、<xref:System.Threading.SendOrPostCallback>でデリゲート、`PrimeNumberCalculator`クラスです。 作成、<xref:System.Threading.SendOrPostCallback>ユーティリティ メソッド内のオブジェクトと呼ばれる`InitializeDelegates`です。  
  
     2 つのデリゲートが必要になります。 クライアントに進行状況をレポート用とクライアントの完了を報告します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  呼び出す、`InitializeDelegates`コンポーネントのコンス トラクターのメソッドです。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  デリゲートを宣言、`PrimeNumberCalculator`を非同期的に実行する実際の作業を処理するクラス。 このデリゲートは、数値が素数かどうかをテストするワーカー メソッドをラップします。 デリゲートは、<xref:System.ComponentModel.AsyncOperation>非同期操作の有効期間を追跡するために使用されるパラメーター。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  保留中の非同期操作の有効期間を管理するためのコレクションを作成します。 クライアントでは、この追跡を行うクライアントが非同期メソッドの呼び出しを作成するときに、一意のトークン、またはタスク ID を渡すクライアントを必要として、実行、完了すると、操作を追跡する方法が必要です。 `PrimeNumberCalculator`コンポーネント必要がありますの追跡の各呼び出しの対応する呼び出しと、タスク ID を関連付けることによってです。 クライアントがタスク ID が一意でないことに渡す場合、`PrimeNumberCalculator`コンポーネントが例外を発生させる必要があります。  
  
     `PrimeNumberCalculator`コンポーネントの追跡タスク ID と呼ばれる特別なコレクション クラスを使用して、<xref:System.Collections.Specialized.HybridDictionary>です。 クラス定義の作成、<xref:System.Collections.Specialized.HybridDictionary>と呼ばれる`userTokenToLifetime`です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>パブリック イベントを実装します。  
 イベント ベースの非同期パターンを実装するコンポーネントは、イベントを使用してクライアントに通信します。 これらのイベントが利用して適切なスレッドで呼び出される、<xref:System.ComponentModel.AsyncOperation>クラスです。  
  
#### <a name="to-raise-events-to-your-components-clients"></a>イベントを発生させるコンポーネントのクライアント。  
  
1.  クライアントへの報告のパブリック イベントを実装します。 イベントは、進行状況と完了をレポートに 1 つのレポートの必要があります。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>完了メソッドの実装  
 完了デリゲートは、非同期操作が正常に完了、エラー、またはキャンセルして終了時に、基になる、フリー スレッドの非同期動作で起動される方法です。 この呼び出しは、任意のスレッドで発生します。  
  
 このメソッドは、クライアントのタスクの ID が一意のクライアントのトークンの内部コレクションから削除する場所です。 また、このメソッドは呼び出すことによって、特定の非同期操作の有効期間を終了、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>メソッドを対応する<xref:System.ComponentModel.AsyncOperation>です。 この呼び出しでは、アプリケーション モデルを適切なスレッドで完了イベントを発生させます。 後に、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>メソッドは、このインスタンスの<xref:System.ComponentModel.AsyncOperation>使用できなくでき、それを使用しようとした後は例外をスローします。  
  
 `CompletionMethod`署名が保持するすべての状態、非同期操作の結果を記述するために必要です。 素数の数値ではない場合、数値が素数と、最初の除数の値かどうかは、この特定の非同期操作によってテストされた数の状態を保持します。 状態が発生した任意の例外を記述するも保持し、<xref:System.ComponentModel.AsyncOperation>この特定のタスクに対応します。  
  
#### <a name="to-complete-an-asynchronous-operation"></a>非同期操作を完了します。  
  
-   完了メソッドを実装します。 設定にそれを使用して、6 つのパラメーター、`CalculatePrimeCompletedEventArgs`を通じて、クライアントのクライアントに返される`CalculatePrimeCompletedEventHandler`です。 内部のコレクションから、クライアントのタスクの ID トークンを削除しを呼び出して非同期操作の有効期間終了<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>です。 <xref:System.ComponentModel.AsyncOperation>スレッドまたはコンテキストに適したアプリケーション モデルへの呼び出しをマーシャ リングします。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点では、コンポーネントをビルドすることができます。  
  
#### <a name="to-test-your-component"></a>コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
     コンパイラの警告が表示されます。  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     この警告は、次のセクションでは解決されます。  
  
## <a name="implementing-the-worker-methods"></a>ワーカー メソッドの実装  
 これまでのサポート、非同期コードを実装している、`PrimeNumberCalculator`コンポーネントです。 実際の処理を行うコードを実装できます。 次の 3 つの方法を実装する: `CalculateWorker`、 `BuildPrimeNumberList`、および`IsPrime`です。 同時に、`BuildPrimeNumberList`と`IsPrime`篩のエラトステネス、かどうかを数値素数テスト数値の平方根までのすべての素数を検索するいると呼ばれる、よく知られているアルゴリズムを構成します。 その時点で除数が見つからない場合、テストの数は、素数です。  
  
 このコンポーネントは、効率性を高める用に作成された場合、異なるテスト数値のさまざまな呼び出しによって検出されたすべての素数を記憶します。 2、3、5 などの単純な除数もチェックします。 どの時間のかかる操作を示すためには、この例の目的は、実行できる非同期で、ただし、ため、これらの最適化は、手順のままにします。  
  
 `CalculateWorker`メソッドは、デリゲートにラップされ、呼び出しを非同期で呼び出される`BeginInvoke`です。  
  
> [!NOTE]
>  進行状況レポートでは実装されて、`BuildPrimeNumberList`メソッドです。 高速なコンピューターは、`ProgressChanged`すばやく連続的にイベントを発生することができます。 これらのイベントが発生した、クライアントのスレッドは、このような状況を処理できる必要があります。 ユーザー インターフェイスのコードのメッセージであふれしてありますに対する遅れ、ハングします。 このような状況を処理する例のユーザー インターフェイスを参照してください。[する方法: イベント ベースの非同期パターンのクライアントを実装する](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)です。  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>素数の計算を非同期的に実行するには。  
  
1.  実装、`TaskCanceled`ユーティリティ メソッドです。 これは、指定したタスクの ID のタスクの有効期間のコレクションをチェックし、返します`true`タスク ID が見つからない場合。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  `CalculateWorker` メソッドを実装します。 2 つのパラメーター: 数をテストするには、<xref:System.ComponentModel.AsyncOperation>です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  `BuildPrimeNumberList` を実装します。 2 つのパラメーター: をテストするには、番号と<xref:System.ComponentModel.AsyncOperation>です。 使用して、<xref:System.ComponentModel.AsyncOperation>レポートの進行状況およびインクリメンタル結果をします。 これで、適切なスレッドまたはアプリケーション モデルのコンテキストで、クライアントのイベント ハンドラーを呼び出すことができます。 ときに`BuildPrimeNumberList`素数見つかると、報告この増分の結果としてのクライアントのイベント ハンドラーに、`ProgressChanged`イベント。 派生したクラスが必要です<xref:System.ComponentModel.ProgressChangedEventArgs>という`CalculatePrimeProgressChangedEventArgs`、これがいずれかの追加と呼ばれるプロパティ`LatestPrimeNumber`です。  
  
     `BuildPrimeNumberList`メソッドも定期的に呼び出して、`TaskCanceled`メソッドと終了メソッドを返す場合`true`です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  `IsPrime` を実装します。 3 つのパラメーター: 既知の素数をテストする数、および最初に見つかった除数の出力パラメーターの一覧です。 素数のリストを指定するには、テスト数は素数が決定されます。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  派生`CalculatePrimeProgressChangedEventArgs`から<xref:System.ComponentModel.ProgressChangedEventArgs>です。 このクラスは、クライアントのイベント ハンドラーにインクリメンタル結果を報告するために必要な`ProgressChanged`イベント。 呼ばれる 1 つの追加プロパティがある`LatestPrimeNumber`です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点では、コンポーネントをビルドすることができます。  
  
#### <a name="to-test-your-component"></a>コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
     書き込まれるは開始して、非同期操作をキャンセルする方法は、すべて`CalculatePrimeAsync`と`CancelAsync`です。  
  
## <a name="implementing-the-start-and-cancel-methods"></a>開始とキャンセル メソッドの実装  
 呼び出すことにより、独自のスレッドで、ワーカー スレッドを開始する`BeginInvoke`でそれをラップするデリゲート。 特定の非同期操作の有効期間を管理するを呼び出す、<xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>メソッドを<xref:System.ComponentModel.AsyncOperationManager>ヘルパー クラス。 これを返します、 <xref:System.ComponentModel.AsyncOperation>、適切なスレッドまたはコンテキストに、クライアントのイベント ハンドラーに呼び出しをマーシャ リングします。  
  
 呼び出して、特定の保留中の操作を取り消す<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>それに対応する <xref:System.ComponentModel.AsyncOperation>です。 これは、操作を終了する、し、後続の呼び出し、<xref:System.ComponentModel.AsyncOperation>例外がスローされます。  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>開始を実装する機能をキャンセルします。  
  
1.  `CalculatePrimeAsync` メソッドを実装します。 クライアントが指定したトークン (タスク ID) が現在保留中のタスクを表すすべてのトークンで一意であることを確認してください。 クライアントが非一意のトークンで渡す場合`CalculatePrimeAsync`例外が発生します。 それ以外の場合、トークンは、タスク ID のコレクションに追加されます。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  `CancelAsync` メソッドを実装します。 場合、`taskId`トークンのコレクションにパラメーターが存在し、削除されます。 これは、取り消されたタスクの実行を開始していないことを防ぎます。 タスクが実行されている場合、`BuildPrimeNumberList`メソッドは、タスク ID が有効期間のコレクションから削除されたことを検出した場合に終了します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点では、コンポーネントをビルドすることができます。  
  
#### <a name="to-test-your-component"></a>コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
 `PrimeNumberCalculator`コンポーネントは完全で使用できるようにします。  
  
 使用する例をクライアントに対して、`PrimeNumberCalculator`コンポーネントを参照してください[する方法: イベント ベースの非同期パターンのクライアントを実装する](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)です。  
  
## <a name="next-steps"></a>次の手順  
 この例を記入を記述して`CalculatePrime`、同期に相当`CalculatePrimeAsync`メソッドです。 これは、操作を行う、`PrimeNumberCalculator`コンポーネント、イベント ベースの非同期パターンに完全に準拠します。  
  
 別のテストの数値のさまざまな呼び出しによって検出されたすべての素数のリストを保持すると、この例を向上できます。 このアプローチを使用して、各タスクは、以前のタスクで行われる作業からメリットがあります。 この一覧を保護するように注意する`lock`領域の場合、別のスレッドでリストへのアクセスがシリアル化されるようにします。  
  
 この例は、2、3、5 などの単純な除数のテストによっても向上できます。  
  
## <a name="see-also"></a>関連項目  
 [方法: バックグラウンドで操作を実行する](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NOT IN BUILD: Visual Basic でのマルチ スレッド](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [方法: イベントベースの非同期パターンをサポートするコンポーネントを実装する](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [イベント ベースの非同期パターンを使用したマルチスレッド プログラミング](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
