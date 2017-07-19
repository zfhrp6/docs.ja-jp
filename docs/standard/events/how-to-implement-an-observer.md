---
title: "方法: オブザーバーを実装する | Microsoft Docs"
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
  - "オブサーバー [.NET Framework]、オブサーバー デザイン パターン"
  - "オブサーバー デザイン パターン [.NET Framework]、オブサーバーを実装する"
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法: オブザーバーを実装する
オブザーバー デザイン パターンでは、通知の登録を行うオブザーバーと、データの監視および 1 つ以上のオブザーバーへの通知の送信を行うプロバイダーとを区別する必要があります。  このトピックでは、オブザーバーを作成する方法について説明します。  関連トピックの「[方法: プロバイダーを実装する](../../../docs/standard/events/how-to-implement-a-provider.md)」では、プロバイダーを作成する方法について説明します。  
  
### オブザーバーを作成するには  
  
1.  <xref:System.IObserver%601?displayProperty=fullName> インターフェイスを実装する型であるオブザーバーを定義します。  たとえば、次のコードでは、ジェネリック型引数の `Temperature` を使用して構築された <xref:System.IObserver%601?displayProperty=fullName> の実装である `TemperatureReporter` という型を定義しています。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  プロバイダーによって <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName> の実装が呼び出される前にオブザーバーが通知の受信を中止できる場合は、プロバイダーの <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName> メソッドから返される <xref:System.IDisposable> の実装を保持するプライベート変数を定義します。  また、プロバイダーの <xref:System.IObservable%601.Subscribe%2A> メソッドを呼び出し、返される <xref:System.IDisposable> オブジェクトを格納するサブスクリプション メソッドを定義する必要があります。  たとえば、次のコードでは、`unsubscriber` というプライベート変数を定義し、プロバイダーの <xref:System.IObservable%601.Subscribe%2A> メソッドを呼び出して返されたオブジェクトを `unsubscriber` 変数に代入する `Subscribe` メソッドを定義しています。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  必要に応じて、プロバイダーによって <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName> の実装が呼び出される前にオブザーバーが通知の受信を中止できるようにするメソッドを定義します。  次の例では、`Unsubscribe` メソッドを定義しています。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <xref:System.IObserver%601> インターフェイスによって定義される 3 つのメソッド \(<xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>、<xref:System.IObserver%601.OnError%2A?displayProperty=fullName>、および <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>\) を実装します。  プロバイダーおよびアプリケーションの必要に応じて、<xref:System.IObserver%601.OnError%2A> メソッドと <xref:System.IObserver%601.OnCompleted%2A> メソッドは、スタブ実装にすることができます。  <xref:System.IObserver%601.OnError%2A> メソッドは渡された <xref:System.Exception> オブジェクトを例外として処理せず、<xref:System.IObserver%601.OnCompleted%2A> メソッドはプロバイダーの <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> の実装を自由に呼び出すことができる点に注意してください。  `TemperatureReporter` クラスの <xref:System.IObserver%601> の実装例を次に示します。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## 使用例  
 温度監視アプリケーションの <xref:System.IObserver%601> を実装する `TemperatureReporter` クラスの完全なソース コード例を次に示します。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## 参照  
 <xref:System.IObserver%601>   
 [オブサーバー デザイン パターン](../../../docs/standard/events/observer-design-pattern.md)   
 [方法: プロバイダーを実装する](../../../docs/standard/events/how-to-implement-a-provider.md)   
 [オブサーバー デザイン パターンのベスト プラクティス](../../../docs/standard/events/observer-design-pattern-best-practices.md)