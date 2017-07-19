---
title: "方法: プロバイダーを実装する | Microsoft Docs"
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
  - "オブサーバー デザイン パターン [.NET Framework]、プロバイダーを実装する"
  - "プロバイダー [.NET Framework]、オブサーバー デザイン パターンでの"
  - "オブサーバー [.NET Framework]、オブサーバー デザイン パターンでの"
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法: プロバイダーを実装する
オブザーバー デザイン パターンでは、データを監視して通知を送信するプロバイダーと、プロバイダーからの通知 \(コールバック\) を受信する 1 つ以上のオブザーバーとを区別する必要があります。  このトピックでは、プロバイダーを作成する方法について説明します。  関連トピックの「[方法: オブザーバーを実装する](../../../docs/standard/events/how-to-implement-an-observer.md)」では、オブザーバーを作成する方法について説明します。  
  
### プロバイダーを作成するには  
  
1.  プロバイダーがオブザーバーに送信するデータを定義します。  プロバイダーとそれがオブザーバーに送信するデータは 1 つの型にすることもできますが、通常は別々の型で表されます。  たとえば、温度監視アプリケーションの場合、`Temperature` 構造で、プロバイダー \(次の手順で定義する `TemperatureMonitor` クラスで表されるプロバイダー\) が監視するデータと、サブスクライブするオブザーバーを定義します。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  <xref:System.IObservable%601?displayProperty=fullName> インターフェイスを実装する型であるデータ プロバイダーを定義します。  プロバイダーのジェネリック型引数は、プロバイダーがオブザーバーに送信する型です。  次の例では、ジェネリック型引数の `Temperature` を使用して構築された <xref:System.IObservable%601?displayProperty=fullName> の実装である `TemperatureMonitor` クラスを定義しています。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  各オブザーバーに適切に通知できるように、プロバイダーでオブザーバーへの参照を保存する方法を決めます。  一般に、この目的には、汎用 <xref:System.Collections.Generic.List%601> オブジェクトなどのコレクション オブジェクトが使用されます。  次の例では、`TemperatureMonitor` クラス コンストラクターでインスタンス化されるプライベート <xref:System.Collections.Generic.List%601> オブジェクトを定義しています。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  サブスクライバーが通知の受信をいつでも中止できるように、プロバイダーがサブスクライバーに返すことができる <xref:System.IDisposable> 実装を定義します。  次の例では、入れ子になった `Unsubscriber` クラスを定義しています。このクラスがインスタンス化されるときに、サブスクライバーのコレクションへの参照とサブスクライバーへの参照が渡されます。  このコードによって、サブスクライバーがオブジェクトの <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 実装を呼び出して、サブスクライバーのコレクションから自身を削除できるようになります。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName> メソッドを実装します。  これは <xref:System.IObserver%601?displayProperty=fullName> インターフェイスへの参照が渡されるメソッドであり、手順 3. で設計したオブジェクトに保存する必要があります。  このメソッドはその後、手順 4. で開発した <xref:System.IDisposable> 実装を返す必要があります。  `TemperatureMonitor` クラスの <xref:System.IObservable%601.Subscribe%2A> メソッドの実装の例を次に示します。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  オブザーバーの <xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>、<xref:System.IObserver%601.OnError%2A?displayProperty=fullName>、および <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName> の各実装を呼び出して、オブザーバーに適切に通知します。  場合によっては、エラーが発生したときに、プロバイダーが <xref:System.IObserver%601.OnError%2A> メソッドを呼び出さないことがあります。  たとえば、次の `GetTemperature` メソッドは、5 秒ごとに温度データを読み取るモニターをシミュレートし、前回の読み取りから温度が 0.1 度以上変化した場合にオブザーバーに通知します。  デバイスが温度を報告しない場合 \(つまり値が null の場合\) は、プロバイダーはオブザーバーに伝送が完了したことを通知します。  `GetTemperature` メソッドは、各オブザーバーの <xref:System.IObserver%601.OnCompleted%2A> メソッドを呼び出すだけでなく、<xref:System.Collections.Generic.List%601> のコレクションをクリアすることに注意してください。  この場合、プロバイダーは、オブザーバーの <xref:System.IObserver%601.OnError%2A> メソッドを呼び出しません。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## 使用例  
 温度監視アプリケーションの <xref:System.IObservable%601> の実装を定義するための完全なソース コードの例を次に示します。  オブザーバーに送信されるデータである `Temperature` 構造と、<xref:System.IObservable%601> の実装である `TemperatureMonitor` クラスが含まれます。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## 参照  
 <xref:System.IObservable%601>   
 [オブサーバー デザイン パターン](../../../docs/standard/events/observer-design-pattern.md)   
 [方法: オブザーバーを実装する](../../../docs/standard/events/how-to-implement-an-observer.md)   
 [オブサーバー デザイン パターンのベスト プラクティス](../../../docs/standard/events/observer-design-pattern-best-practices.md)