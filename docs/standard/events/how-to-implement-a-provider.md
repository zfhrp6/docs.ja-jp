---
title: "方法: プロバイダーを実装する"
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
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9d8f96de8cb3d13568e755f1d5e885e0474d891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-provider"></a>方法: プロバイダーを実装する
オブサーバー デザイン パターンでは、データを監視し、通知を送信する、プロバイダー、およびプロバイダーから通知 (コールバック) を受け取る 1 つまたは複数のオブザーバーの分割が必要です。 このトピックでは、プロバイダーを作成する方法について説明します。 関連するトピック[する方法: オブザーバーを実装する](../../../docs/standard/events/how-to-implement-an-observer.md)オブザーバーを作成する方法について説明します。  
  
### <a name="to-create-a-provider"></a>プロバイダーを作成するには  
  
1.  プロバイダーはオブザーバーに送信するため、データを定義します。 プロバイダーとオブザーバーに送信されるデータを指定できますが、1 つの型は通常、さまざまな種類で表されます。 など、アプリケーションの監視温度、`Temperature`構造データの定義をプロバイダー (で表される、`TemperatureMonitor`次の手順で定義されたクラス) を監視し、どのオブザーバーをサブスクライブします。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  実装する型であるデータ プロバイダーを定義、<xref:System.IObservable%601?displayProperty=nameWithType>インターフェイスです。 プロバイダーのジェネリック型引数は、プロバイダーがオブザーバーに送信する型です。 次の例では定義、`TemperatureMonitor`は構築されたクラス<xref:System.IObservable%601?displayProperty=nameWithType>のジェネリック型引数で実装`Temperature`です。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  プロバイダーは格納方法オブザーバーへの参照できるように、適切な場合に、各オブザーバーを通知することができますを決定します。 ジェネリック型などのコレクション オブジェクトではほとんどの場合、<xref:System.Collections.Generic.List%601>オブジェクトはこの目的に使用します。 次の例では、プライベート<xref:System.Collections.Generic.List%601>でインスタンス化されるオブジェクト、`TemperatureMonitor`クラスのコンス トラクターです。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  定義、<xref:System.IDisposable>実装できるように、いつでも通知の受信が停止することをサブスクライバーにプロバイダーを返すことができます。 次の例は、入れ子になった定義`Unsubscriber`クラスとサブスクライバーのするサブスクライバーのコレクションの参照を渡し、クラスがインスタンス化されるときです。 このコードを有効にするオブジェクトのサブスクライバー<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>自体をサブスクライバーのコレクションから削除する実装。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> メソッドを実装します。 メソッドがへの参照を渡し、<xref:System.IObserver%601?displayProperty=nameWithType>インターフェイスし、手順 3. では、その目的で設計されたオブジェクトに格納する必要があります。 メソッドが返す必要がありますし、<xref:System.IDisposable>手順 4. で開発された実装。 次の例の実装を示しています、<xref:System.IObservable%601.Subscribe%2A>メソッドで、`TemperatureMonitor`クラスです。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  呼び出すことによって適切なオブザーバーに通知が<xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、 <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>、および<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>実装します。 場合によっては、プロバイダーを呼び出すことがない、<xref:System.IObserver%601.OnError%2A>メソッドはエラーが発生したとします。 たとえば、次`GetTemperature`メソッドは、モニターを 5 秒ごとに気温データを読み取り、前の読み取り以降には、少なくとも 1 度によって、温度、変更された場合、オブザーバーに通知をシミュレートします。 場合、デバイスが温度を報告していない (つまり、その値が null 場合)、プロバイダーは、転送が完了したことをオブザーバーに通知します。 なお、各オブザーバーを呼び出すだけでなく<xref:System.IObserver%601.OnCompleted%2A>、メソッド、`GetTemperature`メソッドをクリア、<xref:System.Collections.Generic.List%601>コレクション。 この場合、プロバイダーを行いませんへの呼び出し、<xref:System.IObserver%601.OnError%2A>そのオブザーバーのメソッドです。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>例  
 次の例には、定義するための完全なソース コードが含まれています、<xref:System.IObservable%601>温度監視アプリケーションの実装です。 含まれている、`Temperature`オブザーバーに送信するデータには、構造および`TemperatureMonitor`はクラス、<xref:System.IObservable%601>実装します。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IObservable%601>  
 [オブサーバー デザイン パターン](../../../docs/standard/events/observer-design-pattern.md)  
 [方法: オブザーバーを実装する](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [オブザーバー デザイン パターンのベスト プラクティス](../../../docs/standard/events/observer-design-pattern-best-practices.md)
