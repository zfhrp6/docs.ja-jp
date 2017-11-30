---
title: "インタロックされた操作"
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
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a>インタロックされた操作
<xref:System.Threading.Interlocked>クラスは、複数のスレッドによって共有される変数へのアクセスを同期するメソッドを提供します。 この変数が共有メモリにある場合、さまざまなプロセスのスレッドがこのメカニズムを使用できます。 インタロックされた操作はアトミックです。つまり、その操作全体が 1 つの単位のため、同じ変数の別のインタロックされた操作によって中断されることはありません。 これは、メモリ アドレスから値を読み込んだ後、変更して格納できるようになる前にスレッドを中断できるプリエンプティブ マルチスレッドのオペレーティング システムで重要です。  
  
 <xref:System.Threading.Interlocked>クラスには、次の操作が用意されています。  
  
-   .NET framework version 2.0 では、<xref:System.Threading.Interlocked.Add%2A>メソッドが変数に整数値を追加し、変数の新しい値を返します。  
  
-   .NET framework version 2.0 では、<xref:System.Threading.Interlocked.Read%2A>メソッドは、アトミックな操作として 64 ビット整数値を読み取ります。 これは、64 ビット整数の読み取りが通常はアトミック操作ではない 32 ビット オペレーティング システムでは有用です。  
  
-   <xref:System.Threading.Interlocked.Increment%2A>と<xref:System.Threading.Interlocked.Decrement%2A>メソッドはインクリメントまたは変数をデクリメントを結果の値を返します。  
  
-   <xref:System.Threading.Interlocked.Exchange%2A>メソッドは、指定した変数、その値を返すと、新しい値で置き換えることで、アトミック値の交換を実行します。 .NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。 「<xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>」を参照してください。  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A>メソッドとも交換 2 つの値が比較の結果 contingent です。 .NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。 「<xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>」を参照してください。  
  
 最新のプロセッサのメソッドで、<xref:System.Threading.Interlocked>多くの場合、1 つの命令でクラスを実装できます。 このため、非常にパフォーマンスの高い同期を行うことができ、それらを使用して、スピン ロックのようなより高レベルの同期メカニズムを作成することもできます。  
  
 使用する例については、<xref:System.Threading.Monitor>と<xref:System.Threading.Interlocked>組み合わせで、クラスを参照してください[モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)です。  
  
## <a name="compareexchange-example"></a>CompareExchange の例  
 <xref:System.Threading.Interlocked.CompareExchange%2A>は単純なインクリメントおよびデクリメントより複雑な計算を保護するメソッドを使用できます。 次の例は、浮動小数点数として格納されている現在の合計に対して加算を行うスレッドセーフ メソッドを示しています  (整数、用、<xref:System.Threading.Interlocked.Add%2A>メソッドは、簡単なソリューションです)。完全なコード例については、のオーバー ロードを参照してください。<xref:System.Threading.Interlocked.CompareExchange%2A>単精度と倍精度浮動小数点引数を受け取る (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29>と<xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>)。  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Exchange および CompareExchange の型指定されていないオーバーロード  
 <xref:System.Threading.Interlocked.Exchange%2A>と<xref:System.Threading.Interlocked.CompareExchange%2A>メソッド型の引数を受け取るオーバー ロードがあります<xref:System.Object>です。 これらのオーバー ロードのそれぞれの最初の引数は`ref Object`(`ByRef … As Object` Visual Basic で)、タイプ セーフ必要として厳密に型指定するのには、この引数に渡された変数および<xref:System.Object>; 入力に最初の引数をキャストできません単に<xref:System.Object>。これらのメソッドを呼び出すときにします。  
  
> [!NOTE]
>  .NET Framework version 2.0 でのジェネリック オーバー ロードを使用して、<xref:System.Threading.Interlocked.Exchange%2A>と<xref:System.Threading.Interlocked.CompareExchange%2A>強くを交換するメソッドの型指定される変数です。  
  
 一度だけ設定できる `ClassA` 型のプロパティのコード例を次に示します。このプロパティは、.NET Framework Version 1.0 または 1.1 で実装できます。  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
