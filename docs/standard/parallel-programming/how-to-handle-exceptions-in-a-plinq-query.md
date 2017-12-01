---
title: "方法: PLINQ クエリの例外を処理する"
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
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 209e0c1bf89f231d03647ae4351279bfdb172e68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>方法: PLINQ クエリの例外を処理する
このトピックの最初の例は、処理する方法を示しています、<xref:System.AggregateException?displayProperty=nameWithType>を実行すると、PLINQ クエリからスローされることができます。 2 番目の例では、例外がスローされますにできるだけ近い、デリゲート内で、try-catch ブロックを配置する方法を示します。 これによりとすぐに、発生する可能性のあるクエリの実行を続行して、キャッチすることができます。 連結しているスレッドへ例外が上方向へ通知されると、例外が発生した後も、クエリによって一部の項目の処理が続行される可能性があります。  
  
 場合によっては PLINQ に戻って、シーケンシャル実行と、例外が発生するときに例外が直接反映されでラップされません、<xref:System.AggregateException>です。 また、 <xref:System.Threading.ThreadAbortException>s が直接反映常にします。  
  
> [!NOTE]
>  「マイ コードのみ」を有効にすると、Visual Studio は例外をスローする行で中断し、「で処理されない例外ユーザー コードです」というエラー メッセージを表示 このエラーは問題にはなりません。 F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。  
>   
>  この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 この例をキャッチするクエリを実行するコードの周り、try-catch ブロックを配置する方法を示しています。 <xref:System.AggregateException?displayProperty=nameWithType>s は、スローされます。  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 この例では、クエリは、例外がスローされた後に続行できません。 時点では、アプリケーション コードが例外をキャッチ、PLINQ は既に停止クエリすべてのスレッドにします。  
  
## <a name="example"></a>例  
 次の例では、デリゲートで例外をキャッチし、クエリの実行を続行できるようにすることで、try-catch ブロックを配置する方法を示します。  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   コンパイルして、これらの例を実行、PLINQ データのサンプルにコピーし、Main からメソッドを呼び出します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 プログラムの状態が破損しないように、それを処理する方法を理解していない限り例外をキャッチしません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
