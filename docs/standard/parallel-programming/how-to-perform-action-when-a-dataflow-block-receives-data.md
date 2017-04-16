---
title: "How to: Perform Action When a Dataflow Block Receives Data | Microsoft Docs"
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
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, receiving data"
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Perform Action When a Dataflow Block Receives Data
*実行データ フローのブロック型は* データを受け取ったときにユーザーが指定したデリゲートを呼び出します。  <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=fullName>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=fullName>と <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=fullName> クラスは実行データ フローのブロック型です。  `delegate` の実行データ フローのブロックに処理関数を提供するとキーワード \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`Sub`\)、<xref:System.Action%601>、<xref:System.Func%602>、またはラムダ式を使用できます。  このドキュメントでは、実行ブロックにアクションを実行する場合に <xref:System.Func%602> とラムダ式を使用する方法について説明します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## 使用例  
 次の例は、ディスク上のファイルの読み取りにデータ フローを使用し、ゼロと同じファイルのバイト数を計算します。  このパラメーターは、ファイルを読み取り、それをコンソールにゼロ バイト数を印刷するために、バイト数を計算するために <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> と <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> を使用します。  <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトはブロックがデータを受信するときに処理を実行するに <xref:System.Func%602> オブジェクトを指定します。  <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトは、コンソールに読み取り、バイト数を出力するためにラムダ式を使用します。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトにラムダ式を使用できますが `CountBytes` のメソッドが他のコードを有効にするために、この例では <xref:System.Func%602>。  <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトは、実行する作業がこのタスクに固有であり、他のコードから役に立つとは異なります。ラムダ式を使用します。  ラムダ式は、タスク並列ライブラリでどのように動作するか詳細については、「[Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) ドキュメントのデリゲート型の概要セクションは、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>と <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> オブジェクトに割り当てることのできるデリゲート型をまとめたものです。  この表では、デリゲート型を同期的または非同期的に実行するかどうかを指定します。  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`DataflowExecutionBlocks.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`DataflowExecutionBlocks.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## 信頼性の高いプログラミング  
 この例では <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトからデータ フローのブロックのタスクを同期的に実行 <xref:System.Func%602> 型のデリゲートを示します。  データ フローのブロックを非同期的に実行できるようにするには、データ フローのブロックに <xref:System.Func%601> 型のデリゲートを提供します。  データ フローのブロックを非同期的に実行すると、データ フローのブロックのタスクは <xref:System.Threading.Tasks.Task%601> から返されたオブジェクトのみが完了すると完了します。  次の例では `CountBytes` のメソッドを変更し、[async](../Topic/async%20\(C%23%20Reference\).md) を使用し、非同期的にあるバイト数の合計を計算する [待機します。](../Topic/await%20\(C%23%20Reference\).md) の演算子 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の[Async](../Topic/Async%20\(Visual%20Basic\).md) と [待機します。](../Topic/Await%20Operator%20\(Visual%20Basic\).md)\) を指定されたファイルにゼロを返します。  <xref:System.IO.FileStream.ReadAsync%2A> メソッドは、ファイルの読み取り操作を非同期的に実行します。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 実行データ フローのブロックで操作を非同期にラムダ式を使用できます。  次の例では、非同期的に作業を行うためにラムダ式を使用する場合は、前の例で使用した <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトを変更します。  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)