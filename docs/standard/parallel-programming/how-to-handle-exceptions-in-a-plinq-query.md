---
title: "How to: Handle Exceptions in a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to handle exceptions"
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# How to: Handle Exceptions in a PLINQ Query
このトピックの最初の例では、PLINQ クエリの実行時にスローされる <xref:System.AggregateException?displayProperty=fullName> の処理方法を示します。  2 番目の例では、デリゲート内で例外がスローされる場所のできるだけ近くに try\-catch ブロックを配置する方法を示します。  こうすると、発生の直後に例外をキャッチしてクエリの実行を続行できる可能性があります。  連結しているスレッドへ例外が上方向へ通知されると、例外が発生した後も、クエリによって一部の項目の処理が続行される可能性があります。  
  
 場合によっては、PLINQ が順次実行に戻り、例外が発生すると、例外が直接反映され、<xref:System.AggregateException> にラップされないことがあります。  また、<xref:System.Threading.ThreadAbortException> は常に直接反映されます。  
  
> [!NOTE]
>  \[マイ コードのみ\] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されます。このエラーは問題にはなりません。  F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。  Visual Studio による処理が最初のエラーで中断しないようにするには、**\[ツール\]** メニューの \[オプション\]、\[デバッグ\] の順にクリックし、\[全般\] で \[マイ コードのみ\] チェック ボックスをオフにします。  
>   
>  この例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。  高速化の詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 使用例  
 次の例は、スローされる <xref:System.AggregateException?displayProperty=fullName> をキャッチするクエリを実行するコードの近くに try\-catch ブロックを配置する方法を示しています。  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 この例では、例外がスローされた後にクエリを続行することはできません。  アプリケーション コードが例外をキャッチするまでに、PLINQ はすべてのスレッド上でクエリを停止しています。  
  
## 使用例  
 次の例は、例外をキャッチしてクエリの実行を続行できるようにするため、try\-catch ブロックをデリゲートに配置する方法を示しています。  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## コードのコンパイル  
  
-   これらの例をコンパイルして実行するには、これらのコードを PLINQ データのサンプルにコピーして、Main からメソッドを呼び出します。  
  
## 信頼性の高いプログラミング  
 プログラムの状態を破損しないようにするため、処理方法がわからない場合は、例外をキャッチしないでください。  
  
## 参照  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)