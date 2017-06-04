---
title: "Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern | Microsoft Docs"
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
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern
一部の操作によって著しい遅延が発生する可能性があるクラスを記述する場合は、[Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) の実装による非同期機能の追加を検討してください。  
  
 このチュートリアルでは、イベント ベースの非同期パターンを実装するコンポーネントの作成方法を示します。  これは <xref:System.ComponentModel?displayProperty=fullName> 名前空間からヘルパー クラスを使用して実装されます。これによりコンポーネントは、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、コンソール アプリケーション、および Windows フォーム アプリケーションを含む任意のアプリケーション モデルで正常に動作します。  また、このコンポーネントは、<xref:System.Windows.Forms.PropertyGrid> コントロールおよび独自のカスタム デザイナーでデザインが可能です。  
  
 これが終了すると、素数を非同期的に計算するアプリケーションの用意ができます。  アプリケーションには、メインのユーザー インターフェイス \(UI\) スレッドと、各素数計算のためのスレッドが含まれます。  大きな数が素数かどうかのテストには時間がかかりますが、メインの UI スレッドがこの遅延によって中断されることはなく、計算中もフォームは応答可能な状態です。  同時にいくつでも計算を実行でき、保留中の計算を個別に選択してキャンセルできます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   コンポーネントの作成  
  
-   パブリック非同期イベントおよびデリゲートの定義  
  
-   プライベート デリゲートの定義  
  
-   パブリック イベントの実装  
  
-   完了メソッドの実装  
  
-   ワーカー メソッドの実装  
  
-   開始およびキャンセル メソッドの実装  
  
 このトピックのコードを単一のリストとしてコピーするには、「[How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)」を参照してください。  
  
## コンポーネントの作成  
 最初に、イベント ベースの非同期パターンを実装するコンポーネントを作成します。  
  
#### コンポーネントを作成するには  
  
-   <xref:System.ComponentModel.Component> から継承した、`PrimeNumberCalculator` という名前のクラスを作成します。  
  
## パブリック非同期イベントおよびデリゲートの定義  
 コンポーネントは、イベントを使用してクライアントと通信します。  *MethodName*`Completed` イベントは、非同期タスクの完了にクライアントに表示され、*MethodName*`ProgressChanged` イベントは、非同期タスクの進行状況をクライアントに通知します。  
  
#### コンポーネントのクライアントの非同期イベントを定義するには  
  
1.  <xref:System.Threading?displayProperty=fullName> および <xref:System.Collections.Specialized?displayProperty=fullName> 名前空間をファイルの先頭にインポートします。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  `PrimeNumberCalculator`  クラスの定義の前に、進行状況および完了のイベントのデリゲートを宣言します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  `PrimeNumberCalculator`  クラスの定義の前に、進行状況および完了をクライアントにレポートするイベントを宣言します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  `PrimeNumberCalculator`  クラスの定義の後に、 `CalculatePrimeCompletedEventArgs`  クラスを派生させて、各計算の結果を `CalculatePrimeCompleted`.event のクライアントのイベント ハンドラーにレポートします。  `AsyncCompletedEventArgs` プロパティに加えて、このクラスにより、クライアントはどの数値がテストされたのか、素数かどうか、素数でない場合は最初の除数は何かを判断できます。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## チェックポイント  
 この時点で、コンポーネントをビルドできます。  
  
#### コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
     次の 2 つのコンパイラの警告が表示されます。  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     これらの警告は、次のセクションでは消去されます。  
  
## プライベート デリゲートの定義  
 `PrimeNumberCalculator`  コンポーネントの非同期的な側面は、<xref:System.Threading.SendOrPostCallback> と呼ばれる特別なデリゲートと共に、内部的に実装されます。  <xref:System.Threading.SendOrPostCallback> はコールバック メソッドを表し、<xref:System.Threading.ThreadPool> スレッドで実行されます。  コールバック メソッドには、型 <xref:System.Object> の単一のパラメーターを受け取るシグネチャが必要です。つまり、デリゲート間の状態をラッパー クラスに渡す必要があります。  詳細については、「<xref:System.Threading.SendOrPostCallback>」を参照してください。  
  
