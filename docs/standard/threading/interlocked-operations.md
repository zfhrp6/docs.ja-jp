---
title: "Interlocked Operations | Microsoft Docs"
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
  - "Interlocked class, about Interlocked class"
  - "threading [.NET Framework], Interlocked class"
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Interlocked Operations
<xref:System.Threading.Interlocked> クラスは、複数のスレッドが共有する変数へのアクセスを同期化するメソッドを提供します。  この変数が共有メモリにある場合、各プロセスのスレッドがこの機構を使用できます。  インタロックされた操作はアトミックです。つまり、操作全体が 1 つの単位のため、同じ変数の別のインタロックされた操作によって中断されることはありません。  これは、メモリ アドレスから値を読み込んだ後、変更して格納できるようになる前にスレッドを中断できるプリエンプティブ マルチスレッドのオペレーティング システムで重要です。  
  
 <xref:System.Threading.Interlocked> クラスには、次の操作があります。  
  
-   .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Add%2A> メソッドは変数に整数値を追加して変数の新しい値を返します。  
  
-   .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Read%2A> メソッドはアトミック操作として 64 ビットの整数値を読み込みます。  これは、64 ビットの整数の読み込みが、通常、アトミック操作ではない 32 ビットのオペレーティング システムで有効です。  
  
-   <xref:System.Threading.Interlocked.Increment%2A> メソッドと <xref:System.Threading.Interlocked.Decrement%2A> メソッドは、変数をインクリメントまたはデクリメントした値を返します。  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> メソッドは、指定された変数で値をアトミックに交換して値を返し、新しい値で置き換えます。  .NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。  「<xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>」を参照してください。  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドも 2 つの値を交換しますが、比較の結果しだいです。  .NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。  「<xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>」を参照してください。  
  
 今日のプロセッサでは、多くの場合、<xref:System.Threading.Interlocked> クラスのメソッドは単一の命令で実装できます。  このように、高性能の同期機能を提供するこれらのメソッドによって、スピン ロックなどのより高水準の同期機構を構築できます。  
  
 <xref:System.Threading.Monitor> クラスと <xref:System.Threading.Interlocked> クラスを組み合わせて使用する例については、「[監視](../Topic/Monitors.md)」を参照してください。  
  
## CompareExchange の例  
 <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドは、単純なインクリメントまたはデクリメントよりも複雑な計算を保護するために使用できます。  浮動小数点値として格納されている現在の合計に対して加算を行うスレッド セーフ メソッドの例を次に示します。整数に対しては、<xref:System.Threading.Interlocked.Add%2A> メソッドを使用する方法が簡単です。完全なコード例については、単精度と倍精度の浮動小数点引数 \(<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> と <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>\) を受け取る <xref:System.Threading.Interlocked.CompareExchange%2A> のオーバーロードを参照してください。  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## Exchange と CompareExchange の型指定されていないオーバーロード  
 <xref:System.Threading.Interlocked.Exchange%2A> メソッドと <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドには、<xref:System.Object> 型の引数を受け取るオーバーロードがあります。  各オーバーロードの第 1 引数は `ref Object` \(Visual Basic では `ByRef … As Object`\) で、この引数に渡す変数の型は <xref:System.Object> 型である必要があります。このメソッドを呼び出すときに、第 1 引数を <xref:System.Object> 型にキャストするだけでは不十分です。  
  
> [!NOTE]
>  .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Exchange%2A> メソッドと <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドのジェネリック オーバーロードを使用して厳密に型指定された変数を交換します。  
  
 一度だけ設定できる `ClassA` 型のプロパティのコード例を次に示します。このプロパティは、.NET Framework Version 1.0 または 1.1 で実装できます。  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## 参照  
 <xref:System.Threading.Interlocked>   
 <xref:System.Threading.Monitor>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)