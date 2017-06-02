---
title: "Creating Threads and Passing Data at Start Time | Microsoft Docs"
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
  - "threading [.NET Framework], creating"
  - "threading [.NET Framework], passing data to threads"
  - "threading [.NET Framework], retrieving data from threads"
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Creating Threads and Passing Data at Start Time
オペレーティング システム プロセスが作成されると、オペレーティング システムは、元のアプリケーション ドメインを含め、そのプロセスにコードを実行するためのスレッドを挿入します。  その時点からは、アプリケーション ドメインを作成したり、破棄したりする場合に、必ずしもオペレーティング システム スレッドを作成したり、破棄したりする必要はありません。  実行されているコードがマネージ コードの場合は、<xref:System.Threading.Thread> 型の静的な <xref:System.Threading.Thread.CurrentThread%2A> プロパティを取得すると、現在のアプリケーション ドメインで実行しているスレッドの <xref:System.Threading.Thread> オブジェクトを取得できます。  このトピックでは、スレッドの作成について説明し、データをスレッド プロシージャに渡す代替手段について説明します。  
  
## スレッドの作成  
 <xref:System.Threading.Thread> オブジェクトを作成すると、新しいマネージ スレッドが作成されます。  <xref:System.Threading.Thread> クラスには <xref:System.Threading.ThreadStart> デリゲートまたは <xref:System.Threading.ParameterizedThreadStart> デリゲートを受け取るコンストラクターがあり、このデリゲートは <xref:System.Threading.Thread.Start%2A> メソッドを呼び出す際に新しいスレッドが呼び出すメソッドをラップします。  <xref:System.Threading.Thread.Start%2A> を複数回呼び出すと、<xref:System.Threading.ThreadStateException> がスローされます。  
  
 <xref:System.Threading.Thread.Start%2A> メソッドは即座に制御を返すため、新しいスレッドが開始される前に制御が戻ることも少なくありません。  <xref:System.Threading.Thread.ThreadState%2A> プロパティと <xref:System.Threading.Thread.IsAlive%2A> プロパティを使用すると、任意の時点のスレッドの状態を特定できますが、この 2 つのプロパティは、スレッドの活動を同期するために使用すべきではありません。  
  
> [!NOTE]
>  スレッドが開始した後は、<xref:System.Threading.Thread> オブジェクトへの参照を保持する必要はありません。  スレッドの実行は、スレッド プロシージャが終了するまで継続します。  
  
 別のオブジェクトでインスタンス メソッドと静的メソッドを呼び出すために 2 つの新しいスレッドを作成するコード例を次に示します。  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## スレッドにデータを渡し、スレッドからデータを取得する  
 .NET Framework Version 2.0 では、<xref:System.Threading.Thread.Start%2A?displayProperty=fullName> メソッド オーバーロードを呼び出す際に <xref:System.Threading.ParameterizedThreadStart> デリゲートによってデータを含むオブジェクトをスレッドに簡単に渡すことができます。  コード例については、<xref:System.Threading.ParameterizedThreadStart> を参照してください。  
  
 <xref:System.Threading.ParameterizedThreadStart> デリゲートの使用は、<xref:System.Threading.Thread.Start%2A?displayProperty=fullName> メソッドのオーバーロードが任意のオブジェクトを受け入れるため、タイプ セーフなデータ伝達方法ではありません。  代わりに、スレッド プロシージャとデータをヘルパー クラスにカプセル化し、<xref:System.Threading.ThreadStart> デリゲートを使用してスレッド プロシージャを実行します。  この方法を次の 2 つのコード例に示します。  
  
 非同期呼び出しからデータを返す場所はないため、どちらのデリゲートにも戻り値はありません。  スレッド メソッドの結果を取得するには、コールバック メソッドを使用できます。以下の 2 番目のコードで、その例を示します。  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### コールバック メソッドによるデータの取得  
 スレッドからデータを取得するコールバック メソッドの例を次に示します。  データとスレッド メソッドを含むクラスのコンストラクターは、コールバック メソッドを表すデリゲートも受け取ります。スレッド メソッドの最後で、コールバック デリゲートを呼び出します。  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## 参照  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadStart>   
 <xref:System.Threading.ParameterizedThreadStart>   
 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)