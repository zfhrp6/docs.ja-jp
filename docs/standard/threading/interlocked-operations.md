---
title: インタロックされた操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38532228f7a5d07bb1b9fcf7e90d2be53a28b04c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="interlocked-operations"></a>インタロックされた操作
<xref:System.Threading.Interlocked> クラスでは、複数のスレッドによって共有されている変数へのアクセスを同期するメソッドが提供されます。 この変数が共有メモリにある場合、さまざまなプロセスのスレッドがこのメカニズムを使用できます。 インタロックされた操作はアトミックです。つまり、その操作全体が 1 つの単位のため、同じ変数の別のインタロックされた操作によって中断されることはありません。 これは、メモリ アドレスから値を読み込んだ後、変更して格納できるようになる前にスレッドを中断できるプリエンプティブ マルチスレッドのオペレーティング システムで重要です。  
  
 <xref:System.Threading.Interlocked> クラスでは次の操作が提供されます。  
  
-   .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Add%2A> メソッドは変数に整数値を追加して、変数の新しい値を返します。  
  
-   .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Read%2A> メソッドはアトミック操作として 64 ビットの整数値を読み取ります。 これは、64 ビット整数の読み取りが通常はアトミック操作ではない 32 ビット オペレーティング システムでは有用です。  
  
-   <xref:System.Threading.Interlocked.Increment%2A> および <xref:System.Threading.Interlocked.Decrement%2A> メソッドは変数をインクリメントまたはデクリメントして、結果の値を返します。  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> メソッドは、指定された変数で値をアトミックに変換して値を返し、それを新しい値で置き換えます。 .NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。 「<xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>」を参照してください。  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドでも 2 つの値を変換しますが、比較結果によって異なります。 .NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。 「<xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>」を参照してください。  
  
 最新のプロセッサでは、<xref:System.Threading.Interlocked> クラスのメソッドを単一の命令で実装できる場合もよくあります。 このため、非常にパフォーマンスの高い同期を行うことができ、それらを使用して、スピン ロックのようなより高レベルの同期メカニズムを作成することもできます。  
  
 <xref:System.Threading.Monitor> クラスと <xref:System.Threading.Interlocked> クラスを組み合わせて使用する例については、「[Monitor クラス](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)」を参照してください。  
  
## <a name="compareexchange-example"></a>CompareExchange の例  
 <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドを使用して、単純なインクリメントまたはデクリメントよりも複雑な計算を保護できます。 次の例は、浮動小数点数として格納されている現在の合計に対して加算を行うスレッドセーフ メソッドを示しています  (整数の場合は、<xref:System.Threading.Interlocked.Add%2A> メソッドがより単純なソリューションとなります)。完全なコード例については、単精度と倍精度浮動小数点引数 (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> と <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>) を受け取る <xref:System.Threading.Interlocked.CompareExchange%2A> のオーバーロードを参照してください。  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Exchange および CompareExchange の型指定されていないオーバーロード  
 <xref:System.Threading.Interlocked.Exchange%2A> および <xref:System.Threading.Interlocked.CompareExchange%2A>メソッドには、<xref:System.Object> 型の引数を受け取るオーバーロードがあります。 各オーバーロードの最初の引数は `ref Object` (Visual Basic では `ByRef … As Object`) であり、タイプ セーフを確保するために、この引数に渡される変数は <xref:System.Object> のように厳密に型指定される必要があります。これらのメソッドを呼び出すときに、単に最初の引数を型 <xref:System.Object> にキャストするだけでは不十分です。  
  
> [!NOTE]
>  .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Exchange%2A> および <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドのジェネリック オーバーロードを使用して、厳密に型指定された変数を変換します。  
  
 一度だけ設定できる `ClassA` 型のプロパティのコード例を次に示します。このプロパティは、.NET Framework Version 1.0 または 1.1 で実装できます。  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
