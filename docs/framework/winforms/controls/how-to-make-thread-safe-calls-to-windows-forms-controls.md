---
title: "方法 : Windows フォーム コントロールのスレッド セーフな呼び出しを行う | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHInvalidOperation.WinForms.IllegalCrossThreadCall"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "スレッド セーフ, 呼び出しコントロール [Windows フォーム]"
  - "呼び出しコントロール, スレッド セーフ [Windows フォーム]"
  - "CheckForIllegalCrossThreadCalls プロパティ [Windows フォーム]"
  - "Windows フォーム コントロール, マルチスレッド処理"
  - "BackgroundWorker クラス, 例"
  - "スレッド処理 [Windows フォーム], スレッド間の呼び出し"
  - "コントロール [Windows フォーム], マルチスレッド処理"
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : Windows フォーム コントロールのスレッド セーフな呼び出しを行う
マルチスレッドを使用して Windows フォーム アプリケーションのパフォーマンスを向上させる場合は、必ずスレッド セーフな方法でコントロールを呼び出してください。  
  
 Windows フォーム コントロールへのアクセスは、本質的にスレッド セーフではありません。 コントロールの状態を操作するスレッドが複数ある場合、コントロールが不整合な状態になる可能性があります。 競合状態やデッドロックなど、他のスレッド関連のバグが生じる可能性もあります。 コントロールへのアクセスがスレッド セーフな方法で実行されることを確認することが重要です。  
  
 <xref:System.Windows.Forms.Control.Invoke%2A> メソッドを使用せずにコントロールを作成したスレッド以外のスレッドからコントロールを呼び出すのは安全ではありません。 スレッド セーフでない呼び出しの例を次に示します。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#6)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#6)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#6)]  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] は、スレッド セーフでない方法でコントロールにアクセスしていることを検出するのに役立ちます。 デバッガーでアプリケーションを実行しているときに、コントロールを作成したスレッド以外のスレッドがそのコントロールを呼び出そうとすると、デバッガーは <xref:System.InvalidOperationException> を発生させ、"コントロールが作成されたスレッド以外のスレッドからコントロール '*コントロール名*' がアクセスされました。" というメッセージが示されます。  
  
 この例外は、デバッグ時には確実に発生しますが、場合によっては実行時に発生することもあります。[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] より前に [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] を使用して、作成したアプリケーションのデバッグを行う場合に、この例外が発生することがあります。 この問題が発生したら修正することを強くお勧めしますが、<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> プロパティを `false` に設定して無効にすることもできます。 これによりコントロールは、Visual Studio .NET 2003 および [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)] の下で実行しているかのように実行されます。  
  
> [!NOTE]
>  フォームで ActiveX コントロールを使用している場合、デバッガー下で実行すると、スレッド間の <xref:System.InvalidOperationException> を受け取ることがあります。 これが発生した場合、ActiveX コントロールではマルチスレッドをサポートしていません。 Windows フォームでの ActiveX コントロールの使用の詳細については、「[Windows フォームとアンマネージ アプリケーション](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)」を参照してください。 Visual Studio を使用している場合、Visual Studio ホスティング プロセスを無効にすることで、この例外を防止できます。「[方法 : ホスト プロセスを無効にする](../Topic/How%20to:%20Disable%20the%20Hosting%20Process.md)」を参照してください。  
  
## Windows フォーム コントロールのスレッド セーフな呼び出し  
  
#### Windows フォーム コントロールのスレッド セーフな呼び出しを行うには  
  
1.  コントロールの <xref:System.Windows.Forms.Control.InvokeRequired%2A> プロパティを照会します。  
  
2.  <xref:System.Windows.Forms.Control.InvokeRequired%2A> から `true` が返された場合は、デリゲートを使用して <xref:System.Windows.Forms.Control.Invoke%2A> を呼び出します。このデリゲートがコントロールへの実際の呼び出しを行います。  
  
3.  <xref:System.Windows.Forms.Control.InvokeRequired%2A> から `false` が返された場合は、コントロールを直接呼び出します。  
  
 次のコード例では、スレッド セーフな呼び出しが `ThreadProcSafe` メソッドに実装されており、バックグラウンド スレッドによって実行されます。<xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.InvokeRequired%2A> から `true` が返された場合、`ThreadProcSafe` メソッドによって `SetTextCallback` のインスタンスが作成され、それがフォームの <xref:System.Windows.Forms.Control.Invoke%2A> メソッドに渡されます。 これにより、`SetText` メソッドが <xref:System.Windows.Forms.TextBox> コントロールを作成したスレッドで呼び出されます。また、このスレッド コンテキストで、<xref:System.Windows.Forms.Control.Text%2A> プロパティが直接設定されます。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#7)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#7)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#3)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#8)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#8)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#8)]  
  