#### コンポーネントの内部的な非同期動作を実装するには  
  
1.  `PrimeNumberCalculator`  クラス内に <xref:System.Threading.SendOrPostCallback> デリゲートを宣言および作成します。   `InitializeDelegates` という名前のユーティリティ メソッド内に、<xref:System.Threading.SendOrPostCallback> オブジェクトを作成します。  
  
     クライアントに進行状況を報告するためと、クライアントに完了を報告するための 2 つのデリゲートが必要です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  コンポーネントのコンストラクター内で `InitializeDelegates` メソッドを呼び出します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  `PrimeNumberCalculator` クラス内で、非同期的に行われる実際の作業を処理するデリゲートを宣言します。  このデリゲートは、数値が素数かどうかをテストするワーカー メソッドをラップします。  デリゲートは <xref:System.ComponentModel.AsyncOperation> パラメーターを受け取ります。これは、非同期操作の有効期間を追跡するのに使用されます。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  保留中の非同期操作の有効期間を管理するコレクションを作成します。  クライアントには、実行時および完了時に操作を追跡する手段が必要です。クライアントが非同期メソッドを呼び出したときに、クライアントに一意なトークン \(タスク ID\) を渡すように要求することによって、この追跡を行います。  `PrimeNumberCalculator` コンポーネントは、タスク ID を対応する呼び出しに関連付けて、各呼び出しを追跡する必要があります。  クライアントから一意ではないタスク ID が渡された場合は、`PrimeNumberCalculator` コンポーネントで例外を発生させる必要があります。  
  
     `PrimeNumberCalculator` コンポーネントは、<xref:System.Collections.Specialized.HybridDictionary> と呼ばれる特別なコレクション クラスを使用して、タスク ID を追跡します。  クラス定義内で、 `userTokenToLifetime` という名前の <xref:System.Collections.Specialized.HybridDictionary> を作成します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## パブリック イベントの実装  
 イベント ベースの非同期パターンを実装するコンポーネントは、イベントを使用してクライアントと通信します。  これらのイベントは、<xref:System.ComponentModel.AsyncOperation> クラスのおかげで、適切なスレッドで呼び出されます。  
  
#### コンポーネントのクライアントに対してイベントを発生させるには  
  
1.  クライアントにレポートするために、パブリック イベントを実装します。  進行状況をレポートするためのイベントと、完了をレポートするためのイベントが必要です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## 完了メソッドの実装  
 完了デリゲートとは、非同期操作が正常な完了、エラー、またはキャンセルによって終了したときに、基になるフリースレッドの非同期動作を呼び出すメソッドです。  この呼び出しは任意のスレッドで発生します。  
  
 このメソッドでは、一意なクライアント トークンの内部コレクションからクライアントのタスク ID を削除します。  また、このメソッドは、対応する <xref:System.ComponentModel.AsyncOperation> で <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> メソッドを呼び出すことにより、特定の非同期操作の有効期間を終了します。  この呼び出しにより、アプリケーション モデルに適したスレッドで完了イベントが発生します。  <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> メソッドが呼び出された後、<xref:System.ComponentModel.AsyncOperation> のこのインスタンスは使用できなくなります。これ以降、これを使用しようとすると、例外がスローされます。  
  
 `CompletionMethod` シグネチャには、非同期操作の結果を記述するために必要なすべての状態が格納されている必要があります。  これには、この特定の非同期操作によってテストされた数値と、数値が素数かどうか、素数でない場合はその最初の除数の値の状態が格納されます。  また、発生した例外と、この特定のタスクに対応する <xref:System.ComponentModel.AsyncOperation> を示す状態も格納されます。  
  
