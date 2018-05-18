---
title: スレッドを作成し、開始時にデータを渡す
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96c0c898f103c058c370a0d108568056b1ff8196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>スレッドを作成し、開始時にデータを渡す
オペレーティング システム プロセスが作成されると、オペレーティング システムは、元のアプリケーション ドメインを含め、そのプロセスでコードを実行するスレッドを挿入します。 その時点から、オペレーティング システム スレッドを作成または破棄せずに、アプリケーション ドメインを作成したり破棄したりすることができます。 実行対象コードがマネージ コードである場合は、<xref:System.Threading.Thread> 型の静的 <xref:System.Threading.Thread.CurrentThread%2A> プロパティを取得することで、現在のアプリケーション ドメインで実行されるスレッドの <xref:System.Threading.Thread> オブジェクトを取得できます。 このトピックではスレッドの作成について説明し、データをスレッド プロシージャに渡すための代替手段について説明します。  
  
## <a name="creating-a-thread"></a>スレッドの作成  
 新しい <xref:System.Threading.Thread> オブジェクトを作成すると、新しいマネージ スレッドが作成されます。 <xref:System.Threading.Thread> クラスには <xref:System.Threading.ThreadStart> デリゲートまたは <xref:System.Threading.ParameterizedThreadStart> デリゲートを受け取るコンストラクターがあります。デリゲートは、<xref:System.Threading.Thread.Start%2A> メソッドの呼び出し時に新しいスレッドで呼び出されるメソッドをラップします。 複数回 <xref:System.Threading.Thread.Start%2A> を呼び出すと、<xref:System.Threading.ThreadStateException> がスローされます。  
  
 <xref:System.Threading.Thread.Start%2A> メソッドはすぐに (多くの場合、新しいスレッドが実際に開始される前) 制御を返します。 <xref:System.Threading.Thread.ThreadState%2A> および <xref:System.Threading.Thread.IsAlive%2A> プロパティを使用して、任意の時点のスレッドの状態を判別できますが、スレッドのアクティビティを同期する場合にこれらのプロパティを使用しないでください。  
  
> [!NOTE]
>  スレッドが開始された後に、<xref:System.Threading.Thread> オブジェクトへの参照を保持する必要はありません。 スレッドは、スレッド プロシージャが終了するまで、引き続き実行されます。  
  
 次のコード例では、2 つの新しいスレッドを作成し、別のオブジェクトでインスタンスおよび静的メソッドを呼び出します。  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>スレッドへのデータの受け渡しとスレッドからのデータの取得  
 .NET framework Version 2.0 では、<xref:System.Threading.ParameterizedThreadStart> デリゲートは、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッド オーバーロードの呼び出し時にスレッドにデータを含むオブジェクトを渡すための簡単な方法を提供します。 コード例については、「<xref:System.Threading.ParameterizedThreadStart>」を参照してください。  
  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッド オーバーロードではすべてのオブジェクトを受け入れるため、<xref:System.Threading.ParameterizedThreadStart> デリゲートの使用はデータを渡すためのタイプ セーフな方法ではありません。 代わりに、ヘルパー クラスにデータとスレッド プロシージャをカプセル化し、<xref:System.Threading.ThreadStart> デリゲートを使用して、スレッド プロシージャを実行することができます。 この手法は、以下の 2 つのコード例で示されています。  
  
 非同期呼び出しからデータを返す場所がないため、いずれのデリゲートにも戻り値がありません。 スレッド メソッドの結果を取得するために、コールバック メソッドを使用することができます。これについては、2 つ目のコード例に示されています。  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>コールバック メソッドによるデータの取得  
 次の例では、スレッドからデータを取得するコールバック メソッドを示します。 データとスレッド メソッドを含むクラスのコンストラクターは、コールバック メソッドを表すデリゲートも受け入れます。スレッド メソッドが終了する前に、コールバック デリゲートが呼び出されます。  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)
