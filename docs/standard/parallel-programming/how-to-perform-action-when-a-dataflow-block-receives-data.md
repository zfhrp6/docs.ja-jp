---
title: "方法: データフロー ブロックでデータを受信したときにアクションを実行する"
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
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d049d20f5e685096a72857cd18a89688633883c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>方法: データフロー ブロックでデータを受信したときにアクションを実行する
"*実行データフロー ブロック*" の型は、データを受信したときに、ユーザーが指定したデリゲートを呼び出します。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>クラスは、実行データ フロー ブロックの型。 使用することができます、`delegate`キーワード (`Sub`で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])、 <xref:System.Action%601>、 <xref:System.Func%602>、または実行データフロー ブロックを処理関数を提供する場合は、ラムダ式。 このドキュメントを使用する方法について説明<xref:System.Func%602>と実行ブロックで操作を実行するラムダ式。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="example"></a>例  
 次の例では、データフローを使用してディスクからファイルを読み取り、ファイル内のバイト数がゼロに等しい件数を計算します。 使用して<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>、ファイルを読み取り、ゼロのバイト数を計算して<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>をコンソールにゼロのバイト数を印刷します。 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクトを指定します、<xref:System.Func%602>ブロックのデータの受信時に作業を実行するオブジェクト。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトでは、ラムダ式を使用して、読み取られるゼロのバイト数をコンソールに出力します。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 ラムダ式を指定できますが、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクト、この例では<xref:System.Func%602>を使用するには、その他のコードを有効にする、`CountBytes`メソッドです。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>がであるため実行される作業は、このタスクを特定すると思われるその他のコードからに、オブジェクトは、ラムダ式を使用します。 タスク並列ライブラリでのラムダ式の動作の詳細については、「[PLINQ および TPL のラムダ式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
 デリゲート型の概要 セクションで、[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)ドキュメントを提供できるデリゲート型の概要を示します<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>オブジェクト。 表では、デリゲート型が同期的または非同期的に動作するかどうかについても示しています。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowExecutionBlocks.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowExecutionBlocks.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 この例では、型のデリゲート<xref:System.Func%602>を<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>データ フロー ブロックのタスクを同期的に実行するオブジェクト。 非同期的に動作するデータフロー ブロックを有効にするには、型のデリゲートを指定<xref:System.Func%601>データ フロー ブロックにします。 データ フロー ブロックは非同期に動作する、データ フロー ブロックのタスクは完了の場合にのみ、返された<xref:System.Threading.Tasks.Task%601>オブジェクトが完了するとします。 次の例では、`CountBytes` メソッドを変更して、[async](~/docs/csharp/language-reference/keywords/async.md) 演算子と [await](~/docs/csharp/language-reference/keywords/await.md) 演算子 ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では [Async](~/docs/visual-basic/language-reference/modifiers/async.md) と [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) を使用して、提供されたファイル内のゼロ バイトの件数の合計を非同期的に計算します。 <xref:System.IO.FileStream.ReadAsync%2A>メソッドは非同期的にファイル読み取り操作を実行します。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 実行データフロー ブロックでアクションを実行するために、非同期ラムダ式を使用することもできます。 次の例を変更、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>作業を非同期的に実行する、ラムダ式を使用するように、前の例で使用されるオブジェクト。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
