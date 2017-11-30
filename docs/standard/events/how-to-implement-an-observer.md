---
title: "方法: オブザーバーを実装する"
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a>方法: オブザーバーを実装する
オブサーバー デザイン パターンでは、通知を登録すると、監視者、およびデータを監視し、1 つまたは複数のオブザーバーに通知を送信する、プロバイダーの分割が必要です。 このトピックでは、オブザーバーを作成する方法について説明します。 関連するトピック[する方法: プロバイダーを実装する](../../../docs/standard/events/how-to-implement-a-provider.md)プロバイダーを作成する方法について説明します。  
  
### <a name="to-create-an-observer"></a>オブザーバーを作成するには  
  
1.  実装する型であると、オブザーバーを定義、<xref:System.IObserver%601?displayProperty=nameWithType>インターフェイスです。 たとえば、次のコードがという名前の型を定義`TemperatureReporter`が構築された<xref:System.IObserver%601?displayProperty=nameWithType>のジェネリック型引数で実装`Temperature`です。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  オブザーバーがプロバイダーの呼び出し前に、の通知の受信を停止することができる場合、<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>実装を保持するプライベート変数を定義する、 <xref:System.IDisposable> 、プロバイダーによって返される実装<xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>メソッドです。 呼び出す、プロバイダーのサブスクリプション メソッドを定義することも必要があります。<xref:System.IObservable%601.Subscribe%2A>メソッドと、返されたストア<xref:System.IDisposable>オブジェクト。 たとえば、次のコードがという名前のプライベート変数を定義`unsubscriber`を定義し、`Subscribe`メソッドは、プロバイダーの呼び出しを<xref:System.IObservable%601.Subscribe%2A>メソッドに返されるオブジェクトを代入し、`unsubscriber`変数。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  プロバイダーの呼び出し前に、の通知の受信を停止するオブザーバーをできるようにするメソッドを定義するその<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>実装では、この機能が必要な場合です。 次の例では定義、`Unsubscribe`メソッドです。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  によって定義された 3 つのメソッドの実装を提供する、<xref:System.IObserver%601>インターフェイス: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、 <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>、および<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>です。 プロバイダーと、アプリケーションのニーズに応じて、<xref:System.IObserver%601.OnError%2A>と<xref:System.IObserver%601.OnCompleted%2A>メソッドがスタブ実装を指定できます。 注意してください、<xref:System.IObserver%601.OnError%2A>メソッドを渡された処理しないでください<xref:System.Exception>オブジェクト、例外として、<xref:System.IObserver%601.OnCompleted%2A>メソッドは、プロバイダーの呼び出しに無料<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>実装します。 次の例は、<xref:System.IObserver%601>の実装、`TemperatureReporter`クラスです。  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>例  
 次の例には完全なソース コードが含まれています、`TemperatureReporter`を提供するクラス、<xref:System.IObserver%601>温度監視アプリケーションの実装です。  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IObserver%601>  
 [オブサーバー デザイン パターン](../../../docs/standard/events/observer-design-pattern.md)  
 [方法: プロバイダーを実装する](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [オブザーバー デザイン パターンのベスト プラクティス](../../../docs/standard/events/observer-design-pattern-best-practices.md)