#### 非同期操作を完了するには  
  
-   完了メソッドを実装します。  6 つのパラメーターを受け取ります。これらを使用して  `CalculatePrimeCompletedEventArgs` が作成され、クライアントの  `CalculatePrimeCompletedEventHandler` を介してクライアントに返されます。  クライアントのタスク ID トークンを内部コレクションから削除し、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> の呼び出しにより、非同期操作の有効期間を終了します。  <xref:System.ComponentModel.AsyncOperation> は、アプリケーション モデルに適したスレッドまたはコンテキストの呼び出しをマーシャリングします。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## チェックポイント  
 この時点で、コンポーネントをビルドできます。  
  
#### コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
     次のコンパイラの警告が表示されます。  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     この警告は、次のセクションでは解決されます。  
  
## ワーカー メソッドの実装  
 ここまでで、`PrimeNumberCalculator` コンポーネントをサポートしている非同期コードを実装しました。  次に、実際の作業を行うコードを実装します。  `CalculateWorker`、 `BuildPrimeNumberList`、`IsPrime` の 3 つのメソッドを実装します。  `BuildPrimeNumberList` と `IsPrime` は、エラトステネスのふるいと呼ばれる有名なアルゴリズムを構成します。このアルゴリズムは、テスト数値の平方根まですべての素数を検索して、数値が素数かどうかを調べます。  その時点で除数が見つからない場合、そのテスト数値は素数です。  
  
 効率を最大限に高めるためにこのコンポーネントが記述されている場合は、異なるテスト数値のさまざまな呼び出しによって検出されたすべての素数を記憶します。  また、2、3、5 などの単純な除数もチェックします。  この例の目的は、時間のかかる操作を非同期的に実行する方法を示すことですが、練習用にこれらの最適化も残しておきます。  
  
 `CalculateWorker` メソッドはデリゲート内にラップされており、`BeginInvoke` の呼び出しによって非同期的に呼び出されます。  
  
> [!NOTE]
>  進行状況の報告は、`BuildPrimeNumberList` メソッドによって実装されます。  高速のコンピューターでは、`ProgressChanged` イベントがすばやく連続して発生する場合があります。  こうしたイベントが発生するクライアント スレッドでは、この状況に対応できる必要があります。  ユーザー インターフェイス コードにメッセージがあふれて処理が追いつかなくなり、ハングする可能性があります。  この状況に対応するユーザー インターフェイス例については、「[How to: Implement a Client of the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)」を参照してください。  
  
#### 素数の計算を非同期的に実行するには  
  
1.  `TaskCanceled` ユーティリティ メソッドを実装します。  これにより、指定したタスク ID のタスクの有効期間コレクションがチェックされ、タスク ID が見つからなかった場合は、`true` が返されます。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  `CalculateWorker` メソッドを実装します。  2 つのパラメーターを受け取ります。テストする数値および <xref:System.ComponentModel.AsyncOperation> です。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  `BuildPrimeNumberList` を実装します。  2 つのパラメーターを受け取ります。テストする数値と <xref:System.ComponentModel.AsyncOperation> です。  <xref:System.ComponentModel.AsyncOperation> を使用して、進行状況およびインクリメンタル結果をレポートします。  これにより、クライアントのイベント ハンドラーが、アプリケーション モデルに適したスレッドまたはコンテキストで呼び出されるようになります。  `BuildPrimeNumberList` は素数を検出すると、これをインクリメンタル結果として、`ProgressChanged` イベントのクライアントのイベント ハンドラーにレポートします。  これには、<xref:System.ComponentModel.ProgressChangedEventArgs> から派生した `CalculatePrimeProgressChangedEventArgs` と呼ばれるクラスが必要です。このクラスには、`LatestPrimeNumber` と呼ばれる追加されたプロパティが 1 つあります。  
  
     また、`BuildPrimeNumberList` メソッドは、定期的に `TaskCanceled` メソッドを呼び出し、`true` が返されると終了します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  `IsPrime` を実装します。  3 つのパラメーターを受け取ります。既知の素数のリスト、テストする数値、および見つかった最初の除数の出力パラメーターです。  素数のリストを指定すると、テスト数値が素数かどうかを確認します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  `CalculatePrimeProgressChangedEventArgs` を <xref:System.ComponentModel.ProgressChangedEventArgs> から派生させます。  このクラスは、`ProgressChanged` イベントのクライアントのイベント ハンドラーに、インクリメンタル結果をレポートするために必要です。  `LatestPrimeNumber` という名前の追加されたプロパティが 1 つあります。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## チェックポイント  
 この時点で、コンポーネントをビルドできます。  
  
#### コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
     この他に記述する必要があるものは、非同期操作を開始およびキャンセルするためのメソッド \(`CalculatePrimeAsync` および `CancelAsync`\) です。  
  
## 開始およびキャンセル メソッドの実装  
 ワーカー スレッドを独自のスレッドで開始するには、それをラップしているデリゲートで `BeginInvoke` を呼び出します。  特定の非同期操作の有効期間を管理するには、<xref:System.ComponentModel.AsyncOperationManager> ヘルパー クラスで <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> メソッドを呼び出します。  こうすると <xref:System.ComponentModel.AsyncOperation> が返され、適切なスレッドまたはコンテキストへのクライアントのイベント ハンドラーの呼び出しがマーシャリングされます。  
  
 特定の保留中の操作をキャンセルするには、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> を対応する <xref:System.ComponentModel.AsyncOperation> で呼び出します。  こうするとその操作が終了し、これ以降その <xref:System.ComponentModel.AsyncOperation> を呼び出すと例外がスローされます。  
  
#### 開始およびキャンセル機能を実装するには  
  
1.  `CalculatePrimeAsync` メソッドを実装します。  クライアントによって提供されたトークン \(タスク ID\) が、現在保留中のタスクを表すすべてのタスクから見て一意であることを確認します。  クライアントから一意ではないトークンが渡された場合は、`CalculatePrimeAsync` は例外を発生させます。  それ以外の場合は、トークンがタスク ID のコレクションに追加されます。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  `CancelAsync` メソッドを実装します。  トークン コレクションに `taskId` パラメーターが存在する場合は、削除されます。  これにより、起動されていないキャンセル済みタスクが実行されるのを防止します。  タスクが実行中の場合は、そのタスク ID が有効期間コレクションから削除されたことを `BuildPrimeNumberList` メソッドが検出すると、メソッドは終了します。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## チェックポイント  
 この時点で、コンポーネントをビルドできます。  
  
#### コンポーネントをテストするには  
  
-   コンポーネントをコンパイルします。  
  
 `PrimeNumberCalculator`  コンポーネントがコンパイルされ、使用できるようになります。  
  
 `PrimeNumberCalculator` コンポーネントを使用するクライアントの例については、「[How to: Implement a Client of the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)」を参照してください。  
  
## 次の手順  
 この例に入力するには、`CalculatePrimeAsync` メソッドの同期用である `CalculatePrime` を記述します。  こうすると、`PrimeNumberCalculator` コンポーネントがイベント ベースの非同期パターンに完全に準拠します。  
  
 この例を改善するには、異なるテスト数値のさまざまな呼び出しによって検出された、すべての素数のリストを保持します。  この方法を使用すると、以前のタスクで行われた作業が各タスクに役立ちます。  このリストを `lock` 領域で保護する際には注意が必要です。異なるスレッドによるリストへのアクセスはシリアル化されます。  
  
 2、3、5 などの単純な除数をテストしても、この例を改善できます。  
  
## 参照  
 [方法 : バックグラウンドで操作を実行する](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/ja-jp/c731a50c-09c1-4468-9646-54c86b75d269)   
 [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)