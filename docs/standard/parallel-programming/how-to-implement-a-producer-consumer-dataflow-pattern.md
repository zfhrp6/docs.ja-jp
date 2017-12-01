---
title: "方法: プロデューサー/コンシューマーのデータフロー パターンを実装する"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>方法: プロデューサー/コンシューマーのデータフロー パターンを実装する
このドキュメントでは、TPL データフロー ライブラリを使用して、プロデューサー/コンシューマー パターンを実装する方法について説明します。 このパターンでは、"*プロデューサー*" がメッセージをメッセージ ブロックに送信し、"*コンシューマー*" がそのブロックからメッセージを読み取ります。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="example"></a>例  
 次の例では、データフローを使用する基本的なプロデューサー/コンシューマー モデルを示します。 `Produce`メソッドは、データのランダム バイトを含む配列を書き込みます、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType>オブジェクトおよび`Consume`メソッドがからバイトを読み取り、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>オブジェクト。 操作を実行して、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>と<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>その派生型ではなく、インターフェイスのさまざまなデータ フロー ブロックの型で動作できる再利用可能なコードを記述できます。 この例では、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスです。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスは、両方のソースとして機能をブロックし、ターゲット ブロック、プロデューサーおよびコンシューマーを使用して、共有されたオブジェクト データを転送します。  
  
 `Produce`メソッドの呼び出し、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>ターゲット ブロックにデータを同期的に記述するループ内のメソッドです。 後に、`Produce`メソッドは呼び出しのターゲット ブロックにすべてのデータを書き込みます、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>を示す、ブロックが使用可能なその他のデータを持つことはありません。 `Consume`メソッドを使用、 [async](~/docs/csharp/language-reference/keywords/async.md)と[await](~/docs/csharp/language-reference/keywords/await.md)演算子 ([Async](~/docs/visual-basic/language-reference/modifiers/async.md)と[Await](~/docs/visual-basic/language-reference/operators/await-operator.md)で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) に非同期的にから受信されるバイトの合計数を計算、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>オブジェクト。 非同期的に動作する、`Consume`メソッドの呼び出し、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>メソッド、ソース ブロックがあり、使用可能なデータと、ソース ブロックには使用可能なその他のデータはないときに通知を受信します。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowProducerConsumer.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowProducerConsumer.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 この例では、1 つのコンシューマーのみを使用してソース データを処理します。 アプリケーションで複数のコンシューマーがあればを使用して、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>メソッドを次の例で示すように、ソース ブロックからデータを読み取ります。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>メソッドを返します。`False`データが使用できない場合。 このメカニズムでは、データは、呼び出しの後に引き続き使用できます保証複数のコンシューマーは、ソース ブロックを同時にアクセスする必要がある場合、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>です。  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
