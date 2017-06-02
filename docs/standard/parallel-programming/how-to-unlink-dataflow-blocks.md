---
title: "How to: Unlink Dataflow Blocks | Microsoft Docs"
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
  - "dataflow blocks, unlinking in TPL"
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, unlinking dataflow blocks"
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Unlink Dataflow Blocks
このドキュメントでは、ソースのデータ フローのターゲット ブロックのリンクを解除方法について説明します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## 使用例  
 次の例は、呼び出しの各値を計算する `TrySolution` のメソッド <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> の 3 種類のオブジェクトを作成します。  この例では、最初の呼び出しから `TrySolution` に結果だけを終了する必要があります。  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 完了が、この例 `ReceiveFromAny(T)` のメソッドを定義する場合、最初の <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> から値を受け取るには使用します。  `ReceiveFromAny(T)` のメソッドは <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトの配列を受け取り、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトにオブジェクトにリンクします。  ターゲット ブロックにソース データ フローのブロックのリンクに <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> のメソッドを使用すると、ソースとターゲットのデータが使用可能になったときにメッセージを伝達します。  提供されること <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> クラスの最初のメッセージだけを受け取るため、`ReceiveFromAny(T)` のメソッドは <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> のメソッドを呼び出して結果を生成します。  これは <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトに提供される最初のメッセージを生成します。  <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> のメソッドに <xref:System.Boolean> パラメーターを使用するオーバーロードされたバージョン、ターゲットが 1 回のソースからメッセージを受信すると `True`に設定されている場合、ターゲットからソース ブロックを解除するように指示する `unlinkAfterOne` があります。  <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトがメッセージを受信するとソースの配列と <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトとの関係が不要なため <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトは、ソースからリンクが解除されることが重要です。  
  
 これらの 1 つが計算値、`TrySolution` のメソッドの戻り `ReceiveFromAny(T)` 呼び出しの後で実行 <xref:System.Threading.CancellationToken> オブジェクトを取得した後に、残りの呼び出しが終了することを `TrySolution` を有効にします。  <xref:System.Threading.CancellationToken> オブジェクトがキャンセルされた場合に <xref:System.Threading.SpinWait.SpinUntil%2A> メソッドは true を返します。  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`DataflowReceiveAny.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`DataflowReceiveAny.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## 信頼性の高いプログラミング  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)