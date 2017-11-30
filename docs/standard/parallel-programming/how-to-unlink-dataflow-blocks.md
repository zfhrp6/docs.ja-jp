---
title: "方法: データフロー ブロックのリンクを解除する"
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a>方法: データフロー ブロックのリンクを解除する
このドキュメントでは、ターゲット データ フロー ブロックをソースからのリンクを解除する方法について説明します。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="example"></a>例  
 次の例では、3 つが作成されます<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>呼び出しの各オブジェクト、`TrySolution`値を計算するメソッド。 この例は、最初の呼び出しからの結果だけを必要と`TrySolution`を完了します。  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 最初の値を受け取る<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>が完了するとオブジェクトの場合は、この例で定義、`ReceiveFromAny(T)`メソッドです。 `ReceiveFromAny(T)`メソッドの配列を受け取る<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>オブジェクトし、これらの各オブジェクトにリンク、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクト。 使用すると、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>ソースをターゲット ブロックにソース データフロー ブロックをリンクするメソッドは、データが利用可能になったにターゲットにメッセージを伝達します。 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>クラスは、提供される最初のメッセージだけを受け取り、`ReceiveFromAny(T)`メソッドを呼び出してその結果を生成する、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>メソッドです。 これに提供される最初のメッセージが生成されます、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクト。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>メソッドを受け取るオーバー ロードされたバージョンには、<xref:System.Boolean>パラメーター、`unlinkAfterOne`に設定すると`True`ターゲットがソースから 1 つのメッセージを受信した後、ターゲットからリンクを解除するソース ブロックするよう指示します。 必要があります、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>ためにそのソースからリンクを解除するオブジェクト ソースの配列の間のリレーションシップと<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>後にオブジェクトが不要、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトがメッセージを受信します。  
  
 残りの呼び出しを有効にする`TrySolution`終了後、値が計算うちの 1 つに、`TrySolution`メソッドは、<xref:System.Threading.CancellationToken>オブジェクトへの呼び出し後に取り消された`ReceiveFromAny(T)`を返します。 <xref:System.Threading.SpinWait.SpinUntil%2A>メソッドが返すときにこの<xref:System.Threading.CancellationToken>オブジェクトが取り消されました。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowReceiveAny.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowReceiveAny.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