## BackgroundWorker を使用したスレッド セーフな呼び出し  
 アプリケーションにマルチスレッドを実装する場合は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用することをお勧めします。<xref:System.ComponentModel.BackgroundWorker> コンポーネントでは、マルチスレッドにイベント ドリブン モデルが使用されます。 バックグラウンド スレッドが <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーを実行し、コントロールを作成したスレッドが <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーと <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーを実行します。<xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーと <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーからコントロールを呼び出すことができます。  
  
#### BackgroundWorker を使用してスレッド セーフな呼び出しを行うには  
  
1.  バックグラウンド スレッドで行われるようにする作業を実行するメソッドを作成します。 このメソッドで、メイン メソッドにより作成されたコントロールは呼び出さないでください。  
  
2.  バックグラウンド作業の終了後にその結果を報告するメソッドを作成します。 このメソッドではメイン スレッドにより作成されたコントロールを呼び出すことができます。  
  
3.  手順 1 で作成したメソッドを <xref:System.ComponentModel.BackgroundWorker.DoWork> のインスタンスの <xref:System.ComponentModel.BackgroundWorker> イベントにバインドし、手順 2 で作成したメソッドを同じインスタンスの <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントにバインドします。  
  
4.  バックグラウンド スレッドを開始するには、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> インスタンスの <xref:System.ComponentModel.BackgroundWorker> メソッドを呼び出します。  
  
 次のコード例では、<xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーが <xref:System.Threading.Thread.Sleep%2A> を使用して時間のかかる作業をシミュレートします。 フォームの <xref:System.Windows.Forms.TextBox> コントロールは呼び出しません。<xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティは <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーで直接設定されます。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#5)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#5)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#5)]  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#9)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#9)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#9)]  
  
 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントを使用して、バックグラウンド タスクの進行状況を報告することもできます。 そのイベントを組み込む例については、「<xref:System.ComponentModel.BackgroundWorker>」を参照してください。  
  
## 使用例  
 次のコード例は、3 つのボタンと 1 つのテキスト ボックスを持つフォームで構成される、完全な Windows フォーム アプリケーションです。 最初のボタンは安全でないスレッド間アクセスを示し、2 番目のボタンは <xref:System.Windows.Forms.Control.Invoke%2A> を使用した安全なアクセスを示し、3 番目のボタンは <xref:System.ComponentModel.BackgroundWorker> を使用した安全なアクセスを示します。  
  
> [!NOTE]
>  この例の実行方法については、「[How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/ja-jp/cc447f7e-4c3b-4397-9d05-aeba3ca49416)」を参照してください。 この例では、System.Drawing アセンブリと System.Windows.Forms アセンブリへの参照が必要です。  
  
 [!code-cpp[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CrossThreadCalls#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CrossThreadCalls/VB/Form1.vb#1)]  
  
 アプリケーションを実行し、**\[Unsafe Call\]** ボタンをクリックするとすぐに、テキスト ボックスに "Written by the main thread \(メイン スレッドで作成されました\)" と表示されます。 2 秒後、安全でない呼び出しが行われると、例外が発生したことが Visual Studio デバッガーにより示されます。 デバッガーは、テキスト ボックスに直接書き込もうとしたバックグラウンド スレッドの該当行で停止します。 他の 2 つのボタンをテストするには、アプリケーションを再起動する必要があります。**\[Safe Call\]** ボタンをクリックすると、テキスト ボックスに "Written by the main thread \(メイン スレッドで作成されました\)" と表示されます。 2 秒後、テキスト ボックスは "Written by the background thread \(Invoke\) \(バックグラウンド スレッドで書き込まれました \(呼び出し\)\)" に設定されます。これは、<xref:System.Windows.Forms.Control.Invoke%2A> メソッドが呼び出されたことを示します。**\[Safe BW Call\]** ボタンをクリックすると、テキスト ボックスに "Written by the main thread \(メイン スレッドで作成されました\)" と表示されます。 2 秒後、テキスト ボックスは "Written by the main thread after the background thread completed \(バックグラウンド スレッドの実行後にメイン スレッドで書き込まれました\)" に設定されます。これは、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> の <xref:System.ComponentModel.BackgroundWorker> イベントのハンドラーが呼び出されたことを示します。  
  
## 信頼性の高いプログラミング  
  
> [!CAUTION]
>  どのようなマルチスレッドを使用する場合でも、コードで深刻かつ複雑なバグが発生する可能性があります。 詳細については、マルチスレッドを使用するソリューションを実装する前に、「[Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)」を参照してください。  
  
## 参照  
 <xref:System.ComponentModel.BackgroundWorker>   
 [方法 : バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Windows フォームとアンマネージ アプリケーション](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)