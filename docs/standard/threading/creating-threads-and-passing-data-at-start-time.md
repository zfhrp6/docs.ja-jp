---
title: "スレッドを作成し、開始時にデータを渡す"
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>スレッドを作成し、開始時にデータを渡す
オペレーティング システム プロセスが作成されると、オペレーティング システムは、元のアプリケーション ドメインを含め、そのプロセスでコードを実行するスレッドを挿入します。 その時点から、アプリケーション ドメインを作成および破棄オペレーティング システム スレッドを必ずしも作成中または破棄します。 実行対象のコードが管理されている場合、コード、<xref:System.Threading.Thread>オブジェクトの静的なを取得することによって、現在のアプリケーション ドメインで実行するスレッドを取得できるの<xref:System.Threading.Thread.CurrentThread%2A>型のプロパティ<xref:System.Threading.Thread>です。 このトピックでは、スレッドの作成について説明し、データをスレッド プロシージャに渡すための代替案について説明します。  
  
## <a name="creating-a-thread"></a>スレッドを作成します。  
 新たに作成する<xref:System.Threading.Thread>オブジェクトは、新しいマネージ スレッドを作成します。 <xref:System.Threading.Thread>クラスを受け取るコンス トラクターには、<xref:System.Threading.ThreadStart>委任または<xref:System.Threading.ParameterizedThreadStart>委任; デリゲートを呼び出すときに、新しいスレッドで呼び出されるメソッドをラップする、<xref:System.Threading.Thread.Start%2A>メソッドです。 呼び出す<xref:System.Threading.Thread.Start%2A>により複数回、<xref:System.Threading.ThreadStateException>がスローされます。  
  
 <xref:System.Threading.Thread.Start%2A>メソッドを返しますすぐに、多くの場合、新しいスレッドが実際に開始する前にします。 使用することができます、<xref:System.Threading.Thread.ThreadState%2A>と<xref:System.Threading.Thread.IsAlive%2A>スレッドの活動を同期するためのプロパティを 1 つの時点でスレッドの状態の確認がこれらのプロパティを使用する必要があることはありません。  
  
> [!NOTE]
>  参照を保持する必要はありませんは、スレッドの開始後、<xref:System.Threading.Thread>オブジェクト。 スレッドは、スレッド プロシージャが終了するまでの実行を継続します。  
  
 次のコード例では、別のオブジェクトのインスタンスと静的メソッドを呼び出す 2 つの新しいスレッドを作成します。  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>データをスレッドに渡すと、スレッドからデータを取得します。  
 .NET framework version 2.0 では、<xref:System.Threading.ParameterizedThreadStart>デリゲートを呼び出すときに、スレッドにデータを格納するオブジェクトを渡すための簡単な方法を提供する、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>メソッドのオーバー ロードします。 コード例については、「<xref:System.Threading.ParameterizedThreadStart>」を参照してください。  
  
 使用して、<xref:System.Threading.ParameterizedThreadStart>デリゲートは、タイプ セーフな方法、データを渡すため、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>メソッドのオーバー ロードは、任意のオブジェクトを受け取ります。 代わりに、スレッド処理とヘルパー クラスでデータをカプセル化しを使用し、<xref:System.Threading.ThreadStart>スレッド プロシージャを実行するデリゲート。 この手法は次の 2 つのコード例に示します。  
  
 どちらの非同期呼び出しのデータを返す先がないために、デリゲートは戻り値。 スレッド メソッドの結果を取得するには、2 つ目のコード例で示すようにコールバック メソッドを使用できます。  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>コールバック メソッドを使用してデータを取得します。  
 次の例では、スレッドのスレッドからデータを取得するコールバック メソッドを示します。 データおよびスレッド メソッドを含むクラスのコンス トラクターは、コールバック メソッドを表すデリゲートも受け取ります。スレッド メソッドが終了する前に、コールバック デリゲートを呼び出します。  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)
